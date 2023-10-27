# Assignment Submission

## Project Selected: Project 3: Flask

## I. Introduction
- Briefly introduce the purpose of this section, which is to provide a detailed description of two test cases in the selected open-source project.

## II. Test Case 1: [test_json_bad_requests(app, client)]
### A. Description
- The purpose of this test is to confirm that if the user sends bad json data, the server will return a 400 error.
### B. Gherkin Syntax (if applicable)
- If you choose to use Gherkin syntax, write the Gherkin scenario for this test case.
### C. Test Steps
- 1. define a Flask route that accepts a POST request with JSON data
- 2. simulate a POST request with bad JSON data
- 3. confirm that the server returns a 400 error
### D. Code Segments Under Test
- @app.route("/json", methods=["POST"])
  - this is the route that is being tested
-  rv = client.post("/json", data="malformed", content_type="application/json")
  - this is the POST request that is being tested
- assert rv.status_code == 400
    - this is the assertion that the server returns a 400 error

```Java
//def test_json_bad_requests(app, client):
//@app.route("/json", methods=["POST"])
//    def return_json():
//            return flask.jsonify(foo=str(flask.request.get_json()))
//
//            rv = client.post("/json", data="malformed", content_type="application/json")
//            assert rv.status_code == 400
```
### E. Initial State
- initially, the json endpoint doesn't exist, the client has not made any prior HTTP requests, the malformed json data doesn't exist yet.
### F. Transition
- a route is defined that accepts a POST request with JSON data, the client makes a POST request with bad JSON data
### G. Expected State
- the server returns a 400 error

## III. Test Case 2: [test_method_route(app, client, method)]
### A. Description
- The purpose of this test case is to test various http requests
### B. Gherkin Syntax (if applicable)
- If you choose to use Gherkin syntax, write the Gherkin scenario for this test case.
### C. Test Steps
- 1. a route handler is defined with the common path "/" for GET, POST, PUT, DELETE, and PATCH requests
- 2. a route handler function is defined for each of the above requests
- 3. a client makes a request to the "/" endpoint associated with each of the above requests
- 4. the test checks if the request matches the expected value
### D. Code Segments Under Test
- method_route = getattr(app, method)
  - This function selects an attribute from the app object based on the method parameter
- client_method = getattr(client, method)
  - This function selects an attribute from the client object based on the method parameter
  - This function is used to make a request to the "/" endpoint
- @method_route("/")
        def hello():
                return "Hello"
  - This function defines a route handler for the "/" endpoint that returns "Hello" upon a successful request

```Java
//@pytest.mark.parametrize("method", ["get", "post", "put", "delete", "patch"])
//def test_method_route(app, client, method):
//        method_route = getattr(app, method)
//        client_method = getattr(client, method)
//
//@method_route("/")
//    def hello():
//            return "Hello"
//
//            assert client_method("/").data == b"Hello"@pytest.mark.parametrize("method", ["get", "post", "put", "delete", "patch"])
```
### E. Initial State
- initially, the "/" endpoint doesn't exist, the client has not made any prior HTTP requests
### F. Transition
- a route handler is defined with the common path "/" for GET, POST, PUT, DELETE, and PATCH requests, a route handler function is defined for each of the above requests, a client makes a request to the "/" endpoint associated with each of the above requests
### G. Expected State
- the test checks if the request matches the expected value

