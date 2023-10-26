# Assignment Submission

## Project Selected: <Enter project name>

## I. Introduction

- Briefly introduce the purpose of this section, which is to provide a detailed description of two test cases in the
  selected open-source project.

## II. Test Case 1: [test_options_work(app, client)]

### A. Description

- This test is used to check that the basic functionality of the index endpoint, "/", with options is correct. The
  endpoint accepts both GET and POST requests.

### B. Gherkin Syntax (if applicable)

- Not Used

### C. Test Steps

1. The test case makes a call to the "/" endpoint using the parameter "OPTIONS" saving the response as 'rv'
2. The test case then asserts that the endpoint only allows ["GET", "HEAD", "OPTIONS", "POST"]
3. The case then asserts that the data in the response is an empty string. This is because the endpoint is not set up to
   return anything when it is called with "OPTIONS".

### D. Code Segments Under Test

- This test case interacts with the portion of the system that initializes a Flask App as well as the
  app.test_client.open(), app.test_client.data() and app.test_client.allow() functions.

```Python
def test_options_work(app, client):
@app.route("/", methods=["GET", "POST"])
    def index():
            return "Hello World"

            rv = client.open("/", method="OPTIONS")
        assert sorted(rv.allow) == ["GET", "HEAD", "OPTIONS", "POST"]
        assert rv.data == b""
```

### E. Initial State

- The initial state of the system is that the test suite has spun up an instance of a Flask app. The flask app is
  waiting for requests.

### F. Transition

- The State transition is from the initial waiting state to a return state where the app gets a request form the test
  and returns a response to the test.

### G. Expected State

- The expected state is that the app has returned a response, stored as 'rv'. The response stores what methods are
  allowed and those methods match ["GET", "HEAD", "OPTIONS", "POST"]. Finally, that the response data is an empty
  string.

## III. Test Case 2: [test_basic_url_generation(app)]

### A. Description

- This test case is used to test that the URL requirements of the system are met. It uses variables in the app.config to
  define the "SERVER_NAME"and "PREFERRED_URL_SCHEME". Then it calls the root endpoint and asserts that the resulting URL
  is the expected result.

### B. Gherkin Syntax (if applicable)

- Not Used

### C. Test Steps

1. The first step is to initialize the flask app with the "SERVER_NAME"and "PREFERRED_URL_SCHEME" set with the desired
   outcome.
2. Then the call route needs to be setup. Int this case it is "/".
3. then the test case sets up the app context.
4. the next step isto make the call to  "/" and store the response in the variable rv.
5. Last the test case asserts that the received result matches the expected result.

### D. Code Segments Under Test

- The case interacts with the portion of the code that initializes a Flask app. IT also interacts with the "/" endpoint
  and the functions that define the URL. It also uses the configuration part of the code to set the values of "
  SERVER_NAME"and "PREFERRED_URL_SCHEME".

```Python
def test_basic_url_generation(app):
    app.config["SERVER_NAME"] = "localhost"
    app.config["PREFERRED_URL_SCHEME"] = "https"

    @app.route("/")
    def index():
        pass

    with app.app_context():
        rv = flask.url_for("index")
        assert rv == "https://localhost/"
```

### E. Initial State

- The initial stat of the system is having a Flask app spun up and waiting for an HTTPS request.

### F. Transition

- The transition trigger is when the "/" endpoint is called. At that point the response is stored in the variable rv.

### G. Expected State

- The expected final state is athat the Flask App has returned a valid response and that the URL of that response
  matches the expected output, namely "https://localhost/".

