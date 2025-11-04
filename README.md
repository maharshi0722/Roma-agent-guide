# 🚀 Sentient ROMA — Complete Installation Guide

**Welcome!**  
This guide helps you install and run **Sentient ROMA**, the open-source meta-agent framework by **Sentient AGI**.  

ROMA enables multiple intelligent agents to collaborate seamlessly on complex, high-performance tasks — it’s the foundation of Sentient’s multi-agent intelligence system.  

This simplified guide ensures anyone can install and experience ROMA locally.

---

## 🧩 1. Install Ubuntu on Windows

1. Open **Microsoft Store**, search for **“Ubuntu”**, and install it.  
2. When installation completes, a terminal window opens automatically for updates.  
3. If prompted, set up your **username** and **password** — you’ll use these for later commands.  

> 💡 If Ubuntu doesn’t appear, run these in **PowerShell**:
```bash
wsl --install -d Ubuntu-22.04
wsl -s Ubuntu-22.04
🔑 2. Create an OpenRouter Account & API Key
Visit https://openrouter.ai/

Sign in with Google or another provider.

Click the ⚙️ Settings icon → API Keys → Create API Key.

Name your key, click Create, and copy it (starts with sk-).

⚠️ You won’t be able to view it again later — store it safely.

🐳 3. Install Docker Desktop
Go to Docker Desktop for Windows.

Download and install Docker.

After setup, open Docker Desktop → click Continue without signing in.

Wait until you see “Docker Desktop Running” in the bottom-right corner.

If you get an error, restart Docker and allow it to update.

⚙️ Enable Ubuntu Integration
In Docker Desktop, open Settings → Resources → WSL Integration.

Enable Ubuntu and click Restart & Apply.

🧱 4. Set Up Ubuntu Environment
Open the Ubuntu 22.04 app and run these commands:

bash
Copy code
sudo apt update && sudo apt upgrade -y
sudo apt install git docker.io docker-compose -y
This installs the tools required for ROMA.

🧠 5. Clone and Install ROMA
bash
Copy code
git clone https://github.com/sentient-agi/ROMA.git
cd ROMA
./setup.sh --docker
The installation will take around 10 minutes.
Once completed, continue to configuration.

🪄 6. Configure Your API Key
Link your OpenRouter API key with ROMA:

bash
Copy code
cd
cd ROMA
sed -i 's/api_key: "your-openrouter-key"/api_key: "${OPENROUTER_API_KEY}"/' sentient.yaml
sed -i 's/OPENROUTER_API_KEY=your_openrouter_key_here/OPENROUTER_API_KEY=sk_your_api_key_here/' .env
🔑 Replace sk_your_api_key_here with your actual OpenRouter key.

🧬 7. Set Model ID
Specify the AI model ROMA will use.
This guide uses DeepSeek Chat V3.1 (Free) from OpenRouter:

bash
Copy code
cd ~/ROMA/src/sentientresearchagent/hierarchical_agent_framework/agent_configs
sed -i 's/model_id:.*".*"/model_id: "openrouter\/deepseek\/deepseek-chat-v3.1:free"/g' agents.yaml
⚡ 8. Start ROMA Services
bash
Copy code
cd ~/ROMA/docker
docker compose down
docker compose up -d
docker restart
Wait 2–3 minutes for all containers to initialize.

🔍 9. Check Logs (Optional)
You can verify that ROMA is running correctly with:

docker compose logs -f
If everything is working, you’ll see logs showing active agents.
Press Ctrl + C to exit.

🌐 10. Launch ROMA Interface
Open your browser and go to:
👉 http://localhost:3000/

You should now see the ROMA web interface and can start experimenting!
👉 http://localhost:3000/

You should now see the ROMA web interface and can start experimenting!
