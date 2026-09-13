# webpilot-studio

<img src="./assets/web-ui.png" alt="webpilot-studio Web UI" width="full"/>

<br/>

[![GitHub stars](https://img.shields.io/github/stars/browser-use/web-ui?style=social)](https://github.com/browser-use/web-ui/stargazers)
[![Discord](https://img.shields.io/discord/1303749220842340412?color=7289DA&label=Discord&logo=discord&logoColor=white)](https://link.browser-use.com/discord)
[![Documentation](https://img.shields.io/badge/Documentation-📕-blue)](https://docs.browser-use.com)
[![WarmShao](https://img.shields.io/twitter/follow/warmshao?style=social)](https://x.com/warmshao)

**webpilot-studio** builds upon the foundation of [browser-use](https://github.com/browser-use/browser-use), which is designed to make websites accessible for AI agents.

We would like to officially thank [WarmShao](https://github.com/warmshao) for his contribution to this project.

**Web UI:** Built on Gradio, it supports most `browser-use` functionality and enables easy interaction with the browser agent.

**Expanded LLM Support:** Supports Google, OpenAI, Azure OpenAI, Anthropic, DeepSeek, Ollama, and other models.

**Custom Browser Support:** Use your own browser without signing in to sites again. High-definition screen recording is also supported.

**Persistent Browser Sessions:** Keep the browser open between AI tasks to inspect the history and state of agent interactions.

<video src="https://github.com/user-attachments/assets/56bc7080-f2e3-4367-af22-6bf2245ff6cb" controls="controls">Your browser does not support playing this video!</video>

## Installation Guide

> The project display name is **webpilot-studio**. The clone URL and `web-ui` source directory below retain their existing names; change them only if your actual repository URL or folder is different.

### Option 1: Local Installation

Read the [quickstart guide](https://docs.browser-use.com/quickstart#prepare-the-environment) or follow these steps.

#### Step 1: Clone the Repository

```bash
git clone https://github.com/browser-use/web-ui.git
cd web-ui
```

#### Step 2: Set Up Python Environment

We recommend [uv](https://docs.astral.sh/uv/) for managing the Python environment.

```bash
uv venv --python 3.11
```

Activate the virtual environment:

- Windows (Command Prompt):

  ```cmd
  .venv\Scripts\activate
  ```

- Windows (PowerShell):

  ```powershell
  .\.venv\Scripts\Activate.ps1
  ```

- macOS/Linux:

  ```bash
  source .venv/bin/activate
  ```

#### Step 3: Install Dependencies

```bash
uv pip install -r requirements.txt
playwright install --with-deps
```

To install only Chromium instead of all browsers:

```bash
playwright install chromium --with-deps
```

#### Step 4: Configure Environment

Copy the example environment file:

- Windows (Command Prompt):

  ```cmd
  copy .env.example .env
  ```

- macOS/Linux/Windows (PowerShell):

  ```bash
  cp .env.example .env
  ```

Open `.env` and add your API keys and other settings.

#### Step 5: Run webpilot-studio

```bash
python webui.py --ip 127.0.0.1 --port 7788
```

Open `http://127.0.0.1:7788` in your browser.

**Using your own browser (optional):** Set `BROWSER_PATH` to the browser executable and `BROWSER_USER_DATA` to its user-data directory. Leave `BROWSER_USER_DATA` empty to use local user data.

Windows:

```env
BROWSER_PATH="C:\Program Files\Google\Chrome\Application\chrome.exe"
BROWSER_USER_DATA="C:\Users\YourUsername\AppData\Local\Google\Chrome\User Data"
```

Replace `YourUsername` with your Windows username.

macOS:

```env
BROWSER_PATH="/Applications/Google Chrome.app/Contents/MacOS/Google Chrome"
BROWSER_USER_DATA="/Users/YourUsername/Library/Application Support/Google/Chrome"
```

Close all Chrome windows, open the Web UI in Firefox or Edge, and enable **Use Own Browser** under Browser Settings.

### Option 2: Docker Installation

#### Prerequisites

- Docker and Docker Compose
- [Docker Desktop](https://www.docker.com/products/docker-desktop/) for Windows/macOS, or [Docker Engine](https://docs.docker.com/engine/install/) and [Docker Compose](https://docs.docker.com/compose/install/) for Linux

#### Step 1: Clone the Repository

```bash
git clone https://github.com/browser-use/web-ui.git
cd web-ui
```

#### Step 2: Configure Environment

Copy `.env.example` to `.env` using the command for your shell above, then add your API keys and settings.

#### Step 3: Build and Run

```bash
docker compose up --build
```

For ARM64 systems, including Apple Silicon:

```bash
TARGETPLATFORM=linux/arm64 docker compose up --build
```

#### Step 4: Open webpilot-studio and VNC

- Web UI: `http://localhost:7788`
- VNC viewer: `http://localhost:6080/vnc.html`
- Default VNC password: `youvncpassword`; change it with `VNC_PASSWORD` in `.env`.

## Changelog

- [x] **2025/01/26:** Thanks to @vvincent1234. Browser-use Web UI can combine with DeepSeek-r1 for deeper reasoning.
- [x] **2025/01/10:** Thanks to @casistack. Docker setup and persistent browser sessions were added. [Video tutorial demo](https://github.com/browser-use/web-ui/issues/1#issuecomment-2582511750).
- [x] **2025/01/06:** Thanks to @richard-devbot. A redesigned Web UI was released. [Video tutorial demo](https://github.com/warmshao/browser-use-webui/issues/1#issuecomment-2573393113).
