# API Documentation: Using the `https://api.andyproject.de/v1/gpt3.5/` Endpoint

This documentation provides instructions on how to use the API endpoint available at `https://api.andyproject.de/v1/gpt3.5/`. The endpoint allows you to retrieve a list of models, generate images from text prompts, and get text completions using OpenAI's GPT-3.5 model.

## Endpoint URL

- Base URL: `https://api.andyproject.de/v1/gpt3.5/`

## Available Parameters

### 1. `models`
- **Description**: Fetches the available models from the OpenAI API.
- **Request Method**: GET
- **Example**: `https://api.andyproject.de/v1/gpt3.5/?models`

### 2. `image`
- **Description**: Generates images based on a provided text prompt.
- **Request Method**: GET
- **Required Parameters**:
  - `image` (string): The text prompt for image generation.
- **Example**: `https://api.andyproject.de/v1/gpt3.5/?image=your_prompt_here`

### 3. `prompt`
- **Description**: Generates text completions based on a provided prompt.
- **Request Method**: GET
- **Required Parameters**:
  - `prompt` (string): The text prompt for generating completions.
- **Example**: `https://api.andyproject.de/v1/gpt3.5/?prompt=your_prompt_here`

## Response Format

- The responses are in JSON format.

## Error Handling

- If a required parameter is missing, the response will contain an error message in JSON format.

## Example Python Script

Below is an example Python script to interact with the API endpoint:

```python
import requests

# Function to get available models
def get_models():
    url = "https://api.andyproject.de/v1/gpt3.5/?models"
    response = requests.get(url)
    if response.status_code == 200:
        return response.json()
    else:
        return {"error": "Failed to fetch models"}

# Function to generate an image
def generate_image(prompt):
    url = f"https://api.andyproject.de/v1/gpt3.5/?image={prompt}"
    response = requests.get(url)
    if response.status_code == 200:
        return response.json()
    else:
        return {"error": "Failed to generate image"}

# Function to get text completion
def get_completion(prompt):
    url = f"https://api.andyproject.de/v1/gpt3.5/?prompt={prompt}"
    response = requests.get(url)
    if response.status_code == 200:
        return response.json()
    else:
        return {"error": "Failed to get completion"}

# Example usage
if __name__ == "__main__":
    # Get models
    models = get_models()
    print("Models:", models)

    # Generate image
    image_prompt = "a beautiful landscape"
    image_response = generate_image(image_prompt)
    print("Image Response:", image_response)

    # Get text completion
    text_prompt = "Once upon a time"
    text_response = get_completion(text_prompt)
    print("Text Response:", text_response)
```

This Python script demonstrates how to use the API endpoint to retrieve models, generate images from prompts, and get text completions. Replace the placeholder text in the examples with your actual prompts to test the API.
