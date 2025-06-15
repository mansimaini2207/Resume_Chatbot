# Resume Chatbot

A personalized AI chatbot that answers questions about your professional background using Google's Gemini AI. The chatbot responds in first-person as the resume owner, providing natural and conversational answers about experience, skills, and achievements.

## Features

- **Personalized Responses**: The chatbot responds as the resume owner in first-person
- **Resume-Based Knowledge**: Only uses information from the provided resume file
- **Interactive Chat**: Continuous conversation loop with natural language processing
- **Error Handling**: Robust error handling for API calls and file operations
- **Customizable**: Easy to adapt for different resumes and personalities

## Prerequisites

- Python 3.7 or higher
- Google Gemini API key
- Resume data in text format

## Installation

1. **Clone or download the code**
2. **Install required dependencies**:
   ```bash
   pip install google-generativeai
   ```

3. **Get a Gemini API key**:
   - Visit [Google AI Studio](https://makersuite.google.com/app/apikey)
   - Create a new API key
   - Keep it secure and don't share it publicly

## Setup

1. **Configure your API key**:
   ```python
   API_KEY = "your_actual_api_key_here"
   ```

2. **Create your resume file**:
   - Create a text file named `mansi_resume.txt` (or update the path)
   - Add your resume information in plain text format
   - Include sections like experience, skills, education, projects

3. **Customize the chatbot**:
   - Update the name in the `create_system_prompt()` method
   - Modify the system prompt to match your personality/style

## Usage

### Basic Usage

```python
from resume_chatbot import ResumeChatbot

# Initialize the chatbot
chatbot = ResumeChatbot(api_key="your_api_key", resume_file_path="your_resume.txt")

# Start interactive chat
chatbot.chat()
```

##### Single Query

```python
# Get a single response
response = chatbot.get_response("What is your experience with Python?")
print(response)
```

### Running the Application

```bash
python app.py
```

## Code Structure

### Class: `ResumeChatbot`

The main class that handles all chatbot functionality:

#### Methods:

- **`__init__(api_key, resume_file_path)`**: Initializes the chatbot with API configuration and resume data
- **`load_resume_data(file_path)`**: Reads and loads resume content from text file
- **`create_system_prompt()`**: Creates the system prompt that defines the chatbot's personality and instructions
- **`get_response(user_query)`**: Processes user queries and generates AI responses
- **`chat()`**: Starts an interactive chat session

### Key Features of the Implementation:

1. **System Prompt Engineering**: 
   - Configures the AI to respond in first-person as the resume owner
   - Restricts responses to only resume-provided information
   - Maintains professional yet conversational tone

2. **File Handling**:
   - Robust file reading with error handling
   - UTF-8 encoding support for international characters

3. **Error Management**:
   - Graceful handling of API errors
   - File not found protection
   - User-friendly error messages

## Resume File Format

Create a text file with your resume information. Here's the recommended structure:

```text
[YOUR NAME] - [YOUR TITLE]

EXPERIENCE:
- [Job Title] at [Company] ([Duration])
  - [Key responsibility/achievement]
  - [Key responsibility/achievement]

- [Previous Job Title] at [Previous Company] ([Duration])
  - [Key responsibility/achievement]

SKILLS:
- Programming Languages: [List languages]
- Frameworks: [List frameworks]
- Tools: [List tools]
- Databases: [List databases]

EDUCATION:
- [Degree] in [Field]
- [Relevant coursework or achievements]

PROJECTS:
- [Project Name]: [Brief description]
```

## Customization

### Changing the Persona

To adapt this for a different person:

1. Update the name in `create_system_prompt()`:
   ```python
   return f"""
   You are [NEW_NAME], responding to questions about yourself...
   ```

2. Update the chat display name:
   ```python
   print(f"[NEW_NAME]: {response}\n")
   ```

### Modifying Response Style

Adjust the system prompt to change how the chatbot responds:

```python
def create_system_prompt(self) -> str:
    return f"""
    You are [NAME], a [PROFESSION] with [X] years of experience.
    
    RESPONSE STYLE:
    - Be [enthusiastic/professional/casual]
    - Include [specific details you want emphasized]
    - Always mention [key points to highlight]
    
    [Rest of prompt...]
    """
```

## Testing

The code includes built-in testing functionality:

```python
# Test with multiple predefined queries
test_specific_queries(chatbot)

# Sample test queries included:
# - "What is your overall experience?"
# - "What skills do you have?"
# - "Tell me about your work at [Company]"
# - "What projects have you worked on?"
# - "What's your educational background?"
```

## Security Notes

- **Never commit your API key** to version control
- Store API keys in environment variables for production use:
  ```python
  import os
  API_KEY = os.getenv('GEMINI_API_KEY')
  ```
- Keep your resume file updated and accurate

## Troubleshooting

### Common Issues:

1. **"Resume file not found"**
   - Check the file path is correct
   - Ensure the file exists in the specified location

2. **API Key errors**
   - Verify your Gemini API key is valid
   - Check you have API quota available

3. **Empty responses**
   - Ensure your resume file has content
   - Check your internet connection for API calls

4. **Import errors**
   - Install required packages: `pip install google-generativeai`

## Future Enhancements

Potential improvements you could add:

- **Multiple file formats**: Support for PDF, Word documents
- **Web interface**: Flask/FastAPI web application
- **Voice interaction**: Speech-to-text and text-to-speech
- **Analytics**: Track common questions and optimize responses
- **Multiple personas**: Support for different professional profiles
- **Context memory**: Remember conversation history within a session

## Contributing

Feel free to fork this project and submit pull requests for improvements. Some areas for contribution:

- Enhanced error handling
- Additional file format support
- UI improvements
- Performance optimizations
- Documentation improvements

## License

This project is open-source. Please ensure you comply with Google's Gemini API terms of service when using this application.

---

**Note**: This chatbot is designed for personal/professional use to showcase your background. Always ensure the information in your resume file is accurate and up-to-date.