# 🏥 Medical QLoRA Fine-Tuning + Dr. Deerfly AI Chat UI

A complete end-to-end medical AI project built with QLoRA fine-tuning, GGUF conversion, and a beautiful animated chat interface powered by Ollama.

---

## 📌 Project Overview

This project demonstrates:
- Fine-tuning a large language model on medical data using **QLoRA** (Quantized Low-Rank Adaptation)
- Converting the fine-tuned model to **GGUF format** for local deployment
- Running the model locally using **Ollama**
- A fully animated **Dr. Deerfly medical chat UI** connected to the local model

---

## 🗂️ Project Structure

```
Medical-QLoRA-DrDeerfly/
├── New_Medical_QLoRA.ipynb       ← Main QLoRA fine-tuning notebook
├── Medical_QLoRA_GGUF.ipynb      ← GGUF conversion notebook
├── dr_deerfly_ollama.html        ← Dr. Deerfly animated chat UI
└── README.md                     ← This file
```

---

## 🧠 Model Details

| Parameter | Value |
|-----------|-------|
| Base Model | TinyLlama / Phi-3-mini |
| Fine-tuning Method | QLoRA (4-bit quantization) |
| LoRA Rank | 8-16 |
| LoRA Alpha | 16-32 |
| Dataset | ChatDoctor-HealthCareMagic-100k |
| Training Samples | 300-500 |
| Epochs | 1 |
| Framework | Unsloth + HuggingFace |
| Output Format | LoRA Adapter + GGUF |

---

## 🚀 How to Run

### Step 1 — Fine-tune the model in Google Colab
1. Open `New_Medical_QLoRA.ipynb` in [Google Colab](https://colab.research.google.com)
2. Set Runtime → T4 GPU
3. Click Runtime → Run all
4. Allow Google Drive when asked
5. Wait 15-20 minutes for training to complete
6. Adapter saves automatically to Google Drive

### Step 2 — Convert to GGUF (for Ollama)
1. Open `Medical_QLoRA_GGUF.ipynb` in Google Colab
2. Run all cells
3. GGUF file downloads to your PC automatically

### Step 3 — Load into Ollama
1. Install [Ollama](https://ollama.ai)
2. Create a `Modelfile` in same folder as your `.gguf` file:
```
FROM ./medical_q4.gguf
SYSTEM """You are MedAssist, a medical AI assistant trained on real clinical data."""
PARAMETER temperature 0.7
PARAMETER num_ctx 2048
PARAMETER repeat_penalty 1.3
```
3. Run in Command Prompt:
```bash
ollama create medassist -f Modelfile
ollama run medassist
```

### Step 4 — Open Dr. Deerfly UI
1. Open Command Prompt and run:
```bash
set OLLAMA_ORIGINS=*
ollama serve
```
2. Open `dr_deerfly_ollama.html` in Chrome or Edge
3. Click **Check Connection**
4. Select your model from dropdown
5. Start chatting!

---

## 🦌 Dr. Deerfly UI Features

- 🫀 **Live ECG heartbeat** animation
- 🔬 **Animated medical tools** — stethoscope, microscope, syringe
- 🫁 **Detailed anatomical organs** pop up when you type a disease
- 7 diseases supported with full SVG anatomy:
  - Liver Disease (lobes, bile duct, gallbladder)
  - Heart Attack (4 chambers, valves, coronary artery)
  - Diabetes (pancreas with islets, kidney cross-section)
  - Kidney Failure (both kidneys with full cross-section)
  - Lung Infection (both lungs with bronchial tree)
  - Brain Tumor (cortex with gyri, sulci, 4 lobes)
  - Anemia (biconcave RBC, bone marrow)
- 💬 **Full conversation history** sent to model
- 🟢 **Live connection status** dot
- 📱 **Responsive design** works on all screen sizes

---

## 📊 Training Results

- Loss decreased consistently during training ✅
- Model learned medical Q&A conversation style ✅
- Adapter saved successfully to Google Drive ✅
- GGUF conversion completed successfully ✅

---

## 🛠️ Technologies Used

| Technology | Purpose |
|-----------|---------|
| Google Colab | Training environment (free T4 GPU) |
| Unsloth | Fast QLoRA fine-tuning |
| HuggingFace | Model and dataset hub |
| PEFT | LoRA adapter management |
| TRL | Supervised fine-tuning trainer |
| llama.cpp | GGUF conversion |
| Ollama | Local model deployment |
| HTML/CSS/JS | Dr. Deerfly chat UI |
| SVG | Anatomical organ illustrations |

---

## ⚠️ Disclaimer

This project is for **educational purposes only**. The AI model is not a substitute for professional medical advice. Always consult a licensed healthcare provider for medical decisions.

---

## 👨‍💻 About

Built as a university assignment demonstrating:
- Parameter-efficient fine-tuning (PEFT) with QLoRA
- Local LLM deployment with Ollama
- Interactive medical AI interface design

---

## 📝 License

MIT License — free to use and modify for educational purposes.
