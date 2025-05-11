# 🤖 EmpatheticAI: Mental Health Support Chatbot

![EmpatheticAI Banner]("https://github.com/Pranay22077/Empathetical-AI/blob/main/Screenshot%202025-03-30%20121555.png")

<div align="center">
  
  [![Python Version](https://img.shields.io/badge/python-3.7%2B-blue.svg)](https://www.python.org/downloads/)
  [![Google Gemini](https://img.shields.io/badge/Powered%20by-Gemini%201.5%20Pro-blue.svg)](https://ai.google.dev/)
  [![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
  [![Status](https://img.shields.io/badge/status-active-success.svg)]()
  
</div>

---

## 📋 Table of Contents
- [Overview](#-overview)
- [Features](#-features)
- [System Requirements](https://github.com/Pranay22077/Empathetical-AI/blob/main/requirements.txt)
- [Installation](#-installation)
- [Usage](#-usage)
- [API Key Setup](#-api-key-setup)
- [How It Works](#-how-it-works)
- [Troubleshooting](#-troubleshooting)
- [Contributing](#-contributing)
- [License](#-license)
- [Acknowledgements](#-acknowledgements)

---

## 🌟 Overview

**EmpatheticAI** is an advanced mental health support chatbot built on Google's Gemini 1.5 Pro Large Language Model. It provides empathetic, personalized responses to users experiencing emotional distress or mental health challenges.

This chatbot is designed to be a supportive tool that practices active listening, offers coping strategies, and provides resources while maintaining ethical boundaries and prioritizing user safety.

> **Note:** EmpatheticAI is not a replacement for professional mental health care. It's designed as a complementary support tool.

---

## ✨ Features

- **🧠 Empathetic Engagement:** Recognizes emotional cues and adapts tone accordingly
- **👤 Personalized Support:** Tailors responses based on user history and preferences
- **🛡️ Crisis Detection:** Identifies potential crisis situations and provides appropriate resources
- **🔄 Persistent Conversations:** Maintains context throughout user interactions
- **📊 Response Analysis:** Evaluates safety and estimated user satisfaction
- **⏱️ Rate Limit Handling:** Built-in retry logic for API rate limits
- **🔒 Ethical Boundaries:** Never diagnoses conditions or prescribes medications

---

## 💻 System Requirements

- Python 3.7+
- Internet connection for API access
- Google Gemini API key

---

## 📥 Installation

1. **Clone the repository or download the source code:**

```bash
git clone https://Pranay22077/Empathetical-AI.git
cd empathetic-ai
```

2. **Install required dependencies:**

```bash
pip install -r requirements.txt
```

3. **Set up your Google Gemini API key:**

```bash
# For Linux/macOS
export GEMINI_API_KEY='your-api-key'

# For Windows
set GEMINI_API_KEY=your-api-key
```

Alternatively, create a `.env` file in the project root with:

```
GEMINI_API_KEY=your-api-key
```

---

## 🚀 Usage

### Basic Usage

```python
from gemini_chatbot import GeminiChatbot

# Initialize the chatbot
chatbot = GeminiChatbot()  # Will use GEMINI_API_KEY from environment

# Generate a response
response = chatbot.generate_response("user123", "I'm feeling really anxious today")
print(response["text"])

# Check if any critical issues were detected
if response["detected_issues"]:
    print("Critical issues detected:", response["detected_issues"])
```

### Integration Example

```python
# For a simple command-line interface
chatbot = GeminiChatbot()
user_id = "local_user"

print("EmpatheticAI: Hello! I'm here to provide mental health support. How are you feeling today?")
print("(Type 'exit' to quit)")

while True:
    user_input = input("You: ")
    if user_input.lower() == "exit":
        break
    
    response = chatbot.generate_response(user_id, user_input)
    print(f"EmpatheticAI: {response['text']}")
    
    # Check for critical issues
    if response["detected_issues"]:
        if "suicide_risk" in response["detected_issues"] or "self_harm_risk" in response["detected_issues"]:
            print("\n⚠️ IMPORTANT: If you're in crisis, please call the National Suicide Prevention Lifeline: 988")
```

---

## ⚙️ Advanced Configuration

The `GeminiChatbot` class accepts several configuration parameters:

```python
chatbot = GeminiChatbot(
    api_key="your-api-key",  # Override environment variable
    max_retries=5,           # Maximum number of retries for rate limits
    retry_delay=3            # Initial delay between retries (seconds)
)
```

You can also customize the safety settings by modifying the `safety_levels` dictionary in the class.

---

## 🔑 API Key Setup

1. Visit [Google AI Studio](https://ai.google.dev/)
2. Create a new project or select an existing one
3. Navigate to the API & Services section
4. Enable the Gemini API
5. Create credentials and generate an API key
6. Use this key in your application

---

## 🔄 How It Works

### Architecture

EmpatheticAI uses the following components:

1. **Session Management:** Maintains persistent chat sessions for each user
2. **Response Generation:** Uses Gemini 1.5 Pro to generate empathetic responses
3. **Content Safety:** Implements safety filters to prevent harmful content
4. **Issue Detection:** Identifies potential crisis situations through pattern matching
5. **Response Analysis:** Evaluates response quality and safety

### Conversation Flow

```
┌─────────────┐    ┌─────────────┐    ┌─────────────────┐
│ User Input  │───>│ Issue       │───>│ Response        │
└─────────────┘    │ Detection   │    │ Generation      │
                   └─────────────┘    └─────────────────┘
                         │                     │
                         v                     v
                   ┌─────────────┐    ┌─────────────────┐
                   │ Safety      │<───│ Response        │
                   │ Analysis    │    │ Analysis        │
                   └─────────────┘    └─────────────────┘
                         │                     │
                         v                     v
                   ┌──────────────────────────────────┐
                   │           Final Response         │
                   └──────────────────────────────────┘
```

---

## 🛡️ Safety & Ethics

EmpatheticAI prioritizes user safety and ethical considerations:

- **No Medical Advice:** The bot never provides medical advice or diagnoses
- **Crisis Detection:** Identifies potential crisis situations through pattern matching
- **Resource Sharing:** Provides appropriate resources for specific situations
- **Domain Restriction:** Focuses solely on mental health support topics
- **Privacy:** Maintains user privacy and confidentiality

---

## ❓ Troubleshooting

### Common Issues

#### API Rate Limit Errors

```
Error: 429 You exceeded your current quota, please check your plan and billing details.
```

**Solution:** 
- Verify your API key is correct
- Check your quota limits in the Google Cloud Console
- Consider upgrading your plan for higher quotas

#### No Response Generated

**Solution:**
- Check your internet connection
- Verify your API key is valid
- Try resetting the chat session with `chatbot.reset_chat(user_id)`

#### Package Not Found Errors

**Solution:**
- Ensure all dependencies are installed: `pip install -r requirements.txt`
- Check Python version compatibility (3.7+ required)

---

## 👥 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgements

- [Google Gemini API](https://ai.google.dev/) for the underlying language model

---

<div align="center">
  <sub>Built with ❤️ for supporting mental wellbeing</sub>
</div>


