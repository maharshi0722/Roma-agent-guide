# 🚀 Sentient ROMA - Installation Guide

**Sentient ROMA** is an open-source meta-agent framework by **Sentient AGI** that allows multiple lightweight AI agents to collaborate on complex, high-performance tasks.  

This guide walks you through the complete setup - **Ubuntu + Docker + OpenRouter + ROMA** - in one go.

---


🧠 Click Here to View Full Installation Steps

### 🧩 Step 1 - Install Ubuntu on Windows

1. Open **Microsoft Store**, search for **Ubuntu**, and install it.  
2. Once done, a terminal window opens automatically for updates.  
3. Set up your **username** and **password** when prompted.

> 💡 If Ubuntu doesn’t appear in WSL, open **PowerShell** and run:
```Bash
wsl --install -d Ubuntu-22.04
wsl -s Ubuntu-22.04
```
### 🔑 Step 2 - Create an OpenRouter Account & API Key

Go to https://openrouter.ai/

Sign in with Google (or another provider).

Go to ⚙️ Settings → API Keys → Create API Key.

Copy your new API key (starts with sk-).

⚠️ You can’t see it again after closing the page — save it securely.

### 🐳 Step 3 - Install Docker Desktop

Download from Docker Desktop for Windows
.

Install and open Docker.

Click Continue without signing in.

Wait until you see “Docker Desktop Running” at the bottom-right.

Enable Ubuntu Integration:
Open Settings → Resources → WSL Integration
Turn on Ubuntu
Click Restart & Apply

### 🧱 Step 4 - Set Up Ubuntu Environment

Open your installed Ubuntu 22.04 app and run:
```Bash
sudo apt update && sudo apt upgrade -y
sudo apt install git docker.io docker-compose -y
```

### 🧠 Step 5 - Clone and Install ROMA
```Bash
git clone https://github.com/sentient-agi/ROMA.git
cd ROMA
./setup.sh --docker
```

⏳ Installation may take around 10 minutes. Wait until it completes.

### 🔐 Step 6 - Add Your OpenRouter API Key

Replace sk_your_api_key_here below with your actual key:
```Bash
cd
cd ROMA
sed -i 's/api_key: "your-openrouter-key"/api_key: "${OPENROUTER_API_KEY}"/' sentient.yaml
```
```Bash
sed -i 's/OPENROUTER_API_KEY=your_openrouter_key_here/OPENROUTER_API_KEY=sk_your_api_key_here/' .env
```

### ⚙️ Step 7 - Set Model ID (Recommended: DeepSeek Chat v3.1 Free)
```Bash
cd ~/ROMA/src/sentientresearchagent/hierarchical_agent_framework/agent_configs
sed -i 's/model_id:.*".*"/model_id: "openrouter\/deepseek\/deepseek-chat-v3.1:free"/g' agents.yaml
```

### ⚡ Step 8 - Start ROMA Services

```Bash
cd ~/ROMA/docker
docker compose down
docker compose up -d
docker restart
```

Wait 2–3 minutes for everything to initialize.

### 🧾 Step 9 - Check Logs (Optional)
```Bash
docker compose logs -f
```

You’ll see logs indicating that ROMA services are active.
Press Ctrl + C to exit.

### 🌐 Step 10 - Launch ROMA Interface

Open your browser and go to:
```Bash
👉 http://localhost:3000/
```
<img width="1897" height="940" alt="image" src="https://github.com/user-attachments/assets/74d65b4c-972b-4459-8f41-ddf42aaef24c" />
You’re now ready to use Sentient ROMA locally 🎉



