# Helpbot
HelpBot: A Streamlit Chatbot
# HelpBot: A Streamlit Chatbot

HelpBot is a chatbot application built using Streamlit, LangChain, and LlamaIndex, designed to assist users with various queries. The chatbot can generate responses based on context created from uploaded documents and handle special case inputs.

## Features
- User-friendly chat interface
- Dynamic response generation using LLM (OpenAI)
- Context creation from documents
- Special case handling for specific inputs
- Logging with automatic log file archiving

## Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/rishalu/HelpBot.git
   cd HelpBot
   
2. **Install dependencies: Ensure you have Python installed.** 
Then, install the required packages:
    ```bash
    pip install -r requirements.txt

3. **Set up your environment**
- Ensure you have a valid OpenAI API key.
- Create a .streamlit directory in the root of the project.
- Inside the .streamlit directory, create a secrets.toml file.
- Store your OpenAI API key in the secrets.toml file in the following format:
  ```arduino
  openai_api_key = "your-openai-api-key"

## Usage
Run the Streamlit app with the following command:
    ```bash
  streamlit run mainbot.py

## Functions
**archive_log_file(log_file_path, archive_dir, max_size_kb)**
Archives the log file if it exceeds the specified maximum size. The log file is zipped and stored in the archive directory.

**create_context()**
Creates or recreates the context from documents in the DOC_DIR. The context is then stored in PERSIST_DIR. If the directory already exists, it is removed and recreated.

**initialize_session_state()**
Initializes the Streamlit session state for chat history, token count, and conversation history. 
This ensures that the chatbot's conversation memory and input states are properly managed across user interactions.

**on_click_callback()**
Handles user input when the submit button is clicked. The function processes the input, checks for special cases, queries the AI model, and generates responses. 
It also manages errors and appends chat messages to the session history.

## Customization
**CSS Styling**
The chatbot's appearance is customized using inline CSS styles. You can modify the styling directly in the st.markdown section of the code to change colors, fonts, and other design elements.

**Special Case Handling**
Special cases are handled in the on_click_callback function. You can extend the special_cases dictionary to include additional specific responses based on user input.

**Log Archiving**
The archive_log_file function automatically archives the log file if it exceeds MAX_LOG_SIZE_KB. Adjust the MAX_LOG_SIZE_KB variable to change the log size threshold.

**Logs**
The application logs important events and errors into a log file named app4.log. The log file is automatically archived when it exceeds the specified maximum size.


## Acknowledgements
- Streamlit
- LangChain
- LlamaIndex

## Important Notes

- **Data Folder:**
  - Ensure there is a folder named `data` in the project directory.
  - This folder should contain a PDF file that will be used for context creation.
  - The PDF file will be parsed and indexed automatically by the application.

- **Storage:**
  - Upon context creation, a storage file will be generated automatically.
  - The storage file contains JSON embeddings and is saved in the `PERSIST_DIR`.

- **Log File:**
  - A log file named `app.log` will be created automatically in the project directory.
  - Once the log file reaches a specified size threshold, it will be compressed into a zip file.
  - The compressed log file will be stored in a folder named `archives`.
