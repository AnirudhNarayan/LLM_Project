# LLM_Project

---

### 1. Dataset Overview: ViGGO

ViGGO is an English data-to-text generation dataset in the video game domain, with target responses being more conversational than information-seeking, yet constrained to the information presented in a meaning representation. The dataset is relatively small with about 5,000 datasets but very clean, and can thus serve for evaluating transfer learning, low-resource, or few-shot capabilities of neural models.

---

---

### 2. Model Configuration with Quantization

The large language model is configured using Mistral's base model "Mistral-7B-v0.1" with BitsAndBytes quantization. 

---

---

### 3. Tokenizer Configuration

The tokenizer is initialized using the Mistral base model "Mistral-7B-v0.1" with specific configurations. The tokenization includes a maximum model length of 128 tokens, padding on the left side and the addition of an end-of-sequence (EOS) token. 

---

---

### 4. Tokenization Functions

The code includes two essential functions for tokenization:

- **`tokenize(prompt)`**: Utilizes the configured tokenizer to process a given prompt. The function handles truncation, sets a maximum length of 128 tokens, and pads to the specified maximum length. Additionally it creates a "labels" key in the result, copying the "input_ids" for model training.

- **`generate_and_tokenize_prompt(data_point)`**: Constructs a full prompt, incorporating the target sentence and meaning representation. This prompt is then tokenized using the previously defined `tokenize` function.

---

---

### 5. Model Evaluation

For model evaluation, the tokenizer is re-initialized to exclude padding and end-of-sequence (EOS) tokens. The evaluation prompt is then tokenized using the updated tokenizer. The model is set to evaluation mode, and the generated output is obtained with a maximum of 128 new tokens. The decoded result is printed, excluding special tokens.

---

---

### 6. Model Training Enhancement

To enhance model training, gradient checkpointing is enabled using the `model.gradient_checkpointing_enable()` method. Additionally, the model is prepared for knowledge bit (KBIT) training using the `prepare_model_for_kbit_training` function from the `peft` library. The `print_trainable_parameters` function is provided to display the number of trainable parameters, total parameters, and the percentage of trainable parameters in the model.

---

---

### 7. LORA Model Integration

The script incorporates the popular and lightweight training technique, LoRA (Low-Rank Adaptation of Large Language Models), to significantly reduce the number of trainable parameters. Configuration with `LoraConfig` and preparation for knowledge bit (KBIT) training are applied, along with an accelerator for improved compatibility.

---

---

### 8. Model Training

The script starts training the model using the Hugging Face Transformers library. The `Trainer` class is utilized with specified training and evaluation datasets. The training configuration includes warm-up steps, batch size, learning rate, and other relevant parameters. 

---

---

