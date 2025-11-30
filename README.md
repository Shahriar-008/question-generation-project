# Question Paper Generator

A Python utility to generate a two-column MCQ question paper in Microsoft Word (`.docx`) format from a simple `questions.json` file.

## Features

-   **Dual Document Output**: Generates two separate files:
    -   `Question_Paper.docx`: A clean version for students.
    -   `Question_Paper_With_Answers.docx`: A version for teachers with the correct answers marked.
-   **Two-Column Layout**: Creates a professional, space-saving two-column layout for questions.
-   **Customizable Formatting**:
    -   Easily change the font size for questions and options (currently set to 8pt).
    -   The header is formatted to align "Time" to the left and "Marks" to the right.
-   **Bengali Numeral Conversion**: Automatically converts numbers for time and total marks into Bengali numerals.
-   **Complex Questions**: Supports questions with multiple sub-options before the final prompt.
-   **OMR-Style Options**: Answer choices are presented in a 2x2 grid with OMR-style circles (`◯`).

## Requirements

-   Python 3.8+
-   Dependencies are listed in `requirements.txt`.

## Installation

1.  **Clone the repository (optional):**
    ```powershell
    git clone https://github.com/Shahriar-008/question-generation-project.git
    cd question-generation-project
    ```

2.  **Create and activate a virtual environment:**
    ```powershell
    # Use 'python' or 'py' depending on your system configuration
    py -m venv .venv
    .\.venv\Scripts\Activate.ps1
    ```

3.  **Install the required packages:**
    ```powershell
    pip install -r requirements.txt
    ```

## Usage

Simply run the main script from your terminal:

```powershell
python generate_paper.py
```

The script will read the questions from `questions.json` and generate the Word documents in the `output/` directory.

## Output

The script will produce two files in the `output/` folder:

1.  `Question_Paper.docx`: The question paper for students.
2.  `Question_Paper_With_Answers.docx`: The question paper with correct answers highlighted.

## JSON Format

The `questions.json` file should be an array of question objects. Each object has the following structure:

-   `id` (string): The question number.
-   `question_text` (string): The main text of the question.
-   `type` (string): Can be `simple` or `complex`.
-   `answer_options` (array of strings): The list of possible answers.
-   `correct_answer` (string): The exact text of the correct answer from the `answer_options`.
-   `sub_options` (array of strings, for `complex` type): A list of statements or sub-questions.
-   `final_prompt` (string, for `complex` type): The final question asked after the sub-options.

### Example:

```json
[
  {
    "id": "1",
    "question_text": "What is the capital of France?",
    "type": "simple",
    "answer_options": [
      "London",
      "Paris",
      "Berlin",
      "Rome"
    ],
    "correct_answer": "Paris"
  },
  {
    "id": "2",
    "question_text": "Consider the following statements:",
    "type": "complex",
    "sub_options": [
      "i. The Earth is flat.",
      "ii. The sun revolves around the Earth."
    ],
    "final_prompt": "Which of the above statements is correct?",
    "answer_options": [
      "i only",
      "ii only",
      "Both i and ii",
      "Neither i nor ii"
    ],
    "correct_answer": "Neither i nor ii"
  }
]
```

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.
