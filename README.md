# 🩺 Medical LLM Fine-Tuning with QLoRA & Unsloth

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1NEdIVI--Zl-dxjoqAZ1zlu78xKrTX0B3?usp=sharing)

This project fine-tunes **Llama 3.2 3B Instruct** for medical question answering using **4-bit QLoRA and Unsloth** on Google Colab.

It was completed as **Month 1 – Task 2** of my Generative AI Internship at **Arch Technologies**.

---

## 🎯 Project Objective

The objective was to adapt a pretrained large language model to the medical question-answering domain while keeping computational requirements manageable through parameter-efficient fine-tuning.

Instead of updating the entire model, lightweight LoRA adapters were trained on top of a 4-bit quantized Llama model.

---

## 📊 Dataset

The project uses the **MedQuAD medical question-answering dataset**.

### Dataset preparation

- Raw examples: **16,407**
- After duplicate removal: **16,359**
- After 1,024-token filtering: **15,914**
- Training examples: **4,800**
- Validation examples: **600**
- Held-out test examples: **600**

The dataset was checked for:

- Missing values
- Duplicate question-answer pairs
- Question-type distribution
- Question and answer lengths
- Token-length limits

---

## ⚙️ Fine-Tuning Configuration

| Parameter | Setting |
|---|---|
| Base Model | Llama 3.2 3B Instruct |
| Quantization | 4-bit |
| Fine-Tuning Method | QLoRA / LoRA |
| LoRA Rank | 16 |
| LoRA Alpha | 16 |
| Trainable Parameters | 24,313,856 |
| Trainable Share | 0.7511% |
| Training Examples | 4,800 |
| Validation Examples | 600 |
| Epochs | 1 |
| Sequence Length | 1,024 tokens |
| Effective Batch Size | 8 |
| Learning Rate | 2e-4 |
| Training Steps | 600 |

---

## 📈 Final Results

Validation loss decreased throughout training.

| Metric | Result |
|---|---|
| Final Validation Loss | **1.1511** |
| Held-Out Test Loss | **1.1253** |
| Held-Out Test Perplexity | **3.0813** |
| Held-Out Test Examples | **600** |

Only approximately **0.75% of the model parameters** were trained, demonstrating the efficiency of parameter-efficient fine-tuning.

---

## 🔄 Workflow

1. Configure Google Colab GPU
2. Load the 4-bit Llama 3.2 3B Instruct model
3. Load and inspect the MedQuAD dataset
4. Remove duplicate examples
5. Analyze token lengths
6. Prepare train, validation, and held-out test sets
7. Configure LoRA adapters
8. Fine-tune using Unsloth and TRL
9. Monitor training and validation loss
10. Save the trained LoRA adapter
11. Compare base and fine-tuned responses
12. Evaluate on unseen test examples

---

## 🛠️ Technologies Used

- Python
- Google Colab
- PyTorch
- Hugging Face Transformers
- Hugging Face Datasets
- Unsloth
- TRL
- PEFT / LoRA
- QLoRA
- Llama 3.2 3B Instruct
- MedQuAD

---

## 📓 Notebook

The complete organized notebook can be opened directly in Google Colab:

**[Open Medical QLoRA Fine-Tuning Notebook](https://colab.research.google.com/drive/1NEdIVI--Zl-dxjoqAZ1zlu78xKrTX0B3?usp=sharing)**

---

## ⚠️ Medical Disclaimer

This project was developed for **educational and research purposes only**.

The model has not been clinically validated and must not be used for medical diagnosis, treatment decisions, or as a replacement for professional healthcare advice.

---

## 👩‍💻 Author

**Kaunain Gul Khalid**  
BS Artificial Intelligence  
University of Malakand
