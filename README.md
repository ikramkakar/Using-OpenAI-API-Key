# Using OpenAI API Key in Google Colab

This repository demonstrates how to securely use your OpenAI API key in a Google Colab notebook to access and interact with OpenAI’s language models (such as GPT-4o). The project serves as a practical guide for integrating OpenAI’s Python library in a Colab environment and showcases a simple use case: generating a natural language response from a prompt.

---

## Why was this notebook developed?

- **Educational Purpose:** To show how you can safely provide your OpenAI API key when working within Colab, without exposing sensitive credentials in shared code.
- **Ease of Use:** Streamlines the process for developers, researchers, and students to quickly get started with OpenAI’s API in a cloud-based notebook.
- **Practical Demonstration:** Includes a working example where the notebook sends a message to the GPT-4o model and prints the AI’s reply.

---

## How the Code Works

1. **API Key Handling:**  
   The notebook uses `google.colab.userdata.get` to securely access the `OPENAI_API_KEY` stored in Colab’s Secrets. This means your key isn’t visible in the code and isn't accidentally shared.

2. **OpenAI Library:**  
   It employs OpenAI’s Python library to initialize a client and send a chat message to the GPT-4o model.

3. **Chat Completion Example:**  
   The provided snippet sends a prompt ("Explain recursion in one sentence.") and prints the model’s response.

---

## Steps & Instructions

### 1. Save Your OpenAI API Key in Colab

Before running the notebook, add your OpenAI API key as a secret in Google Colab:

- In the menu, go to:  
  `Runtime` > `Manage Secrets`
- Add a new secret:  
  Name: `OPENAI_API_KEY`  
  Value: Your OpenAI API key string

### 2. Run the Notebook

- Open the notebook:  
  [`Using_OpenAI_API_key_in_Colab.ipynb`](./Using_OpenAI_API_key_in_Colab.ipynb)
- Run the first cell to import libraries and fetch the API key using:
  
  ```python
  from openai import OpenAI
  from google.colab import userdata
  api_key = userdata.get('OPENAI_API_KEY')
  client = OpenAI(api_key=api_key)
  ```

- Run the next cell to send a conversational prompt:

  ```python
  response = client.chat.completions.create(
      model="gpt-4o",
      messages=[
          {"role": "system", "content": "You are a helpful assistant."},
          {"role": "user", "content": "Explain recursion in one sentence."}
      ],
      temperature=0.7
  )
  print(response.choices[0].message.content)
  ```

  The notebook will output the assistant's reply from the model.

---

## Requirements

- Google Colab account
- OpenAI Python package (`!pip install openai`)
- A valid OpenAI API key ([get yours here](https://platform.openai.com/account/api-keys))

---

## Notes

- Never share your API key in shared code or public repositories.
- You can modify the `messages` or `model` parameter to try different prompts or models supported by OpenAI.

---

## License

This project is for educational and demonstration purposes.
