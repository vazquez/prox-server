# prox-server
This is the server side component to the first NMX prototype project.

# Setup
Set up a virtualenv (assuming you already installed virtualenv with pip) and install dependencies.

    virtualenv env
    source env/bin/activate
    pip install -r requirements.txt

and `deactivate` to leave the virtualenv.

## Firebase
Add the path to the Firebase credentials json file to `config.py`, and then run

    python -m samples.firebase-test

You can view real-time changes to the database on the console.

## Testing
Testing is done via [pytest](pytest.org):

    pytest

All tests should pass before landing on `master`.

## Running

The project is a `flask` server which puts jobs on a `rq` task queue.

Thus, the app is run in three parts:

Run redis:

    redis-server

Then run the flask web app:

    python app.py

Then run the workers which will consume the tasks coming from the web server.

    rq worker -c rq_settings