# Quiz Brain Game Project

Welcome to the Quiz Brain Game Project! This project is a simple quiz game implemented in Python using Object-Oriented Programming (OOP) principles. The game asks the user a series of True/False questions and keeps track of their score. This README provides an overview of the project, its structure, and how to run it.

## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Code Structure](#code-structure)
- [Contributing](#contributing)
- [License](#license)

## Project Overview

The Quiz Brain Game Project is designed to demonstrate the use of OOP in Python. It includes classes for representing questions and managing the quiz logic. The questions are stored in a list of dictionaries, and the game logic iterates through these questions, prompting the user for their answers and providing feedback.

## Features

- Object-Oriented design with classes for questions and quiz logic.
- Simple True/False questions.
- Keeps track of the user's score and displays it after each question.
- Provides feedback on whether the user's answer is correct or not.
- Displays the final score at the end of the quiz.

## Installation

To run this project, you need to have Python installed on your machine. Follow these steps to get started:

1. Clone this repository:
    ```bash
    git clone https://github.com/your-username/quiz-brain-game.git
    cd quiz-brain-game
    ```

2. (Optional) Create a virtual environment and activate it:
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    ```

3. Install any required dependencies (if any):
    ```bash
    pip install -r requirements.txt  # If a requirements.txt file is provided
    ```

## Usage

To start the quiz, run the following command:
```bash
python main.py
```

The game will prompt you with True/False questions. Type your answer and press Enter. The game will provide feedback and keep track of your score. After all questions have been answered, the game will display your final score.

## Code Structure

The project is organized into the following files:

- `question_model.py`: Contains the `Question` class.
- `quiz_brain.py`: Contains the `QuizBrain` class.
- `data.py`: Contains the list of questions used in the quiz.
- `main.py`: The main entry point of the program, which sets up the quiz and runs it.

### `question_model.py`
```python
class Question:
    def __init__(self, q_text, q_answer):
        self.text = q_text
        self.answer = q_answer
```

### `quiz_brain.py`
```python
class QuizBrain:
    def __init__(self, q_list):
        self.question_number = 0
        self.score = 0
        self.question_list = q_list

    def still_has_questions(self):
        return self.question_number < len(self.question_list)

    def next_question(self):
        current_question = self.question_list[self.question_number]
        self.question_number += 1
        user_answer = input(f"Q.{self.question_number}: {current_question.text} (True/False): ")
        self.check_answer(user_answer, current_question.answer)

    def check_answer(self, user_answer, correct_answer):
        if user_answer.lower() == correct_answer.lower():
            self.score += 1
            print("You got it right!")
        else:
            print("That's wrong.")
        print(f"The correct answer was: {correct_answer}.")
        print(f"Your current score is: {self.score}/{self.question_number}")
        print("\n")
```

### `data.py`
```python
question_data = [
    {"type": "boolean", "difficulty": "easy", "category": "Animals",
     "question": "The Killer Whale is considered a type of dolphin.",
     "correct_answer": "True", "incorrect_answers": ["False"]},
    # Additional questions...
]
```

### `main.py`
```python
from question_model import Question
from data import question_data
from quiz_brain import QuizBrain

question_bank = []
for question in question_data:
    question_text = question["question"]
    question_answer = question["correct_answer"]
    new_question = Question(question_text, question_answer)
    question_bank.append(new_question)

quiz = QuizBrain(question_bank)

while quiz.still_has_questions():
    quiz.next_question()

print("You've completed the quiz")
print(f"Your final score was: {quiz.score}/{quiz.question_number}")
```

## Contributing

Contributions are welcome! If you have any suggestions or improvements, feel free to open an issue or create a pull request.

If you have any questions, feel free to reach out. Enjoy my Quiz Brain Game!
