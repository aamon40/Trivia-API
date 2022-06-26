# Full Stack Trivia Game

## Udacitrivia

Udacitrivia is a fun trivia game that helps to create bonding experiences between teams. It can be played by anyone. It has questions of varying difficulty from 6 interesting categories; Science, Art, Geography, History, Entertainment and Sports. It is a Full Stack app with a React based front-end and a Flask based back-end.

<!-- Udacity is invested in creating bonding experiences for its employees and students. A bunch of team members got the idea to hold trivia on a regular basis and created a webpage to manage the trivia app and play the game, but their API experience is limited and still needs to be built out.

That's where you come in! Help them finish the trivia app so they can start holding trivia and seeing who's the most knowledgeable of the bunch. The application must: -->

## API Description

1. Display questions - all questions and by category. Questions show the question, category and difficulty rating by default and can show/hide the answer.
2. Quesstions can be deleted easily.
3. Questions can be added but require that they include question and answer text.
4. Questions can be searched based on a text query string that is case insensitive.
5. The quiz game can be played by randomizing either all questions or questions within a specific category.

<!-- Completing this trivia app will give you the ability to structure plan, implement, and test an API - skills essential for enabling your future applications to communicate with others. -->

<!-- [Fork](https://help.github.com/en/articles/fork-a-repo) the project repository and [clone](https://help.github.com/en/articles/cloning-a-repository) your forked repository to your machine. Work on the project locally and make sure to push all your changes to the remote repository before submitting the link to your repository in the Classroom. -->

## Requirements to set up

<!-- The [backend](./backend/README.md) directory contains a partially completed Flask and SQLAlchemy server. You will work primarily in `__init__.py` to define your endpoints and can reference models.py for DB and SQLAlchemy setup. These are the files you'd want to edit in the backend:

1. `backend/flaskr/__init__.py`
2. `backend/test_flaskr.py`

> View the [Backend README](./backend/README.md) for more details. -->

### Setting up the Backend

### Install Dependencies

1. **Python 3.7** - Follow instructions to install the latest version of python for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)

2. **Virtual Environment** - We recommend working within a virtual environment whenever using Python for projects. This keeps your dependencies for each project separate and organized. Instructions for setting up a virual environment for your platform can be found in the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)

3. **PIP Dependencies** - Once your virtual environment is setup and running, install the required dependencies by navigating to the `/backend` directory and running:

```bash
pip install -r requirements.txt
```

#### Key Pip Dependencies

- [Flask](http://flask.pocoo.org/) is a lightweight backend microservices framework. Flask is required to handle requests and responses.

- [SQLAlchemy](https://www.sqlalchemy.org/) is the Python SQL toolkit and ORM we'll use to handle the lightweight SQL database. You'll primarily work in `app.py`and can reference `models.py`.

- [Flask-CORS](https://flask-cors.readthedocs.io/en/latest/#) is the extension we'll use to handle cross-origin requests from our frontend server.

### Set up the Database

With Postgres running, create a `trivia` database:

```bash
createbd trivia
```

Populate the database using the `trivia.psql` file provided. From the `backend` folder in terminal run:

```bash
psql trivia < trivia.psql
```

### Run the Server

From within the `./src` directory first ensure you are working using your created virtual environment.

To run the server, execute:

```bash
export FLASK_APP=flaskr
export FLASK_ENV=development
flask run --reload
```

### Frontend

# Frontend - Trivia API

## Getting Setup

> _tip_: this frontend is designed to work with [Flask-based Backend](../backend) so it will not load successfully if the backend is not working or not connected. We recommend that you **stand up the backend first**, test using Postman or curl, update the endpoints in the frontend, and then the frontend should integrate smoothly.

### Installing Dependencies

1. **Installing Node and NPM**
   This project depends on Nodejs and Node Package Manager (NPM). Before continuing, you must download and install Node (the download includes NPM) from [https://nodejs.com/en/download](https://nodejs.org/en/download/).

2. **Installing project dependencies**
   This project uses NPM to manage software dependencies. NPM Relies on the package.json file located in the `frontend` directory of this repository. After cloning, open your terminal and run:

```bash
npm install
```

> _tip_: `npm i`is shorthand for `npm install``

## Required Tasks

### Running Your Frontend in Dev Mode

The frontend app was built using create-react-app. In order to run the app in development mode use `npm start`. You can change the script in the `package.json` file.

Open [http://localhost:3000](http://localhost:3000) to view it in the browser. The page will reload if you make edits.

```bash
npm start
```

## Tests

In order to run tests, navigate to the backend folder and run the following commands:

```bash
dropdb trivia_test
createdb trivia_test
psql trivia_test < trivia.psql
python test_flaskr.py
```

Omit the 'dropdb' command the first time you run the tests.

All tests are kept in that file and should be maintained as updaates are made to app functionality.

# API Reference

## Getting Started

- Base URL: At present this app is not hosted as a base URL. The backend app is hosted at the default, http://127.0.0.1:5000/ which is set as a proxy in the frontend configuration.
- Authentication: This version of the application does not require authentication or API keys.

## Error Handling

Errors are returned as JSON objects in the following format:

```bash
{
    "success": False,
    "error": 400,
    "message": "bad request"
}
```

The API will return the following errors when requests fail:

- 400: bad request
- 404: resource not found
- 422: unprocessable

# Endpoints

## GET '/categories'

- Returns: An object with a single key, categories, that contains an object of id: category_string key:value pairs.
- Request Arguments: None

Sample: curl http://127.0.0.1:5000/categories

```bash
{
	'1' : "Science",
	'2' : "Art",
	'3' : "Geography",
	'4' : "History",
	'5' : "Entertainment",
	'6' : "Sports"
}
```

## GET '/questions'

- Returns a list of questions, success value, and total number of questions. Also returns a list of the categories.
- Results are paginated in groups of 10. Include a request argument to choose page number, starting from 1.

Sample: curl http://127.0.0.1:5000/questions

```bash
{
  "categories": {
    "1": "Science",
    "2": "Art",
    "3": "Geography",
    "4": "History",
    "5": "Entertainment",
    "6": "Sports"
  },
  "current_category": null,
  "questions": [
    {
      "answer": "Apollo 13",
      "category": 5,
      "difficulty": 4,
      "id": 2,
      "question": "What movie earned Tom Hanks his third straight Oscar nomination, in 1996?"
    },
    {
      "answer": "Tom Cruise",
      "category": 5,
      "difficulty": 4,
      "id": 4,
      "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
    }
    ],
    ...#some results have been omitted.
    "success": true,
  "total_questions": 25
}
```

## DELETE /questions/{question_id}

- Deletes a selected question by id if it exists.
- Returns a JSON object of the deleted_id, remaining questions, and length of total questions.

Sample: curl -X DELETE http://127.0.0.1:5000/questions/16?page=2

```bash
{
"deleted_question": "16",
  "questions": [
    {
      "answer": "Agra",
      "category": 3,
      "difficulty": 2,
      "id": 15,
      "question": "The Taj Mahal is located in which Indian city?"
    },
    {
      "answer": "Mona Lisa",
      "category": 2,
      "difficulty": 3,
      "id": 17,
      "question": "La Giaconda is better known as what?"
    },
    {
      "answer": "One",
      "category": 2,
      "difficulty": 4,
      "id": 18,
      "question": "How many paintings did Van Gogh sell in his lifetime?"
    }
    ...#omission
  ],
 "success": true,
  "total_questions": 24
}
```

## POST '/questions'

- Creates a new question posted from the front end, with required
  fields: answer, difficulty and category.
- Returns a success value and ID of the question.

Sample: curl http://127.0.0.1:5000/questions -X POST -H "Content-Type: application/json" -d '{"question":"Who is the founder of Space X?", "answer":"Elon Musk", "category":"1", "difficulty":"2"}'

```bash
{
    "new_question": 41,
    "success": true
}
```

## POST '/questions/search'

- Return questions with matching strings if present and none if not present. Search is case insensitive.

Sample: curl http://127.0.0.1:5000/questions -X POST -H "Content-Type: application/json" -d '{"searchTerm":"actor"}'

```bash
{
    "current_category": null,
    "questions": [
        {
            "answer": "Tom Cruise",
            "category": 5,
            "difficulty": 4,
            "id": 4,
            "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
        }
    ],
    "success": true,
    "total_questions": 1
}
```

## GET '/categories/{category_id}/questions'

- Returns JSON response of current_category, and all the questions in the specified.

Sample: curl http://localhost:5000/categories/1/questions

```bash
{
    "categories": [
        "Science",
        "Art",
        "Geography",
        "History",
        "Entertainment",
        "Sports"
    ],
    "current_category": {
        "id": 1,
        "type": "Science"
    },
    "questions": [
        {
            "answer": "The Liver",
            "category": 1,
            "difficulty": 4,
            "id": 20,
            "question": "What is the heaviest organ in the human body?"
        }

        ...#omission
    ],
    "success": true,
    "total_questions": 4
}
```

## POST '/quizzes'

- Allows the user to create either a random quiz or one based on category.

Sample: curl http://localhost:5000/quizzes -X POST -H "Content-Type: application/json" -d '{"previous_questions":[], "quiz_category":{"type":"Art","id":2}}'

```bash
{
    "question": {
        "answer": "Blood",
        "category": 1,
        "difficulty": 4,
        "id": 22,
        "question": "Hematology is a branch of medicine involving the study of what?"
    },
    "success": true
}
```
