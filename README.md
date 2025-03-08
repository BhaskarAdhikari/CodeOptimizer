CodeOptimizer using DeepSeek API

Overview
This Python project demonstrates how to build a chatbot named CodeOptimizer using the DeepSeek API, a customized version of OpenAI's API. The chatbot can help with code optimization by providing suggestions and fixes based on user input. It supports both standard and streaming responses for a more interactive experience.

Features
API Integration: Connects to DeepSeek's API using a custom base URL.
Streaming Responses: Provides real-time replies for a smooth chat experience.
Code Optimization Tips: Detects and suggests fixes for common code issues.
Conversation History: Maintains chat context across multiple user inputs.
Requirements
Python 3.12.7 or later
OpenAI Python library
Install the OpenAI library if you haven’t already:

bash
Copy
Edit
pip install openai
Setup
Obtain an API key from DeepSeek.
Set your API key as an environment variable:
bash
Copy
Edit
export DEEPSEEK_API_KEY='your_api_key_here'
Ensure the openai library is installed.
Usage
1. Getting a Standard Response
This part of the code sends a prompt to the deepseek-chat model and prints the response.

python
Copy
Edit
response = client.chat.completions.create(
    model="deepseek-chat",
    messages=[
        {"role": "system", "content": "You are a helpful assistant"},
        {"role": "user", "content": "Hello"},
    ],
    stream=False
)
print(response.choices[0].message.content)
Example Output:

css
Copy
Edit
Hello! How can I assist you today? 😊
2. Getting a Streaming Response
The stream_chat_response function sends a prompt to the deepseek-chat model and streams the response back in real-time.

python
Copy
Edit
stream_chat_response("Can you help me fix this Python code?")
Example Output:

rust
Copy
Edit
Bot: Sure! Please provide the code you'd like me to fix, and let me know what issues or errors you're encountering. I'll do my best to help!
3. Interactive Chat Mode
This section enables an interactive chat session:

python
Copy
Edit
if __name__ == "__main__":
    print("DeepSeek Chatbot - Type 'exit' to end the chat.")
    while True:
        user_input = input("You: ")
        if user_input.lower() == "exit":
            print("Goodbye!")
            break
        stream_chat_response(user_input)
To exit the chat, type:

bash
Copy
Edit
exit
4. Example: Code Optimization Suggestion
If you input:

kotlin
Copy
Edit
You: Can you review this code to check if a number is prime?
The chatbot might respond:

vbnet
Copy
Edit
Bot: The code has a few issues that need to be fixed:

1. The condition `if n + i == 0` is incorrect. It should check if `n` is divisible by `i` (i.e., `n % i == 0`).
2. The function should return a boolean (`True` or `False`) instead of a string for better usability.
3. The function should handle the case where `n` is 1, which is not a prime number.

Here’s the corrected code:

```python
def is_prime(n):
    if n <= 1:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True
markdown
Copy
Edit

## Customization
- **Temperature:** Controls creativity (0 to 1). Increase for more creative responses.
- **Max Tokens:** Adjusts the length of the response.
- **Model:** Change `"deepseek-chat"` to other models if needed.

## Error Handling
If an error occurs, the functions print an error message instead of crashing.

## Notes
- Make sure your API key is valid and has enough quota.
- Ensure that the base URL for DeepSeek's API is correct.

This project provides a solid base for building more complex chatbot applications. Feel free to modify and expand it as needed!




Search

