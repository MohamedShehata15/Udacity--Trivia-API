# Full Stack API Final Project

## Full Stack Trivia

Udacity is invested in creating bonding experiences for its employees and students. A bunch of team members got the idea to hold trivia on a regular basis and created a  webpage to manage the trivia app and play the game, but their API experience is limited and still needs to be built out. 

That's where you come in! Help them finish the trivia app so they can start holding trivia and seeing who's the most knowledgeable of the bunch. The application must:

1) Display questions - both all questions and by category. Questions should show the question, category and difficulty rating by default and can show/hide the answer. 
2) Delete questions.
3) Add questions and require that they include question and answer text.
4) Search for questions based on a text query string.
5) Play the quiz game, randomizing either all questions or within a specific category. 


## Getting Started
<hr>

### Pre-requisites and Local Development
<hr>
Developers using this project should already have Python3, pip and node installed on their local machines.<br><br>

### Database Setup
<hr>

With Postgres running, restore a database using the trivia.psql file provided. From the backend folder in terminal run:
```bash
psql trivia < trivia.psql
```

In windows
```bash
psql -h hostname -d trivia -U username -f trivia.psql
```

### Backend
<hr>

From the backend folder run
```
pip install
requirements.txt
```
All required packages are included in the requirements file.<br><br>

To run the application run the following commands:
```
export FLASK_APP=flaskr
export FLASK_ENV=development
flask run
```

Base URL: At present this app can only be run locally and is not hosted as a base URL. The backend app is hosted at the default, `http://127.0.0.1:5000/` , which is set as a proxy in the frontend configuration.

Authentication: This version of the application does not require authentication or API keys.<br><br>

### Frontend
<hr>

From the frontend folder, run the following commands to start the client:
```
npm install // only once to install dependencies
npm start
```
By default, the frontend will run on `localhost:3000`.<br><br>

## API Reference
<hr>

### Error Handling
Errors are returned as JSON objects in the following format:

```
{
    "success": False, 
    "error": 400,
    "message": "bad request"
}
```
The API will return three error types when requests fail:
* 400: Bad Request
* 404: Resource Not Found
* 422: Not Processable

<br>

### Endpoint

#### GET/categories
* General: Returns a list of category objects, success value, and total number of categories
* Sample: ```curl http://127.0.0.1:5000/categories ```

```
{
  "categories": {
    "1": "Science",
    "2": "Art",
    "3": "Geography",
    "4": "History",
    "5": "Entertainment",
    "6": "Sports"
  },
  "success": true,
  "total_categoreis": 6
}
```

#### GET/questions
* General
    * Returns a list of question objects, success value, and total number of questions
    * Results are paginated in groups of 10. Include a request argument to choose page number, starting from 1.
* Sample: ```curl http://127.0.0.1:5000/questions ```

```
{
  "categories": {
    "1": "Science",
    "2": "Art",
    "3": "Geography",
    "4": "History",
    "5": "Entertainment",
    "6": "Sports"
  },
  "current_category": [
    5,
    5,
    4,
    5,
    4,
    6,
    6,
    4,
    3,
    3
  ],
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
    },
    {
      "answer": "Maya Angelou",
      "category": 4,
      "difficulty": 2,
      "id": 5,
      "question": "Whose autobiography is entitled 'I Know Why the Caged Bird Sings'?"
    },
    {
      "answer": "Edward Scissorhands",
      "category": 5,
      "difficulty": 3,
      "id": 6,
      "question": "What was the title of the 1990 fantasy directed by Tim Burton about a young man with multi-bladed appendages?"
    },
    {
      "answer": "Muhammad Ali",
      "category": 4,
      "difficulty": 1,
      "id": 9,
      "question": "What boxer's original name is Cassius Clay?"
    },
    {
      "answer": "Brazil",
      "category": 6,
      "difficulty": 3,
      "id": 10,
      "question": "Which is the only team to play in every soccer World Cup tournament?"
    },
    {
      "answer": "Uruguay",
      "category": 6,
      "difficulty": 4,
      "id": 11,
      "question": "Which country won the first ever soccer World Cup in 1930?"
    },
    {
      "answer": "George Washington Carver",
      "category": 4,
      "difficulty": 2,
      "id": 12,
      "question": "Who invented Peanut Butter?"
    },
    {
      "answer": "Lake Victoria",
      "category": 3,
      "difficulty": 2,
      "id": 13,
      "question": "What is the largest lake in Africa?"
    },
    {
      "answer": "The Palace of Versailles",
      "category": 3,
      "difficulty": 3,
      "id": 14,
      "question": "In which royal palace would you find the Hall of Mirrors?"
    }
  ],
  "success": true,
  "total_questions": 14
}

```

#### GET/categories/{category_id}/questions
* General: Get questions by category id.
* Sample: ```curl http://127.0.0.1:5000/categories/2/questions ```

```
{
  "category": 2,
  "questions": [
    {
      "answer": "Escher",
      "category": 2,
      "difficulty": 1,
      "id": 16,
      "question": "Which Dutch graphic artist\u2013initials M C was a creator of optical illusions?"
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
  ],
  "success": true,
  "total_current_question": 3,
  "total_questions": 13
}
```



#### DELETE/questions/{question_id}
* General: Deletes the question of the given ID if it exists. Returns the id of the deleted question, success value, total questions, and question list based on current page number to update the frontend.
=======
#### DELETE /questions/{question_id}
* General: Deletes the question of the given ID if it exists. Returns the id of the deleted question, success value, total question, and question list based on current page number to update the frontend.

* Sample: ```curl http://127.0.0.1:5000/questions/5 -X DELETE ```

```
{
  "deleted": 5,
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
    },
    {
      "answer": "Edward Scissorhands",
      "category": 5,
      "difficulty": 3,
      "id": 6,
      "question": "What was the title of the 1990 fantasy directed by Tim Burton about a young man with multi-bladed appendages?"
    },
    {
      "answer": "Muhammad Ali",
      "category": 4,
      "difficulty": 1,
      "id": 9,
      "question": "What boxer's original name is Cassius Clay?"
    },
    {
      "answer": "Brazil",
      "category": 6,
      "difficulty": 3,
      "id": 10,
      "question": "Which is the only team to play in every soccer World Cup tournament?"
    },
    {
      "answer": "Uruguay",
      "category": 6,
      "difficulty": 4,
      "id": 11,
      "question": "Which country won the first ever soccer World Cup in 1930?"
    },
    {
      "answer": "George Washington Carver",
      "category": 4,
      "difficulty": 2,
      "id": 12,
      "question": "Who invented Peanut Butter?"
    },
    {
      "answer": "Lake Victoria",
      "category": 3,
      "difficulty": 2,
      "id": 13,
      "question": "What is the largest lake in Africa?"
    },
    {
      "answer": "The Palace of Versailles",
      "category": 3,
      "difficulty": 3,
      "id": 14,
      "question": "In which royal palace would you find the Hall of Mirrors?"
    },
    {
      "answer": "Agra",
      "category": 3,
      "difficulty": 2,
      "id": 15,
      "question": "The Taj Mahal is located in which Indian city?"
    }
  ],
  "success": true,
  "total_questions": 13
}
```


#### POST/questions
* General: Creates a new question using the submitted title, author and rating. Returns the id of the created question, success value, total questions, and question list based on current page number to update the frontend..
* Sample: ```curl -X POST -H 'Content-Type: application/json' -d '{ "question": "New Question?", "answer": "New Answer", "difficulty": "1", "category": "5"}' http://127.0.0.1:5000/questions```

```
{
    "created": 88,
    "questoins": {
        "answer": "New Answer",
        "category": 5,
        "difficulty": 1,
        "id": 88,
        "question": "New Question?"
    },
    "success": true,
    "total_questions": 14
}
```

#### POST/qeustions/search
* General: Returns all the questions that contain the value in the Search input.
* Sample: ```curl -X POST -H 'Content-Type: application/json' -d '{ "searchTerm": "Africa"}' http://127.0.0.1:5000/questions/search ```

```
{
    "current_category": [
        3
    ],
    "questions": [
        {
            "answer": "Lake Victoria",
            "category": 3,
            "difficulty": 2,
            "id": 13,
            "question": "What is the largest lake in Africa?"
        }
    ],
    "sucess": true,
    "total_questions": 14
}
```


#### POST/quizzes
* General: Returns the current quiz question.
* Sample: ```curl -X POST -H 'Content-Type: application/json' -d '{"previous_questions": [10], "quiz_category": {"type": "Sports", "id": "6"}}' http://127.0.0.1:5000/quizzes ```

```
{
    "question": {
        "answer": "Uruguay",
        "category": 6,
        "difficulty": 4,
        "id": 11,
        "question": "Which country won the first ever soccer World Cup in 1930?"
    },
    "success": true
}
```

