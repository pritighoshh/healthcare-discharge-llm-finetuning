# 🏥 Clinical-to-Patient Discharge Instruction Generator  
*Fine-Tuning FLAN-T5 with LoRA for Patient-Friendly Medical Communication*
**👨‍💻 Author:** Priti Pradeep Ghosh 
**📘 Course:** Advanced NLP / LLM Fine-Tuning  
**📅 Date:** February 2026 

---

## 📌 Project Overview

This project fine-tunes a pre-trained sequence-to-sequence language model to transform **clinical hospital course notes** into **clear, patient-friendly discharge instructions**.

Clinical documentation is often written for healthcare professionals and can be difficult for patients to understand. The goal of this project is to bridge that gap by generating discharge instructions that are:
- Easy to read
- Reassuring in tone
- Focused on actionable next steps

To achieve this, we apply **parameter-efficient fine-tuning (LoRA)** on top of a **FLAN-T5** base model using a real-world clinical dataset.

---

## 🧠 Key Objectives

- Adapt a general-purpose language model to the healthcare domain
- Improve clarity and accessibility of discharge instructions
- Compare baseline vs fine-tuned model performance
- Demonstrate practical deployment via an interactive interface

---

## 📂 Dataset

**Dataset:** DischargeSum – Discharge Target  
**Source:** Hugging Face Datasets  
**Task:** Clinical summarization (hospital course → discharge instructions)

### Dataset Structure
- **Input:** Brief hospital course (clinical narrative)
- **Target:** Discharge instructions written for patients
- **Splits:** Train / Validation / Test (predefined)

The dataset contains tens of thousands of real clinical notes, making it suitable for domain-specific fine-tuning.

---

## 🏗️ Model Architecture

- **Base Model:** `google/flan-t5-base`
- **Task Type:** Sequence-to-sequence text generation
- **Fine-Tuning Method:** LoRA (Low-Rank Adaptation)

### Why FLAN-T5?
- Instruction-tuned and well-suited for summarization
- Efficient and stable for medium-length medical text
- Strong performance with limited fine-tuning data

### Why LoRA?
- Trains <1% of model parameters
- Faster training and lower memory usage
- Ideal for experimentation and deployment constraints

---

## ⚙️ Training Strategy

We evaluated **three different fine-tuning configurations** to study the impact of learning rate and training duration:

| Run | Learning Rate | Epochs | Purpose |
|----|--------------|--------|--------|
| Run A | 3e-4 | 1 | Fast adaptation baseline |
| Run B | 1e-4 | 1 | Lower learning rate test |
| Run C | 1e-4 | 2 | Extended training |

The best-performing model (Run A) was selected based on ROUGE metrics and efficiency.

---

## 📊 Evaluation Metrics

Because this is a **text generation task**, classification metrics such as accuracy and F1-score are not applicable.

We evaluate performance using **ROUGE metrics**, which measure content overlap between generated text and reference instructions:

- ROUGE-1
- ROUGE-2
- ROUGE-L
- ROUGE-Lsum

---

## 📈 Results Summary

### Baseline vs Fine-Tuned (Test Subset)

| Metric | Baseline | Fine-Tuned (Run A) | Improvement |
|------|----------|-------------------|-------------|
| ROUGE-1 | ~0.09 | ~0.31 | +0.22 |
| ROUGE-2 | ~0.01 | ~0.11 | +0.09 |
| ROUGE-L | ~0.06 | ~0.23 | +0.16 |

The fine-tuned model shows **substantial improvement** across all metrics, demonstrating effective domain adaptation.

---

## 🔍 Error Analysis

Qualitative analysis of poor-performing examples revealed common challenges:
- Overly brief summaries missing follow-up details
- Occasional over-generalization of advice
- Length imbalance between generated and reference text

These insights suggest future improvements through stricter decoding constraints and enhanced instruction prompts.

---

## 🚀 Inference & Deployment

The project includes:
- A reusable Python inference function
- An interactive **Gradio web interface** for live demonstrations

Users can paste a clinical hospital course note and instantly receive patient-friendly discharge instructions.

> ⚠️ This demo is for educational purposes only and does not provide medical advice.

---

## 🧪 Tools & Libraries

- Hugging Face Transformers
- Hugging Face Datasets
- PEFT (LoRA)
- PyTorch
- ROUGE
- Gradio
- TensorBoard

---

## 📌 Conclusion

This project demonstrates how targeted fine-tuning of large language models can significantly improve the accessibility of clinical information for patients. By combining instruction-tuned models with parameter-efficient adaptation techniques, we achieve strong performance gains while maintaining training efficiency.

The approach highlights a practical pathway for deploying language models in healthcare communication workflows, with careful consideration of safety, clarity, and usability.

---

## 📚 References

- Raffel et al., *Exploring the Limits of Transfer Learning with T5*
- Hu et al., *LoRA: Low-Rank Adaptation of Large Language Models*
- Hugging Face Transformers & PEFT Documentation
- DischargeSum Dataset (Hugging Face)
- ROUGE Evaluation Metric
- Gradio Documentation
- YouTube: Fine-Tuning Large Language Models – Practical Walkthrough

---

## 📄 License

This project is released for educational and research purposes only.  
All datasets and models are subject to their respective licenses.  
Generated content should not be used for clinical decision-making.
