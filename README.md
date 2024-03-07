# LLM_Project

---

### 1. Dataset Overview: ViGGO

ViGGO is an English data-to-text generation dataset within the video game domain. It comprises more conversational target responses, constrained by the information in a meaning representation. With approximately 5,000 instances, ViGGO is a clean dataset ideal for assessing transfer learning, low-resource, or few-shot capabilities of neural models. In this project, ViGGO is employed for model training, validation, and evaluation of performance metrics.

---

---

### 2. Model Configuration with Quantization

The large language model is configured using Mistral's base model "Mistral-7B-v0.1" with BitsAndBytes quantization. 

---

---

### 3. Tokenizer Configuration

The tokenizer is initialized using the Mistral base model "Mistral-7B-v0.1" with specific configurations. The tokenization includes a maximum model length of 128 tokens, padding on the left side, and the addition of an end-of-sequence (EOS) token. 

---

---

### 4. Tokenization Functions

The code includes two essential functions for tokenization:

- **`tokenize(prompt)`**: Utilizes the configured tokenizer to process a given prompt. The function handles truncation, sets a maximum length of 128 tokens, and pads to the specified maximum length. Additionally, it creates a "labels" key in the result, copying the "input_ids" for model training.

- **`generate_and_tokenize_prompt(data_point)`**: Constructs a full prompt, incorporating the target sentence and meaning representation. This prompt is then tokenized using the previously defined `tokenize` function.

---

