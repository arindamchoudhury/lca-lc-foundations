# 🔗 Introduction to LangChain - Python

## Introduction

Welcome to LangChain Academy's **Introduction to LangChain** course!

This repository is the companion to the course located [HERE](https://academy.langchain.com/courses/foundation-introduction-to-langchain-python).

---

## 🚀 Setup

### Prerequisites

- The [Chrome](https://www.google.com/chrome/) browser is recommended
- [git](https://git-scm.com/install/) is recommended
- A package/project manager: [uv](https://docs.astral.sh/uv/) (recommended), [pip](https://pypi.org/project/pip/), or [conda](https://docs.conda.io/)
- note: `uv` is also required in Module 2, Lesson 1 to run the MCP server with `uvx`
- The course requires Python >=3.12, <3.14. **Python 3.13 is recommended** — Python 3.14 is not yet supported. If you use `uv`, it will take care of this for you. [More info](#python-virtual-environments)

### Installation

Download the course repository
```bash
# Clone the repo
git clone --depth 1 https://github.com/langchain-ai/lca-lc-foundations.git
cd lca-lc-foundations
```

Make a copy of example.env
```bash
# Create .env file
cp example.env .env
```

Edit the .env file to include the keys below for [Models](#model-providers) and optionally [LangSmith](#getting-started-with-langsmith)

- Get an OpenAI API Key [here](https://openai.com/index/openai-api/).  
- Optional for Module1/Lesson1, get an Anthropic API Key [here](https://console.anthropic.com) and a Google API Key [here](https://ai.google.dev/gemini-api/docs/quickstart).
- Optional, Create a [LangSmith](https://smith.langchain.com/) account and API Key.  

```bash
# Manual installs for checking: uv

# Required
OPENAI_API_KEY='your_openai_api_key_here'
TAVILY_API_KEY='your_tavily_api_key_here'

# optional, only used in Module1, Lesson 1 once
ANTHROPIC_API_KEY='your_anthropic_api_key_here'
GOOGLE_API_KEY='your_google_api_key_here'

# Optional for evaluation and tracing
LANGSMITH_API_KEY='your_langsmith_api_key_here'
# uncomment to set tracing to true when you set up your LangSmith account
#LANGSMITH_TRACING=true
LANGSMITH_PROJECT=lca-lc-foundation
# Uncomment the following if you are on the EU instance:
#LANGSMITH_ENDPOINT=https://eu.api.smith.langchain.com
```


Make a virtual environment and install dependencies. [More info](#python-virtual-environments)

<details open>
<summary>Using uv (recommended)</summary>

```bash
uv sync
```

</details>

<details>
<summary>Using pip</summary>

```bash
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

</details>

<details>
<summary>Using conda</summary>

```bash
conda env create -f environment.yml
conda activate lc-foundations
```

To update an existing conda environment:
```bash
conda env update -f environment.yml --prune
```

</details>

### Dependency Versions (updated May 2026)

<details>
<summary>View version changes</summary>

| Package | Previous | Current |
|---|---|---|
| `langchain` | >=1.1.3 | >=1.3.2 |
| `langchain-core` | >=1.3.3 | >=1.4.0 |
| `langchain-openai` | >=1.1.1 | >=1.2.2 |
| `langchain-anthropic` | >=1.0.3 | >=1.4.4 |
| `langchain-google-genai` | >=3.1.0 | >=4.2.4 |
| `langchain-tavily` | >=0.2.13 | >=0.2.18 |
| `langchain-community` | >=0.4.1 | >=0.4.2 |
| `langchain-text-splitters` | >=1.0.0 | >=1.1.2 |
| `langchain-mcp-adapters` | >=0.1.13 | >=0.2.2 |
| `langgraph` | >=1.0.3 | >=1.2.2 |
| `langgraph-cli` | >=0.4.9 | >=0.4.27 |
| `langsmith` | >=0.8.5 | >=0.8.6 |

</details>

### Setup Verification

After completing the Setup section, we recommend you run the following command to verify your environment.

<details open>
<summary>Using uv</summary>

```bash
uv run python env_utils.py
```

</details>

<details>
<summary>Using pip</summary>

```bash
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
python env_utils.py
```

</details>

[If the script flags issues, see this section below.](#setup-verification-issues)

### Run Notebooks [More Info](#development-environment)

<details open>
<summary>Using uv (recommended)</summary>

```bash
uv run jupyter lab
```

</details>

<details>
<summary>Using pip or conda</summary>

```bash
source .venv/bin/activate      # pip: On Windows: .venv\Scripts\activate
conda activate lc-foundations  # conda
jupyter lab
```

</details>

### Run Studio (optional)

Ensure you are in the notebooks/module-1 or notebooks/module-3 directory

 <details open>
<summary>Using uv (recommended)</summary>

```bash
uv run langgraph dev
```

</details>

<details>
<summary>Using pip</summary>

```bash
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
langgraph dev
```

</details>

## 📚 Lessons
This repository contains three Modules that serve as introductions to many of LangChain's most-used features.

---

### Module 1: Create Agent

- Foundational models
- Tools
- Short-Term Memory
- Multimodal Messages
- Project: Personal Chef

### Module 2: Advanced Agent

- Model Context Protocol (MCP)
- Context and State
- Multi-Agent Systems
- Project: Wedding Planner

### Module 3: Production-Ready Agent

- What is Middleware?
- Managing Long Conversations
- Human In The Loop (HITL)
- Dynamic Agents
- Project: Email Assistant
- Bonus: Agent Chat UI

## 📖 Related Resources

### Setup Verification Issues

**What the verification procedure checks:**
- ✅ Python executable location and version (must be >=3.12, <3.14)
- ✅ Virtual environment is properly activated
- ✅ Required packages are installed with correct versions
- ✅ Packages are in the correct Python version's site-packages
- ✅ Environment variables (API keys) are properly configured

**Configuration Issues and Solutions:**

<details>
<summary>ImportError when running env_utils.py</summary>

If you see an error like `ModuleNotFoundError: No module named 'dotenv'`, you're likely running Python outside the virtual environment.

**Solution:**
- Use `uv run python env_utils.py` (recommended), or
- Activate the virtual environment first:
  - macOS/Linux: `source .venv/bin/activate`
  - Windows: `.venv\Scripts\activate`

</details>

<details>
<summary>Environment Variable Conflicts</summary>

If you see a warning about "ENVIRONMENT VARIABLE CONFLICTS DETECTED", you have API keys set in your system environment that differ from your .env file. Since `load_dotenv()` doesn't override existing variables by default, your system values will be used.

**Solutions:**
1. Do nothing and accept the system environment variable value
2. Unset the conflicting system environment variables for this shell session (commands provided in warning)
3. Use `load_dotenv(override=True)` in your notebooks to force .env values to take precedence
4. Update your .env file or shell init so the values are in agreement

</details>

<details>
<summary>LangSmith Tracing Errors</summary>

If you see "LANGSMITH_TRACING is enabled but LANGSMITH_API_KEY still has the example/placeholder value", you need to either:
1. Set a valid LangSmith API key in your .env file, or
2. Comment out or set `LANGSMITH_TRACING=false` in your .env file

Note: LangSmith is optional for evaluation and tracing. The course works without it.

</details>

<details>
<summary>Wrong Python Version</summary>

If you see a warning about Python version not satisfying requirements, you need Python >=3.12 and <3.14. **Python 3.14 is not yet supported** — use Python 3.13.

**Solution:**
- If using `uv`: Run `uv sync` which will automatically install the correct Python version
- If using pip: Install Python 3.13 using [pyenv](#python-virtual-environments) or from [python.org](https://www.python.org/downloads/)
- If using conda: The `environment.yml` pins to Python 3.13 automatically

</details>

### Python Virtual Environments

Managing your Python version is often best done with virtual environments. This allows you to select a Python version for the course independent of the system Python version.

<details open>
<summary>Using uv (recommended)</summary>

`uv` will install a version of Python compatible with the versions specified in the `pyproject.toml` in the `.venv` directory when running the `uv sync` specified above. It will use this version when invoking with `uv run`. For additional information, please see [uv](https://docs.astral.sh/uv/).
</details>

<details>
<summary>Using pyenv + pip</summary>

If you are using pip instead of uv, you may prefer using pyenv to manage your Python versions. For additional information, please see [pyenv](https://github.com/pyenv/pyenv).

```bash
pyenv install 3.12
pyenv local 3.12
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

</details>

### Model Providers

If you don't have an OpenAI API key, you can sign up [here](https://openai.com/index/openai-api/). The course primarily uses `gpt-5-nano` which is very inexpensive. A newer drop-in replacement, `gpt-5.4-nano` (released March 2026), is also available — swap the model name in `init_chat_model()` if desired.  If desired, you may also obtain additional API keys for [Anthropic](https://console.anthropic.com) or [Google](https://ai.google.dev/gemini-api/docs/quickstart).

This course has been created using particular models and model providers.  You can use other providers, but you will need to update the API keys in the .env file and make some necessary code changes. LangChain supports many chat model providers. [More Info](https://docs.langchain.com/oss/python/integrations/providers/all_providers).

Tavily is a search provider that returns search results in an LLM-friendly way. They have a generous free tier. [Tavily](https://tavily.com)

If you prefer not to sign up for Tavily, you can use `DuckDuckGoSearchRun` instead — no API key required:

```python
from langchain_community.tools import DuckDuckGoSearchRun
search = DuckDuckGoSearchRun()
```

#### Using DeepSeek (cheaper alternative to OpenAI)

[DeepSeek](https://platform.deepseek.com) offers an OpenAI-compatible API at roughly 10-35x lower cost. Add your key to `.env`:

```env
DEEPSEEK_API_KEY = 'your_key_here'
```

Then use it in notebooks via the OpenAI integration:

```python
from langchain_openai import ChatOpenAI

model = ChatOpenAI(
    model="deepseek-chat",
    api_key=os.environ["DEEPSEEK_API_KEY"],
    base_url="https://api.deepseek.com/v1"
)
```

#### Running Locally with Ollama (no API keys required)

All notebooks can be run using free local models via [Ollama](https://ollama.com), with no API keys needed.

**1. Install Ollama** — download from [ollama.com](https://ollama.com) and install.

**2. Pull a model:**

```bash
# Recommended for this course (RTX 3060 6GB or similar)
ollama pull qwen3.5:4b

# For multimodal notebooks (Module 1, Lesson 4)
ollama pull llava
```

| Model | VRAM | Best for |
|---|---|---|
| `qwen3.5:4b` (recommended) | ~3.5GB | All text-based notebooks — fast and capable |
| `qwen3.5:9b` | ~6GB | Better reasoning; tight on 6GB cards |
| `llava` | ~4GB | Multimodal (image) notebooks |

**3. Replace model initialisation in notebooks:**

```python
# Instead of:
from langchain.chat_models import init_chat_model
model = init_chat_model(model="gpt-5-nano")

# Use:
from langchain_ollama import ChatOllama
model = ChatOllama(model="qwen3.5:4b")
```

**4. Structured output** — pass `method="json_mode"` explicitly:

```python
structured_model = model.with_structured_output(MySchema, method="json_mode")
```

**Note:** No changes to `.env` are needed when using Ollama. The Ollama server runs locally at `http://localhost:11434` and requires no API key.

**5. Keep the model warm (avoid slow cold starts)**

The first invocation takes 60–100s while the model loads into VRAM. By default Ollama unloads the model after 5 minutes of inactivity. To keep it resident for your session, pass `keep_alive` to `ChatOllama`:

```python
model = ChatOllama(model="qwen3.5:4b", keep_alive="1h")   # keep loaded for 1 hour
# model = ChatOllama(model="qwen3.5:4b", keep_alive=-1)   # keep until Ollama restarts
```

To change the server-wide default, set the environment variable before starting Ollama:

```powershell
# Windows — persist for your user, then restart Ollama from the system tray
[System.Environment]::SetEnvironmentVariable("OLLAMA_KEEP_ALIVE", "1h", "User")
```

**6. Reduce VRAM usage (optional)**

The default context length is 16 384 tokens, which reserves ~1.6 GB of VRAM for the KV cache. Lower it if you are tight on memory:

```python
model = ChatOllama(model="qwen3.5:4b", num_ctx=4096)
```

**7. Monitor Ollama logs (Windows):**

```powershell
Get-Content "$env:LOCALAPPDATA\Ollama\server.log" -Wait -Tail 20
```

Key lines to look for:
- `offloaded X/Y layers to GPU` — confirms GPU is being used
- `eval rate: XX tokens/s` — generation speed (expect 25-40 t/s for `qwen3.5:4b`)

### Getting Started with LangSmith

- Create a [LangSmith](https://smith.langchain.com/) account
- Create a LangSmith API key

<img width="600" alt="LangSmith Dashboard" src="https://github.com/user-attachments/assets/e39b8364-c3e3-4c75-a287-d9d4685caad5" />

<img width="600" alt="LangSmith API Keys" src="https://github.com/user-attachments/assets/2e916b2d-e3b0-4c59-a178-c5818604b8fe" />

- Update the .env file you created with your new LangSmith API Key.
- Check that LANGSMITH_TRACING is uncommented and set to true.

For more information on LangSmith, see our docs [here](https://docs.langchain.com/langsmith/home).

**Note:** If you enable LangSmith tracing by setting `LANGSMITH_TRACING=true` in your .env file, make sure you have a valid `LANGSMITH_API_KEY` set. The environment verification script (`env_utils.py`) will warn you if tracing is enabled without a valid key.

### Environment Variables

This course uses the [dotenv](https://pypi.org/project/python-dotenv) module to read key-value pairs from the .env file and set them in the environment in the Jupyter notebooks. They do not need to be set globally in your system environment.

**Note:** If you have API keys already set in your system environment, they may conflict with the ones in your .env file. The `env_utils.py` verification script will detect and warn you about such conflicts. By default, `load_dotenv()` does not override existing environment variables.


### Development Environment

The course uses [Jupyter](https://jupyter.org/) notebooks. The Jupyter package is installed in the virtual environment and can be run as described above. Jupyter notebooks can also be edited and run in VSCode or other VSCode variants such as Windsurf or Cursor.
