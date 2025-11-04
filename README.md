AI Terminal Assistant
An AI-powered terminal assistant that converts natural language into terminal commands, provides human-friendly explanations, and warns users about dangerous operations — all while working completely offline using local models.
Features
• Converts plain English to terminal commands
• Explains each command in simple terms
• Detects and warns about dangerous commands
• Works offline (no internet or API required)
• Cross-platform (Windows / Linux / macOS supported)
• Optional confirmation before execution
• Built using local LLMs like Mistral via GPT4All
Tech Stack
Language Model: Mistral-7B (GGUF) via GPT4All
Backend Engine: Python 3.9+
NLP Parsing: GPT4All local inference
Command Execution: subprocess
Risk Detection: Regex-based analyzer
CLI Interface: Rich + Prompt Toolkit
Packaging: setuptools (pyproject.toml)
Installation (From PyPI)
You can install the assistant directly as a Python package:
pip install ai-terminal-assistant
Important: This package depends on a local model file. You need to manually download and place it before running.
Model Setup
1. Create a folder named 'models' inside your project or home directory.
2. Download the Mistral-7B Instruct model from: https://gpt4all.io/models/
3. Place the model file (mistral-7b-instruct.Q4_K_M.gguf) inside the 'models' folder.
4. The default configuration automatically detects this path.
Running the Assistant
Once installed and model is in place, simply run:
assistant
Or, if you cloned the repository:
python -m assistant.main
Example Usage
Input: Show all files in this folder
Output: dir – Lists all files and folders in the current directory.
Input: Delete the text file named notes.txt
Output: del notes.txt – Deletes the specified file permanently.
Risk Detection Logic
The assistant uses a regex-based analyzer (risk.py) to detect dangerous patterns such as:
Super Dangerous: rm -rf /, format C: → Blocked
Dangerous: del, chmod -R 777 → Warn
Safe: dir, cd, type → Allowed
Troubleshooting
1. 'Model not found' – Ensure the model file exists in the models folder.
2. 'assistant not recognized' – Activate your Python environment or reinstall the package.
3. 'Permission denied' – Command might be detected as risky by the safety module.
Developer Mode (Run from Source)
git clone https://github.com/<yourusername>/ai-terminal-assistant.git
cd ai-terminal-assistant
pip install -e .
python -m assistant.main
Project Structure

ai-terminal-assistant/
│
├── assistant/
│   ├── main.py
│   ├── command_gen.py
│   ├── explain.py
│   ├── risk.py
│   ├── executor.py
│   ├── nlu.py
│   ├── io_cli.py
│   └── utils.py
│
├── data/
│   ├── flags_windows.yaml
│   ├── flags_linux.yaml
│
├── models/
│   └── mistral-7b-instruct.Q4_K_M.gguf
│
├── config.yaml
├── pyproject.toml
└── README.md

Credits
Developed by: Nidhi Kushwaha and Team AI Terminal Assistant
Department of Computer Engineering, Bangalore Institute of Technology

MIT License © 2025 Nidhi Kushwaha
