# 🏦 Loan Approval AI Banking System

A comprehensive AI-powered loan application processing system that intelligently analyzes and makes loan approval decisions using LangGraph-based agent orchestration.

## 📋 Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [API Documentation](#api-documentation)
- [Architecture](#architecture)
- [Agent Pipeline](#agent-pipeline)
- [License](#license)

---

## 🎯 Overview

The **Loan Approval AI Banking System** is an intelligent application that processes loan applications through multiple AI agents. Each agent specializes in a specific aspect of loan analysis:

- **Profile Agent**: Evaluates applicant profile and income stability
- **Risk Agent**: Analyzes financial risk based on debt-to-income ratio
- **Decision Agent**: Makes approval/rejection decisions
- **Compliance Agent**: Ensures regulatory compliance and timestamps the decision

The system provides a user-friendly Streamlit frontend and a robust FastAPI backend for seamless loan processing.

---

## ✨ Features

✅ **Multi-Agent AI Pipeline**
- Specialized agents for profile, risk, decision, and compliance analysis
- LangGraph-based orchestration for complex workflows

✅ **Interactive Web Interface**
- Streamlit-powered frontend for easy loan application input
- Real-time analysis results with visual feedback
- Comprehensive result breakdown with metrics

✅ **RESTful API Backend**
- FastAPI-based REST API
- JSON request/response format
- Scalable and production-ready

✅ **Detailed Analysis Output**
- Income stability assessment
- Employment risk evaluation
- Debt-to-income (DTI) ratio calculation
- Risk level classification
- Final approval/rejection decision with timestamp

✅ **Security**
- Environment variable management for API keys
- Clean separation of concerns
- Modular agent architecture

---

## 🛠️ Tech Stack

### Backend
- **Framework**: FastAPI (Python web framework)
- **AI/ML**: LangGraph (Agentic workflow orchestration)
- **API Server**: Uvicorn (ASGI server)

### Frontend
- **Framework**: Streamlit (Interactive web app)
- **HTTP Client**: Requests (API communication)

### Infrastructure
- **Language**: Python 3.12+
- **Virtual Environment**: venv
- **API Communication**: HTTP/REST

### Key Dependencies
```
fastapi==0.104+
streamlit==1.28+
langgraph==1.2.5+
requests==2.31+
uvicorn==0.24+
```

---

## 📁 Project Structure

```
RKV-_-Loan-App-Banking-System/
├── README.md                          # Project documentation
├── .gitignore                         # Git ignore rules
├── Agents/                            # AI Agent modules
│   ├── __init__.py
│   ├── profile_agent.py              # Profile analysis agent
│   ├── risk_agent.py                 # Risk assessment agent
│   ├── decision_agent.py             # Decision making agent
│   └── compliance_agent.py           # Compliance verification agent
└── Loan AI Banking App/              # Streamlit + FastAPI application
    ├── app.py                        # Streamlit frontend
    ├── api.py                        # FastAPI backend
    ├── orchestrator.py               # LangGraph pipeline orchestration
    ├── .env                          # Environment variables (excluded from git)
    └── venv/                         # Virtual environment (excluded from git)
```

---

## 🚀 Installation

### Prerequisites
- Python 3.12 or higher
- pip (Python package manager)
- Virtual environment (recommended)

### Step 1: Clone the Repository
```bash
git clone https://github.com/reniev20-debug/RKV-_-Loan-App-Banking-System.git
cd RKV-_-Loan-App-Banking-System
```

### Step 2: Create Virtual Environment
```bash
cd "Loan AI Banking App"
python -m venv venv
```

### Step 3: Activate Virtual Environment

**On Linux/macOS:**
```bash
source venv/bin/activate
```

**On Windows:**
```bash
venv\Scripts\activate
```

### Step 4: Install Dependencies
```bash
pip install fastapi uvicorn streamlit requests langgraph pydantic python-dotenv
```

Or use requirements file (if available):
```bash
pip install -r requirements.txt
```

### Step 5: Configure Environment Variables
Create a `.env` file in the `Loan AI Banking App/` directory:
```
LLMGW_API_KEY=your_api_key_here
LLMGW_BASE_URL=https://llmgw-wp.tekstac.com
```

---

## 💻 Usage

### Running the Application

#### Terminal 1: Start FastAPI Backend
```bash
cd "Loan AI Banking App"
source venv/bin/activate
export PYTHONPATH="/path/to/parent/directory"
uvicorn api:app --host 127.0.0.1 --port 8000
```

#### Terminal 2: Start Streamlit Frontend
```bash
cd "Loan AI Banking App"
source venv/bin/activate
export PYTHONPATH="/path/to/parent/directory"
streamlit run app.py
```

### Accessing the Application

- **Streamlit UI**: http://127.0.0.1:8501
- **API Base URL**: http://127.0.0.1:8000
- **API Health Check**: http://127.0.0.1:8000/

### Example Workflow

1. **Open Streamlit Frontend**: Navigate to http://127.0.0.1:8501
2. **Fill Application Details**:
   - Age: 35
   - Annual Income: $75,000
   - Employment Type: Full-time
   - Loan Amount: $250,000

3. **Submit Application**: Click "Submit Application" button

4. **View Results**: See detailed analysis including:
   - Profile Analysis (Income Stability, Employment Risk)
   - Risk Assessment (DTI Ratio, Risk Level)
   - Final Decision (APPROVED/REJECTED)
   - Processing Timestamp

---

## 📡 API Documentation

### Endpoint: Process Loan Application

**POST** `/loan`

#### Request Body
```json
{
  "age": 35,
  "income": 75000,
  "employment": "Full-time",
  "loan_amount": 250000
}
```

#### Response (200 OK)
```json
{
  "input": {
    "age": 35,
    "income": 75000,
    "employment": "Full-time",
    "loan_amount": 250000
  },
  "profile": {
    "income_stability": "High",
    "employment_risk": "Low"
  },
  "risk": {
    "dti": 3.33,
    "risk_level": "High"
  },
  "decision": "REJECTED",
  "final": {
    "final_decision": "REJECTED",
    "timestamp": "2026-06-18 16:16:26.870968",
    "status": "Processed"
  }
}
```

### Endpoint: Health Check

**GET** `/`

#### Response
```json
{
  "message": "Loan AI API Running"
}
```

#### cURL Examples

**Process Loan:**
```bash
curl -X POST http://127.0.0.1:8000/loan \
  -H "Content-Type: application/json" \
  -d '{
    "age": 35,
    "income": 75000,
    "employment": "Full-time",
    "loan_amount": 250000
  }'
```

**Health Check:**
```bash
curl http://127.0.0.1:8000/
```

---

## 🏗️ Architecture

### System Design

```
┌─────────────────────┐
│   Streamlit UI      │
│   (Frontend)        │
└──────────┬──────────┘
           │ HTTP Request
           ▼
┌─────────────────────┐
│   FastAPI Server    │
│   (Backend)         │
└──────────┬──────────┘
           │ Python Call
           ▼
┌─────────────────────┐
│   Orchestrator      │
│   (LangGraph)       │
└──────────┬──────────┘
           │
    ┌──────┼──────┬──────┬────────┐
    │      │      │      │        │
    ▼      ▼      ▼      ▼        ▼
┌────────┐┌────┐┌────┐┌────┐┌──────────┐
│Profile ││Risk││Dec-││Com-││External  │
│Agent   ││Ag. ││ision││pliance│API   │
│        ││    ││ Ag.││ Ag.││         │
└────────┘└────┘└────┘└────┘└──────────┘
```

### Data Flow

1. **User Input** → Streamlit captures application details
2. **API Request** → Frontend sends JSON to FastAPI backend
3. **Orchestration** → LangGraph routes through agent pipeline
4. **Analysis** → Each agent processes and returns results
5. **Decision** → Final agent produces approval decision
6. **Response** → Results returned to frontend for display

---

## 🤖 Agent Pipeline

### 1. Profile Agent
- **Input**: Applicant demographics and income
- **Processing**: Evaluates income stability and employment risk
- **Output**: Profile analysis (stability level, risk category)

### 2. Risk Agent
- **Input**: Income and loan amount
- **Processing**: Calculates debt-to-income ratio and risk level
- **Output**: Risk metrics (DTI ratio, risk classification)

### 3. Decision Agent
- **Input**: Profile analysis and risk assessment
- **Processing**: Makes APPROVED/REJECTED decision based on metrics
- **Output**: Binary decision with reasoning

### 4. Compliance Agent
- **Input**: Decision result
- **Processing**: Validates compliance and adds timestamp
- **Output**: Final decision with compliance status and timestamp

### Pipeline Flow
```
Input → Profile → Risk → Decision → Compliance → Output
```

---

## 🔐 Security Notes

⚠️ **Important**

- **Never commit `.env` file**: Contains API keys and sensitive credentials
- **Use `.gitignore`**: Already configured to exclude sensitive files
- **API Keys**: Store securely in environment variables only
- **Data Protection**: User information not stored persistently in demo

---

## 📝 Configuration

### Environment Variables (.env)
```
LLMGW_API_KEY=your_api_key_here
LLMGW_BASE_URL=https://llmgw-wp.tekstac.com
```

### Streamlit Config
Default configuration in `app.py`:
- Page title: "Loan Approval AI"
- Layout: Wide
- Sidebar: Expanded

### FastAPI Config
Default configuration in `api.py`:
- Host: 127.0.0.1
- Port: 8000
- Reload: Enabled (for development)

---

## 📊 Sample Test Cases

### Test Case 1: High Income, Full-time
```json
{
  "age": 45,
  "income": 150000,
  "employment": "Full-time",
  "loan_amount": 300000
}
```
**Expected**: APPROVED (Low DTI, High stability)

### Test Case 2: Low Income, High Loan
```json
{
  "age": 25,
  "income": 30000,
  "employment": "Self-employed",
  "loan_amount": 500000
}
```
**Expected**: REJECTED (High DTI, Higher risk)

### Test Case 3: Moderate Profile
```json
{
  "age": 35,
  "income": 75000,
  "employment": "Full-time",
  "loan_amount": 200000
}
```
**Expected**: Decision based on DTI calculation

---

## 🐛 Troubleshooting

### Issue: "ModuleNotFoundError: No module named 'Agents'"
**Solution**: Ensure `PYTHONPATH` is set to parent directory
```bash
export PYTHONPATH="/path/to/parent/directory"
```

### Issue: "Cannot connect to API"
**Solution**: Verify FastAPI is running on port 8000
```bash
curl http://127.0.0.1:8000/
```

### Issue: "Port 8000 already in use"
**Solution**: Use different port
```bash
uvicorn api:app --host 127.0.0.1 --port 8001
```

### Issue: "venv not found"
**Solution**: Recreate virtual environment
```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

---

## 📚 Learning Resources

- **FastAPI**: https://fastapi.tiangolo.com/
- **Streamlit**: https://streamlit.io/
- **LangGraph**: https://langchain-ai.github.io/langgraph/
- **Python Async**: https://docs.python.org/3/library/asyncio.html

---

## 🤝 Contributing

This is a capstone project. For improvements or issues:
1. Create a fork
2. Create a feature branch
3. Make changes
4. Submit a pull request

---

## 📄 License

This project is part of an educational capstone program.

---

## 👤 Author

**RKV** - Capstone Project
- GitHub: [@reniev20-debug](https://github.com/reniev20-debug)
- Repository: [RKV-_-Loan-App-Banking-System](https://github.com/reniev20-debug/RKV-_-Loan-App-Banking-System)

---

## 📞 Support

For questions or issues:
- Check the [Troubleshooting](#troubleshooting) section
- Review the [Architecture](#architecture) diagram
- Examine agent implementations in `Agents/` directory

---

**Last Updated**: June 18, 2026

**Status**: ✅ Active and Running

---
