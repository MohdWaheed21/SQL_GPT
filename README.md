
# 🦙 Fine-Tuned LLaMA 3.2 on SQL Data (Unsloth + Ollama Integration)

This repository contains the code and setup instructions for running a fine-tuned LLaMA 3.2 model on SQL-related data. The model is fine-tuned using Unsloth + LoRA and integrated with Ollama for local inference.

## 🔥 Highlights

- Trained on SQL query generation data using [Unsloth](https://github.com/unslothai/unsloth) with LoRA
- Supports easy local inference with [Ollama](https://ollama.com)
- Training notebook included for reproducibility
- Model weights available via Google Drive

---

## 🚀 How to Run the Model with Ollama

### 1. Clone this repository

```bash
git clone https://github.com/MohdWaheed21/SQL_GPT
cd SQL_GPT
```

### 2. Download the model weights

- Download the model archive from the following link:  
  🔗 [Download model.zip](https://drive.google.com/file/d/1t_-ikw1VrYRvo0driv0eZmrL777QGsPU/view)

- Place the `model.zip` inside the cloned repo folder.

### 3. Extract the model

```bash
unzip model.zip
```

This will extract files like `config.json`, `tokenizer.json`, and `unsloth.Q4_K_M.gguf` necessary tokenizer files into the current directory.

### 4. Add the Ollama `Modelfile`

Ensure there's a `Modelfile` (provided in this repo or copy from `ollama/Modelfile`) in the same directory where you extracted the model files.

Example contents of `Modelfile`:
```
FROM llama3
PARAMETER adapter_path=./
```

### 5. Create and Run Your Ollama Model

```bash
ollama create SQL_GPT -f Modelfile
ollama run SQL_GPT
```

You're now running a local LLaMA 3.2 model fine-tuned on SQL queries!

---

## 📓 Want to Train It Yourself?

The entire training pipeline is available in this repo.

➡️ Open and run [`SQL_GPT.ipynb`](SQL_GPT.ipynb) to reproduce the fine-tuning using Unsloth on Colab with a T4 GPU.

---

## 🧠 Example Prompt

```
Input:
"Write a SQL query to find users with more than 3 failed login attempts in the past week."

Output:
SELECT * FROM logins WHERE status = 'failed' AND attempt_count > 3 AND login_date >= DATE_SUB(CURDATE(), INTERVAL 7 DAY);
```

---

## 👥 Collaborators

- Vighneshwar Kuru (https://github.com/vighneshwarkuru)  
- Mohd Waheed (https://github.com/mohhdwaheed21)

---

## 📄 License

This project is open-sourced under the MIT License.
