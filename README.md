**Question Generation Project**

- **Description:**: A small Python utility that generates a two-column, snaking MCQ paper (Microsoft Word `.docx`) from a JSON file of questions. The script `generate_paper.py` builds a full-width header, converts numeric values to Bengali numerals, and lays out options in a compact 2x2 answer grid with Bengali option prefixes and OMR-style circles.

- **Main script:**: `generate_paper.py`

**Features**
- **Bengali numerals**: Converts numbers (time, total marks) to Bengali digits.
- **Two-column layout**: Creates a continuous section with two columns and snaking question flow.
- **Compact options**: Renders answer options in a 2x2 table with Bengali prefixes (`ক)`, `খ)`, `গ)`, `ঘ)`) and an OMR circle symbol.
- **Complex questions**: Supports a `complex` question type which can include `sub_options` and a `final_prompt`.

**Requirements**
- **Python version**: 3.8+ is recommended.
- **Dependencies**: `python-docx` (for `.docx` creation).

**Installation (PowerShell)**
**Question Generation Project**

- **Description:**: A small Python utility that generates a two-column, snaking MCQ paper (Microsoft Word `.docx`) from a JSON file of questions. The script `generate_paper.py` builds a full-width header, converts numeric values to Bengali numerals internally, and lays out options in a compact 2x2 answer grid with Bengali option prefixes and OMR-style circles. This README uses English-only examples.

- **Main script:**: `generate_paper.py`

**Features**
- **Numeric conversion**: Converts numbers (time, total marks) to Bengali numerals inside the document (this is the script's default behavior).
- **Two-column layout**: Creates a continuous section with two columns and snaking question flow.
- **Compact options**: Renders answer options in a 2x2 table with Bengali prefixes and an OMR circle symbol.
- **Complex questions**: Supports a `complex` question type which can include `sub_options` and a `final_prompt`.

**Requirements**
- **Python version**: 3.8+ is recommended.
- **Dependencies**: `python-docx` (for `.docx` creation).

**Installation (PowerShell)**
```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install python-docx
```

**Quick Usage**
- **Input file**: `questions.json` (project root)
- **Output folder**: `output/`
- **Run**:
```powershell
python generate_paper.py
```
The script uses the defaults in the `__main__` block and will write `output/Generated_Paper_Correct_Header.docx`.

**JSON format (example — English only)**
The input JSON should be an array of question objects. Example:
```json
[
  {
    "id": 1,
    "question_text": "What is the capital of France?",
    "type": "mcq",
    "answer_options": [
      "Paris",
      "London",
      "Berlin",
      "Rome"
    ]
  },
  {
    "id": 2,
    "question_text": "Which of the following statements is correct?",
    "type": "complex",
    "sub_options": [
      "Statement A: The Earth orbits the Sun.",
      "Statement B: The Sun orbits the Earth."
    ],
    "final_prompt": "Which statement is correct?",
    "answer_options": [
      "Only Statement A",
      "Only Statement B",
      "Both A and B",
      "Neither A nor B"
    ]
  }
]
```

**Output**
- The script writes a `.docx` file with a full-width header and the remainder in a continuous two-column section. Default output path: `output/Generated_Paper_Correct_Header.docx`.

**Notes & Tips**
- The script sets the default font to `Nirmala UI`. If you prefer English-only output or a different font, change the font settings in `generate_paper.py` (style section).
- If you want a different filename or input path, edit the `input_file` / `output_file` variables at the bottom of `generate_paper.py` or call `create_question_paper()` from another wrapper with custom paths.
- For small changes to layout (column spacing, font size), inspect the section/`cols` settings in `generate_paper.py`.

**Contributing**
- Feel free to open issues or pull requests. For major changes, describe the behavior you want to change and include a minimal reproduction example.

**License**
- This repository currently has no license file. Add a `LICENSE` if you want to grant reuse permissions.
