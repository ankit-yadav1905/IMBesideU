# 🧠 AI Agent for Academic PDF Summarization and Question Generation

### Developed by: **Yadav Ankit Shivsurat**  
**Roll No :** 231181  
**Department:** Chemical Engineering  
**University:** Indian Institute of Technology Kanpur  

---

## 📘 Project Overview
This project presents an **AI agent** designed to assist students in last-minute academic revision.  
It automatically **summarizes educational PDFs** and **generates theoretical questions**, helping learners review key concepts efficiently.

The agent follows a **Planner–Executor architecture** built on top of a **fine-tuned `google/gemma-2-2b` model** using **QLoRA** for parameter-efficient tuning.  
Outputs are formatted into **LaTeX-rendered PDFs** for clean and professional readability.

---

## ⚙️ Features

- 📄 **PDF Understanding** – Extracts and processes text from academic PDFs.  
- 🧩 **Planner–Executor Framework** – Planner defines tasks; Executor performs summarization and formatting.  
- 🧠 **Fine-Tuned LLM (Gemma-2-2b)** – Trained using QLoRA for summarization and question generation.  
- 🔍 **Gemini API Dataset Generation** – Created a custom dataset via automated text summarization and question creation.  
- 🧾 **LaTeX-Based Output** – Converts generated content into a high-quality revision PDF.  
- ☁️ **Hugging Face Deployment** – The fine-tuned model is hosted on Hugging Face for scalable API access.

---

## 🏗️ Architecture Overview

### **Core Components**
| Component | Function |
|------------|-----------|
| **Planner** | Interprets user goal, decomposes tasks (extract, summarize, format). |
| **Executor** | Performs text extraction, model inference, and LaTeX PDF creation. |
| **Model** | Fine-tuned `google/gemma-2-2b` (via QLoRA) hosted on Hugging Face. |
| **Interface Layer** | Simple upload-and-generate interface for users. |

### **Interaction Flow**
1. User uploads a PDF.  
2. Planner defines the workflow and task order.  
3. Executor extracts text, invokes the fine-tuned model, and formats the output.  
4. Final summarized + question-based revision PDF is generated.

---

## 🎯 Model Details

- **Base Model:** `google/gemma-2-2b`  
- **Fine-tuning Technique:** QLoRA (4-bit quantization with LoRA adapters)  
- **Frameworks Used:** `transformers`, `peft`, `bitsandbytes`, `torch`  
- **Training Objective:** Summarization + Question Generation  
- **Dataset Source:** Custom-built using Gemini API outputs on scraped academic PDFs  

---

## 📊 Evaluation

### **Qualitative Results**
- Summaries were concise, coherent, and preserved the original meaning.
- Generated questions were conceptually aligned with text.
- LaTeX formatting improved clarity and academic presentation.

---

## 🚀 Deployment

The fine-tuned model is deployed on **Hugging Face Hub**, enabling:
- Public API access for inference.  
- Easy integration into other platforms or agents.  
- Continuous improvement via model versioning.

Example usage:
```python
from transformers import AutoTokenizer, AutoModelForCausalLM

tokenizer = AutoTokenizer.from_pretrained("ankityadav06/gemma-study-agent")
model = AutoModelForCausalLM.from_pretrained("ankityadav06/gemma-study-agent")

prompt = "Summarize the following academic text..."
inputs = tokenizer(prompt, return_tensors="pt")
outputs = model.generate(**inputs, max_new_tokens=400)
print(tokenizer.decode(outputs[0], skip_special_tokens=True))
```

Chat Logs: <https://chatgpt.com/c/68078c16-3d04-8004-8e29-0fcda16f8c50>
