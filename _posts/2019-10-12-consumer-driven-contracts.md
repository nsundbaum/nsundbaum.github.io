---
layout: post
title:  "Consumer driven contracts"
date:   2019-10-12 18:17:04 +0100
---

Recently, I decided to dig a little deeper into consumer driven contracts and more specifically the [Pact framework](https://docs.pact.io "The Pact framework"). In essence, consumer driven contracts are about having consumers of a service define their expectations (i.e. contract) on that service in terms of tests that can be executed on both the consumer and the service provider side. Such tests can then be run as part of the CI build of the service provider as well as the consumer. If done right, the provider service can evolve independently as long as it doesn’t break any of those tests and you therefore limit the need for extensive end-to-end testing as a means to catch breaking changes. Which is good since such tests can be both time-consuming and fragile. In this age of APIs and (micro)service oriented architectures, I think this is a very interesting approach to QA and test automation. And arguably also a fairly underutilized one.    

So, let's get started with an example. In this scenario, we are integrating with a service that can provide a list of users. In the client code, we call this service like this:

```python
class UserApi():
  def __init__(self, host='http://127.0.0.1', port=5001):
    self.base_url = f'{host}:{port}'  

  def all_users(self):
    response = requests.get(f'{self.base_url}/users')
    return self._handle_response(response)

  def _handle_response(self, response):
    response.raise_for_status()
    return response.json()

  ...
```

A consumer driven contract test implemented in Pact could then look like this:

```python
expected_user = {
    'name': Like('John Doe'),
    'id': Like('abc123'),
    'active': Like(True)
}

def test_get_users(self):
  expected = EachLike(self.expected_user)

  pact
    .upon_receiving('a request for users')
    .with_request('get', '/users')
    .will_respond_with(200, body=expected)

  with pact:
      result = user_api.all_users()

  self.assertEqual(result, get_generated_values(expected))
```

When we run this on the client side, Pact will start a mock http server that responds to a `GET /users` request with a 200 status and a list of users.

Once this passes on the client side, we can generate something called a “Pact file”, which is a a JSON representation of the test above. We then share this file with the service provider, either manually, using a shared file server (or an S3 bucket or similar) or by publishing it to a “Pact broker”, which is basically a repository of Pact files that both the client and the service provider have access to. The process of generating Pact files and publishing them is typically done as part of the client’s CI flow.

On the service provider side, the interactions defined in the Pact file is then executed against the service and verified according to the rules defined in the test. This is done by the Pact framework and only requires a running provider service. Note that since the Pact file is defined in JSON format, the client and service provider can be implemented in different languages. Pact currently support Python, PHP, .Net, Ruby, Java (actually all JVM compatible languages), JavaScript, Swift and Go.

Since the client (where the test is created) can’t control exactly what data that will be returned (would make it a very brittle test and make it challenging to include dynamic data like timestamps or ids), “minimal verification” is used in this phase. This is why we used the `Like(...)` construct when declaring the `expected_user` variable above and it basically means that Pact should only verify the data types and not the actual contents. This can also be done using regular expressions.

As a next test, we can make sure that the service responds with a 404 if we ask for a user that does not exist:

```python
def test_get_unknown_user(self):
    pact
      .upon_receiving('a request for a non-existing user')
      .with_request('get', '/users/non-existing-id')
      .will_respond_with(404)

    with pact:
        self.assertRaises(HTTPError, user_api.user_by_id, 'non-existing-id')
```

Of course, this assumes that there is not actually a user with the id `non-existing-id` in the provider service.

So far, so good. As long as tests are as simple as one single interaction, things are very straightforward. However, if a test depends on something being setup in a certain way in the provider service, things become a little bit more complicated. As an example, let’s say that we want to test to get a user by id. To do that, we may first need to create a new user on the service provider side and get the id from there. Pact’s solution to this is something called “provider states”.

Provider states in Pact are setup as a special endpoint in the provider service (although it doesn’t strictly have to be the same service, it could also be a “test” service running side-by-side with the real provider service). This endpoint contains the setup code for different scenarios. The client can then trigger these setup endpoints by using an agreed naming scheme. This is a little bit cumbersome and introduces some tighter coupling between the client and the provider, but I guess it is a challenging problem to begin with. It is not recommended to use the public provider API to setup data (e.g. calling `POST /users` before `GET users/xyz`), so I get the impression that this is a conscious design decision from the Pact developers to make sure that tests don’t become too brittle.

Some things to keep in mind:

* These tests should not verify functionality, only focus on testing the format of the requests and responses between a client and a provider.
* The client should only verify the things (e.g. data fields, response codes etc.) that it actually needs, to give the provider as much freedom as possible to evolve.
* This type of testing is not really suited for public APIs or in other cases where the client team and the provider team don’t communicate on a regular basis.

To summarize, even though I only scratched the surface this time, I think it was a pretty good experience and in my opinion consumer driven contracts should definitely be something to assess as part of your QA automation toolbox when working with micro-service oriented architectures.
