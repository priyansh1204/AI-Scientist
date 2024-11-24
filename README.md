# LLM Batch Response Tool

This repository provides a Python implementation for interacting with multiple LLM (Large Language Model) clients and models. It supports batch responses, various models, and error handling with backoff for rate limits and timeouts.

## Features

- **Multiple Model Support**: Easily interact with a variety of models, including OpenAI's GPT, Claude by Anthropic, and Meta's LLaMA.
- **Batch Response Handling**: Retrieve multiple responses in a single request for ensembling or other analysis purposes.
- **Error Handling**: Implements exponential backoff for handling API rate limits and timeouts.
- **Ollama Integration**: Supports the Ollama framework for local model hosting.
- **JSON Parsing**: Extract structured JSON from LLM outputs for easier downstream processing.

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/priyansh1204/AI-Scientist.git
   cd llm-batch-response-tool
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

### Basic Example

Use the `get_batch_responses_from_llm` function to fetch multiple responses from a specified model:

```python
from your_script_name import get_batch_responses_from_llm

response, history = get_batch_responses_from_llm(
    msg="What is the capital of France?",
    client=openai,
    model="gpt-4o-2024-05-13",
    system_message="You are an assistant that provides concise answers.",
    n_responses=3
)

print(response)
```

### Ollama Example

For models hosted locally via Ollama:

```python
from your_script_name import llm_json_auto_correct

result = llm_json_auto_correct(
    system_prompt="You are a JSON auto-corrector.",
    user_prompt='{"key": "value"'
)
print(result)
```

### JSON Parsing

Extract JSON objects embedded within LLM outputs:

```python
from your_script_name import extract_json_between_markers

json_content = extract_json_between_markers(output_from_llm)
print(json_content)
```

## Configuration

- Customize the models and their configurations by editing the `ollama_choices` and `allchoices` lists in the script.
- Set your API keys for OpenAI and other services as required.

## Dependencies

- `openai`: For OpenAI's GPT models.
- `backoff`: For handling retries with exponential backoff.
- `json`: For JSON handling in Python.

Install dependencies via `pip install -r requirements.txt`.

## Contributing

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-name`).
3. Commit your changes (`git commit -am 'Add feature'`).
4. Push to the branch (`git push origin feature-name`).
5. Create a pull request.

## License

This project is licensed under the [MIT License](LICENSE).
