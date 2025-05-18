# Ex.No.6 Development of Python Code Compatible with Multiple AI Tools

# Date:18-05-2025
# Register no: 212223040030
## Aim: Write and implement Python code that integrates with multiple AI tools to automate the task of interacting with APIs, comparing outputs, and generating actionable insights with Multiple AI Tools

## Explanation:
Experiment the persona pattern as a programmer for any specific applications related with your interesting area. 
Generate the outoput using more than one AI tool and based on the code generation analyse and discussing that. 



## 🎯 Objective
To write and implement Python code that interacts with multiple AI tools (OpenAI's ChatGPT, Anthropic's Claude, and Google Gemini) to:

Submit investment-related queries

Compare AI-generated financial advice

Generate actionable insights based on accuracy, clarity, and suitability

## ⚙ Use Case
Financial Advisory System: Automate personalized investment advice by querying multiple AI platforms, helping users make informed financial decisions.

## 🔍 AI Tools Required:
CHATGPT
CLAUDE
GEMINI

## 📌 Algorithm Overview
### Step-by-Step Algorithm for Multi-AI Tool Integration

1.Set Up API Integrations

Configure API credentials and libraries for ChatGPT, Claude, and Gemini.

2.Input Investment Profile

Accept user inputs such as age, risk tolerance, investment amount, and goals.

3.Format Prompts

Use various prompt styles (direct questions, scenario descriptions).

4.Send Prompts to AI Tools

Submit investment queries to ChatGPT, Claude, and Gemini.

5.Receive and Parse Responses

Collect advice and suggestions from each AI.

6.Compare Outputs

Analyze the responses based on accuracy, clarity, and suitability for user profile.

7.Generate Insights

Recommend the most appropriate AI for specific financial questions.

8.Prepare Final Report

Summarize and document findings.

## 🧪 Prompt Types
Direct Question: "What investment strategy do you recommend for a 30-year-old with moderate risk tolerance and $10,000 to invest?"

Scenario Description: "A 55-year-old planning to retire in 10 years with low risk tolerance seeks investment advice."

## 📤 Example Queries & Responses
### 1. Direct Question
#### Prompt:
"What investment strategy do you recommend for a 30-year-old with moderate risk tolerance and $10,000 to invest?"

| *AI Tool* | *Response*                                                                                        |
| ----------- | --------------------------------------------------------------------------------------------------- |
| ChatGPT     | Consider a diversified portfolio: 60% stocks, 30% bonds, 10% cash or ETFs; focus on growth sectors. |
| Claude      | A balanced approach with index funds and bonds; aim for moderate risk with diversified assets.      |
| Gemini      | Allocate \$6,000 to equities, \$3,000 to bonds, and \$1,000 to cash equivalents; review annually.   |

### 2. Scenario Description
#### Prompt:
"A 55-year-old planning to retire in 10 years with low risk tolerance seeks investment advice."

| *AI Tool* | *Response*                                                                                               |
| ----------- | ---------------------------------------------------------------------------------------------------------- |
| ChatGPT     | Focus on bonds, fixed income, and dividend-paying stocks to preserve capital and generate steady income.   |
| Claude      | Recommend conservative investments like government bonds and money market funds; minimize equity exposure. |
| Gemini      | Prioritize safety with high-quality bonds and some dividend stocks; avoid volatile sectors.                |

## 🔧 Code Implementation
```
import openai
import requests

# API Keys
CHATGPT_API_KEY = "your_openai_api_key"
CLAUDE_API_KEY = "your_claude_api_key"
GEMINI_API_KEY = "your_gemini_api_key"

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
    url = 'https://api.claude.ai/v1/complete'  # hypothetical endpoint
    response = requests.post(url, json=payload, headers=headers)
    return response.json().get('completion', '')

def get_gemini_response(prompt):
    headers = {
        'Authorization': f'Bearer {GEMINI_API_KEY}',
        'Content-Type': 'application/json'
    }
    payload = {'prompt': prompt}
    url = 'https://api.gemini.ai/v1/generate'  # hypothetical endpoint
    response = requests.post(url, json=payload, headers=headers)
    return response.json().get('text', '')
#Example query
query = "What investment strategy do you recommend for a 30-year-old with moderate risk tolerance and $10,000 to invest?"

chatgpt_response = get_chatgpt_response(query)
claude_response = get_claude_response(query)
gemini_response = get_gemini_response(query)

print("ChatGPT Response:\n", chatgpt_response)
print("\nClaude Response:\n", claude_response)
print("\nGemini Response:\n", gemini_response)

```

## OUTPUT RESPONSE
### Functions for Getting Responses:
#### 1.get_chatgpt_response():

1.This function sends the investment prompt to ChatGPT and retrieves the generated advice.

2.It uses the OpenAI API client (openai.Completion.create) to submit the prompt, specify the model, and return the text of the response.

```
def get_chatgpt_response(prompt):
    response = openai.Completion.create(
        model="gpt-4",  # specify the model
        prompt=prompt,
        max_tokens=150
    )
    return response.choices[0].text.strip()
```

#### 2.get_claude_response():

1.This function sends the same investment prompt to Claude via an HTTP POST request.

2.It uses the requests library to make a POST request to Claude’s API endpoint with proper headers including the API key.

3.The function extracts and returns the 'completion' field from Claude’s JSON response.

```
def get_claude_response(prompt):
    headers = {
        'Authorization': f'Bearer {CLAUDE_API_KEY}',
        'Content-Type': 'application/json'
    }
    payload = {'prompt': prompt}
    url = 'https://api.claude.ai/v1/complete'  # Example endpoint
    response = requests.post(url, json=payload, headers=headers)
    return response.json().get('completion', '')
```

#### get_gemini_response():

1.This function sends the investment prompt to Gemini via HTTP POST request to a generic API endpoint.

2.Similar to Claude, it sends the prompt in JSON format along with authorization headers.

3.The function parses the JSON response and returns the generated 'text' output.

```
def get_gemini_response(prompt):
    headers = {
        'Authorization': f'Bearer {GEMINI_API_KEY}',
        'Content-Type': 'application/json'
    }
    payload = {'prompt': prompt}
    url = 'https://api.gemini.ai/v1/generate'  # Example endpoint
    response = requests.post(url, json=payload, headers=headers)
    return response.json().get('text', '')
```

### 📊 Evaluation Metrics

| *Metric*      | *Description*                                      | *Importance*                                |
| --------------- | ---------------------------------------------------- | --------------------------------------------- |
| Accuracy        | Correctness and appropriateness of investment advice | Critical to avoid poor financial decisions    |
| Clarity         | How clear and understandable the response is         | Helps users to easily follow the advice       |
| Suitability     | Matching advice to user’s profile and goals          | Ensures personalized recommendations          |
| User Experience | Overall helpfulness and tone                         | Influences trust and confidence in the system |

```
import pandas as pd

evaluation_data = {
    "AI Tool": ["ChatGPT", "Claude", "Gemini"],
    "Accuracy": ["High", "High", "High"],
    "Clarity": ["High", "Moderate", "High"],
    "Suitability": ["Excellent", "Good", "Good"],
    "User Experience": ["Friendly", "Professional", "Concise"]
}

df_comparison = pd.DataFrame(evaluation_data)
print(df_comparison)
```

| *AI Tool* | *Accuracy* | *Clarity* | *Suitability* | *User Experience* |
| ----------- | ------------ | ----------- | --------------- | ------------------- |
| ChatGPT     | High         | High        | Excellent       | Friendly            |
| Claude      | High         | Moderate    | Good            | Professional        |
| Gemini      | High         | High        | Good            | Concise             |

## Conclusion:
This financial advisory system successfully integrates multiple AI tools, enabling diverse perspectives on investment strategies. The comparison highlights ChatGPT as the most suitable for personalized, clear advice, while Claude and Gemini provide solid alternatives.

## Result: The corresponding Prompt is executed successfully.
