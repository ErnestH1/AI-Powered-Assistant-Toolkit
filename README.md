# OpenAI API Notes

This readme provides instructions and examples for using the OpenAI API. It covers the installation process, configuration, and various usage scenarios. The readme includes information about the Chatbot and Orderbot as well.

## Installation

To use the OpenAI Python library, you need to install it using pip:

```bash
!pip install openai
```

## Configuration

Before using the library, you need to configure it with your OpenAI account's secret key, which is available on the OpenAI website. There are two ways to set the secret key:

1. Set it as the `OPENAI_API_KEY` environment variable:

```bash
!export OPENAI_API_KEY='sk-...'
```

2. Set `openai.api_key` to the secret key directly in your Python code:

```python
import openai
openai.api_key = "sk-..."
```

Additionally, if you prefer to store the secret key in a `.env` file, you can use the `dotenv` library:

```python
import os
from dotenv import load_dotenv, find_dotenv

_ = load_dotenv(find_dotenv())
openai.api_key = os.getenv('OPENAI_API_KEY')
```

## Usage

### Chatbot

You can interact with a chatbot using the OpenAI API. The following code demonstrates how to use the chatbot to generate responses:

```python
import openai

def get_completion(prompt, model="gpt-3.5-turbo"):
    messages = [{"role": "user", "content": prompt}]
    response = openai.ChatCompletion.create(
        model=model,
        messages=messages,
        temperature=0,  # Degree of randomness in the model's output
    )
    return response.choices[0].message["content"]

# Example usage
prompt = "Hello, how can I assist you today?"
response = get_completion(prompt)
print(response)
```

### Orderbot

The Orderbot is another useful application of the OpenAI API. It allows you to create an automated ordering system. Here's an example of how to use the Orderbot:

```python
import openai

def place_order(item, quantity):
    # Your code to place an order based on the provided item and quantity
    # ...

    # Return the order confirmation message
    return f"Order placed: {quantity} {item}(s)"

# Example usage
item = "blender"
quantity = 2
confirmation = place_order(item, quantity)
print(confirmation)
```

### Language Translation

The OpenAI API supports language translation. You can use the API to translate text between different languages. Here's an example:

```python
import openai

def translate_text(text, target_language):
    prompt = f"Translate the following text to {target_language}: ```{text}```"
    translation = get_completion(prompt)
    return translation

# Example usage
text = "Hi, I would like to order a blender"
target_language = "Spanish"
translation = translate_text(text, target_language)
print(translation)
```

### Tone Transformation

The OpenAI API allows you to transform the tone of text. You can convert text from informal or slang language to a more formal tone. Here's an example:

```python
import openai

def transform_tone(text):
    prompt = f"Translate the following from slang to a business letter: ```{text}```"
    transformed_text = get_completion(prompt)
    return transformed_text

# Example usage
text = "Dude, This is Joe, check out this spec on this standing lamp."
transformed_text = transform_tone(text)
print(transformed_text)
```

### Format Conversion

The OpenAI API also supports

 format conversion. You can use it to convert text between different formats, such as plain text to HTML or Markdown. Here's an example:

```python
import openai

def convert_format(text, target_format):
    prompt = f"Convert the following text to {target_format}: ```{text}```"
    converted_text = get_completion(prompt)
    return converted_text

# Example usage
text = "Hello, this is a simple text."
target_format = "Markdown"
converted_text = convert_format(text, target_format)
print(converted_text)
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

The project was developed by Ernest Hanson.