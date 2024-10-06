# Flask Code Challenge - Superheroes

This project is about an API for tracking heroes and their
superpowers.
- There is a Flask application with some features built out.
- There is a fully built React frontend application.
Depending on your preference, you can either check your API by:
- Using Postman to make requests

## Setup
To download the dependencies for the frontend and backend, run:

```console
pipenv install
pipenv shell
npm install --prefix client
```

You can run your Flask API on [`localhost:5555`](http://localhost:5555) by
running:

```console
python server/app.py
```

You can run your React app on [`localhost:4000`](http://localhost:4000) by
running:

```sh
npm start --prefix client
```


## Models
The file `server/models.py` defines the model classes **without relationships**.
Use the following commands to create the initial database `app.db`:

```console
export FLASK_APP=server/app.py
flask db init
flask db upgrade head
```

Now you can implement the relationships :

- A `Hero` has many `Power`s through `HeroPower`
- A `Power` has many `Hero`s through `HeroPower`
- A `HeroPower` belongs to a `Hero` and belongs to a `Power`

Update `server/models.py` to establish the model relationships. Since a
`HeroPower` belongs to a `Hero` and a `Power`, configure the model to cascade
deletes.

Set serialization rules to limit the recursion depth.

Run the migrations and seed the database:

```console
flask db revision --autogenerate -m 'message'
flask db upgrade head
python server/seed.py
```

> If you aren't able to get the provided seed file working, you are welcome to
> generate your own seed data to test the application.

## Validations

Add validations to the `HeroPower` model:

- `strength` must be one of the following values: 'Strong', 'Weak', 'Average'

Add validations to the `Power` model:

- `description` must be present and at least 20 characters long

## Routes
Set up the following routes. Make sure to return JSON data in the format
specified along with the appropriate HTTP verb.

## Author
Ombeyi Brenda.