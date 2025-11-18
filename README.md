# TruthLens 🔍  
**See through the hype. One claim at a time.**

[![TruthLens Demo]
![Built with Gemma](https://img.shields.io/badge/LLM-Gemma%202B%20/%207B-34bfba)  
![Deployed on Cloud Run](https://img.shields.io/badge/Deploy-Google%20Cloud%20Run-4285F4?logo=googlecloud)  
![GPU Accelerated](https://img.shields.io/badge/GPU-NVIDIA%20L4-ff3b3b)

## 🚨 The Problem
Every day we’re bombarded with:
- “90% OFF – Today Only!” ads  
- Influencer promotions that sound suspiciously perfect  
- Terms & conditions written like legal mazes  
- Messages that trigger FOMO or urgency  

Most of us don’t have time (or energy) to fact-check every claim — so we either ignore our gut or fall for it.

## 🛡 The Solution – TruthLens
TruthLens is an AI-powered “bullsh*t detector” that instantly analyzes any text you throw at it (ads, emails, social media posts, contracts, etc.) and returns a clear, unbiased breakdown:

- **Truth Score** (0–100)  
- Red flags & manipulative tactics used  
- Simplified plain-English explanation  
- Evidence-based reasoning  
- Recommendations (safe / cautious / avoid)

Built entirely on open-source & Google Cloud tools — no black-box APIs.

## 🏗 Architecture Overview


## 📁 Starter Structure

```
accelerate-ai-lab3-starter/
├── README.md                    # This file
├── ollama-backend/              # Ollama backend (separate deployment)
│   └── Dockerfile               # Backend container (TODO: implement)
└── adk-agent/                   # ADK agent (separate deployment)
    ├── pyproject.toml           # Python dependencies (complete)
    ├── env.template             # Environment template (complete)
    ├── server.py                # FastAPI server (TODO: implement)
    ├── Dockerfile               # Container config (TODO: implement)
    ├── elasticity_test.py       # Elasticity testing (TODO: implement)
    └── production_agent/        # Agent implementation
        ├── __init__.py          # Package init (complete)
        └── agent.py             # Agent logic (TODO: implement)
```

## 🎯 Files to Complete

You'll need to implement the following files by following the codelab instructions:

**Ollama Backend:**

- 🚧 `ollama-backend/Dockerfile` - Ollama container

**ADK Agent:**

- ✅ `adk-agent/pyproject.toml` - Dependencies (already complete)
- ✅ `adk-agent/env.template` - Environment template (already complete)
- 🚧 `adk-agent/production_agent/agent.py` - ADK agent implementation
- 🚧 `adk-agent/server.py` - FastAPI server with endpoints
- 🚧 `adk-agent/Dockerfile` - Container configuration
- 🚧 `adk-agent/elasticity_test.py` - Elasticity testing script

## 📚 Getting Started

1. Follow the codelab instructions to implement each TODO section
2. Copy and paste the provided code snippets
3. Deploy Gemma backend to Cloud Run with GPU
4. Deploy ADK agent and test with elasticity testing

## 🔗 Resources

- [Complete Solution](https://github.com/amitkmaraj/accelerate-ai-lab3-complete)
- [Google ADK Documentation](https://cloud.google.com/agent-development-kit)
- [Cloud Run Documentation](https://cloud.google.com/run/docs)

Happy coding! 🎉
