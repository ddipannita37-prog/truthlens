# TruthLens 🔍  
**See through the hype. One claim at a time.**

[![Live Demo](https://img.shields.io/badge/%F0%9F%94%97_Live_Demo-Try_Now-34bfba?style=for-the-badge&logo=googlecloud)](https://your-truthlens-agent-url-here.a.run.app)  
![LLM](https://img.shields.io/badge/LLM-Gemma_3_270M-34bfba?style=flat&logo=google)  
![Platform](https://img.shields.io/badge/Platform-Google_Cloud_Run-4285F4?style=flat&logo=googlecloud)  
![GPU](https://img.shields.io/badge/GPU-NVIDIA_L4-ff3b3b?style=flat&logo=nvidia)  
![Privacy](https://img.shields.io/badge/Privacy-No_Logs_%E2%9C%85-success)  
![Open Source](https://img.shields.io/badge/Open_Source-%E2%9D%A4-ff69b4)

> An AI-powered **bullsh*t detector** that instantly analyzes ads, emails, social posts, contracts, or any suspicious text — and gives you the truth in plain English.

## 🚨 The Problem
Every day we face:
- “90% OFF – Today Only!” flash sales
- Influencer posts that feel *too perfect*
- Terms & conditions written to confuse
- Urgent messages designed to trigger FOMO

Most people don’t have time to verify everything.  
So we either ignore our gut… or fall for it.

## 🛡 The Solution – TruthLens
Just paste any suspicious text → get an instant, unbiased report:

- **Truth Score** (0–100)  
- Detected red flags & manipulation tactics  
- Plain-English breakdown  
- Evidence-based reasoning  
- Verdict: **Safe • Be Cautious • Avoid**

100% open tools. No closed APIs. Full control.

## 🏗 Architecture (Production-Ready)

### Features
Real-time streaming responses
Beautiful built-in chat interface (powered by ADK)
Custom truth-seeking system prompt for maximum neutrality
Handles 50+ concurrent users effortlessly
Zero data logging — your privacy is fully protected
Completely self-hostable & open source

### Tech Stack
Model: Gemma-3-270M (via Ollama)
Framework: Google Agent Development Kit (ADK)
API: FastAPI + Uvicorn
Inference: Ollama on Cloud Run + NVIDIA L4 GPU
Frontend: ADK Web UI
Deploy: Google Cloud Run (2nd generation)

Repository Structure
truthlens/
├── ollama-backend/          # GPU inference service
│   └── Dockerfile
├── adk-agent/               # Agent + web UI
│   ├── production_agent/
│   │   └── agent.py         # ← TruthLens core logic & prompt
│   ├── server.py
│   ├── Dockerfile
│   └── elasticity_test.py
└── README.md

Deployment Steps
# 1. Clone the repo
git clone https://github.com/ddipannita37-prog/truthlens.git
cd truthlens

# 2. Deploy Ollama + Gemma (GPU backend)
cd ollama-backend
gcloud run deploy truthlens-ollama \
  --source . --region europe-west1 \
  --gpu 1 --gpu-type nvidia-l4 --cpu 8 --memory 16Gi \
  --max-instances 1 --port 11434 --allow-unauthenticated

export OLLAMA_URL=$(gcloud run services describe truthlens-ollama --region europe-west1 --format='value(status.url)')

# 3. Deploy TruthLens Agent (frontend + logic)
cd ../adk-agent
gcloud run deploy truthlens-agent \
  --source . --region europe-west1 \
  --cpu 2 --memory 4Gi \
  --set-env-vars OLLAMA_API_BASE=$OLLAMA_URL \
  --allow-unauthenticated

echo "🚀 TruthLens is live at:"
gcloud run services describe truthlens-agent --region europe-west1 --format='value(status.url)'


    A[👤 You<br/>Web Chat UI] --> B[TruthLens Agent<br/>Cloud Run - CPU<br/>FastAPI + ADK]
    B --> C[Ollama Server<br/>Gemma-3-270M<br/>Cloud Run - NVIDIA L4 GPU]
    C --> B
    B --> A[Streaming Response<br/>Truth Score + Analysis]
