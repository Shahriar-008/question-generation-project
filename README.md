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

- **Description:**: A small Python utility that generates a two-column, snaking MCQ paper (Microsoft Word `.docx`) from a JSON file of questions. The main script is `generate_paper.py`. The script writes a full-width header and creates a continuous two-column section for questions. Internally the script converts digit strings to Bengali numerals for display by default.

- **Main script:**: `generate_paper.py`

**Features**
- **Numeric conversion**: Converts numbers (time, total marks) to Bengali numerals inside the generated document (default behavior).
- **Two-column layout**: Creates a continuous section with two columns and snaking question flow.
- **Compact options**: Renders answer options in a 2x2 grid with option prefixes and an OMR-style circle symbol.
- **Complex questions**: Supports a `complex` question type which can include `sub_options` and a `final_prompt`.

**Requirements**
- **Python version**: 3.8+ is recommended.
- **Dependencies**: See `requirements.txt` (the project currently requires `python-docx`).

**Installation (PowerShell)**
```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```
pip install python-docx
```

**Quick Usage**
- **Input file**: `questions.json` (project root)
- **Output folder**: `output/`
- **Run**:
```powershell
python generate_paper.py
```
By default the script reads `questions.json` in the repository root and writes the output to `output/Generated_Paper_Correct_Header.docx` (see the `__main__` block in `generate_paper.py` for defaults).

**JSON format (example — English only)**
The input JSON should be an array of question objects. Each question object supports these fields:

- `id` (number): Question ID displayed before the text.
- `question_text` (string): The question content.
- `type` (string): `mcq` or `complex`.
- `answer_options` (array of strings): Up to four options are rendered in a 2x2 grid.
- `sub_options` (array of strings, optional): Used when `type` is `complex` to list sub-statements.
- `final_prompt` (string, optional): Prompt shown after `sub_options` for `complex` questions.

Example JSON:
```json
[
  {
    "id": 1,
    "question_text": "What is the capital of France?",
    "type": "mcq",
    "answer_options": ["Paris", "London", "Berlin", "Rome"]
  },
  {
    "id": 2,
    "question_text": "Which statement is correct?",
    "type": "complex",
    "sub_options": ["Statement A: The Earth orbits the Sun.", "Statement B: The Sun orbits the Earth."],
    "final_prompt": "Which statement is correct?",
    "answer_options": ["Only A", "Only B", "Both", "Neither"]
  }
]
```

**Output**
- The script writes a `.docx` file with a full-width header and the remainder in a continuous two-column section. Default output path: `output/Generated_Paper_Correct_Header.docx`.


**Notes & Tips**
- **Font**: The script sets the default font to `Nirmala UI` in `generate_paper.py`. For English-only papers you can choose a different font by editing the `style.font.name` line.
- **Numeric display**: The script converts digit strings to Bengali numerals for display. If you prefer to keep Arabic numerals, modify or remove the `to_bengali_numeral` usage in the header generation code.
- **File paths**: To change input or output paths, edit the `input_file` / `output_file` variables in the `__main__` block or call `create_question_paper()` from another script.
- **Layout tweaks**: Column count and spacing are defined in the section `w:cols` settings; adjust `w:num` and `w:space` in `generate_paper.py`.

**License**
- This repository is licensed under the MIT License — see the `LICENSE` file in the repository root.

**Contributing**
- Issues and pull requests are welcome. For non-trivial changes, please open an issue to discuss the design before submitting a PR.

**Contact**
- Author: `Shahriar-008` (GitHub)


**Contributing**
- Feel free to open issues or pull requests. For major changes, describe the behavior you want to change and include a minimal reproduction example.

**License**
- This repository currently has no license file. Add a `LICENSE` if you want to grant reuse permissions.
