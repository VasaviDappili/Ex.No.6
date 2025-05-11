## Ex.No.6 Development of Python Code Compatible with Multiple AI Tools
## Develop By  : DAPPILI VASAVI
## Register no : 212223040030

## Aim 
Write and implement Python code that integrates with multiple AI tools to automate the task of interacting with APIs, comparing outputs, and generating actionable insights with Multiple AI Tools.
## 🔍 AI Tools Required:
ChatGPT (OpenAI)

Claude (Anthropic)

Gemini (Google)


## Explanation:
Experiment the persona pattern as a programmer for any specific applications related with your interesting area. Generate the outoput using more than one AI tool and based on the code generation analyse and discussing that.

## ⚙️ Use Case
Mental Health Assessment System: An AI-powered assistant for preliminary evaluation of psychological symptoms (e.g., anxiety, depression, sleep disorders). It collects symptom information and offers probable conditions and action steps for further consultation.


## 📌 Algorithm Overview
## Step-by-Step Workflow
## 1. Set Up API Integrations
Configure API keys and setup for ChatGPT, Claude, and Gemini using Python.

## 2. Input Mental Health Query
Provide structured inputs: emotional state, sleep pattern, social activity level, mood swings.

## 3. Prompt Variants

Standard Prompt: Plain text question

Survey Format Prompt: Questionnaire-style

Incomplete Sentence Prompt: Gap-fill prompt for prediction

## 4. Send Prompts to Each AI Tool

## 5. Receive & Parse AI Responses

## 6. Evaluate Responses
Compare for empathy, diagnostic accuracy, language clarity, and suggested actionability.

## 7. Generate Insights

## 8. Display Final Report

## 🧪 Prompt Types
## 1. Standard Prompt
## Prompt:
"Patient reports persistent sadness, loss of interest in daily activities, and insomnia. What mental health condition might this indicate, and what are the next steps?"

| **AI Tool** | **Response**                                                                                     |
| ----------- | ------------------------------------------------------------------------------------------------ |
| **ChatGPT** | Likely depression; suggest therapy and sleep hygiene practices.                                  |
| **Claude**  | Suggests Major Depressive Disorder; recommends clinical diagnosis, CBT, and possible medication. |
| **Gemini**  | Could be clinical depression; advises mental health evaluation and journaling exercise.          |

## 2. Survey Format Prompt
## Prompt (Questionnaire style):

![image](https://github.com/user-attachments/assets/91b29810-4923-4cbf-944f-46626bb990d5)

Query: Based on this profile, provide the possible condition and next steps.
| **AI Tool** | **Response**                                                                     |
| ----------- | -------------------------------------------------------------------------------- |
| **ChatGPT** | Indicative of depression; recommends visiting a psychologist.                    |
| **Claude**  | Strong symptoms of depressive disorder; suggests a diagnostic interview and CBT. |
| **Gemini**  | May point to mood disorder; suggests digital therapy apps and self-care tips.    |

## 3. Incomplete Sentence Prompt
## Prompt:
"A person showing signs of anxiety and restlessness is likely suffering from ______."
| **AI Tool** | **Response**                          |
| ----------- | ------------------------------------- |
| **ChatGPT** | Generalized Anxiety Disorder          |
| **Claude**  | Anxiety disorder                      |
| **Gemini**  | Generalized anxiety or panic disorder |

## 💻 Python Code:
```
import openai
import requests

# API keys (replace with actual keys)
CHATGPT_API_KEY = "your_openai_key"
CLAUDE_API_KEY = "your_claude_key"
GEMINI_API_KEY = "your_gemini_key"

openai.api_key = CHATGPT_API_KEY

def get_chatgpt_response(prompt):
    response = openai.Completion.create(
        model="gpt-4",
        prompt=prompt,
        max_tokens=150
    )
    return response.choices[0].text.strip()

def get_claude_response(prompt):
    headers = {
        'Authorization': f'Bearer {CLAUDE_API_KEY}',
        'Content-Type': 'application/json'
    }
    payload = {'prompt': prompt}
    url = 'https://api.claude.ai/v1/complete'
    response = requests.post(url, json=payload, headers=headers)
    return response.json().get('completion', '')

def get_gemini_response(prompt):
    headers = {
        'Authorization': f'Bearer {GEMINI_API_KEY}',
        'Content-Type': 'application/json'
    }
    payload = {'prompt': prompt}
    url = 'https://api.gemini.ai/v1/generate'
    response = requests.post(url, json=payload, headers=headers)
    return response.json().get('text', '')

# Sample input
query = "Patient reports persistent sadness, loss of interest in daily activities, and insomnia. What mental health condition might this indicate, and what are the next steps?"

# Execute all APIs
chatgpt = get_chatgpt_response(query)
claude = get_claude_response(query)
gemini = get_gemini_response(query)

# Display responses
print("ChatGPT Response:\n", chatgpt)
print("\nClaude Response:\n", claude)
print("\nGemini Response:\n", gemini)
```

## 📊 Evaluation
```
import pandas as pd

data = {
    "AI Tool": ["ChatGPT", "Claude", "Gemini"],
    "Accuracy": ["High", "High", "Moderate"],
    "Empathy": ["High", "High", "Moderate"],
    "Clarity": ["Very Clear", "Detailed", "Concise"],
    "Practicality": ["Useful", "Clinical", "Light Suggestions"]
}

df = pd.DataFrame(data)
print(df)

```
| AI Tool | Accuracy | Empathy  | Clarity    | Practicality      |
| ------- | -------- | -------- | ---------- | ----------------- |
| ChatGPT | High     | High     | Very Clear | Useful            |
| Claude  | High     | High     | Detailed   | Clinical          |
| Gemini  | Moderate | Moderate | Concise    | Light Suggestions |

## 📌 Conclusion:
This experiment demonstrates an AI-assisted diagnostic framework for mental health use cases. The integration with multiple AI tools showcases how prompt structuring and platform selection can affect diagnosis quality. ChatGPT proved effective in empathy and clarity, while Claude offered detailed clinical guidance. Gemini performed well in concise delivery.

## Result: 
The corresponding Prompt is executed successfully.

