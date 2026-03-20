![GitHub](https://img.shields.io/github/license/DataForScience/GeminiAI)
[![Twitter @data4sci](https://img.shields.io/twitter/follow/data4sci)](https://twitter.com/intent/follow?screen_name=data4sci)
![GitHub top language](https://img.shields.io/github/languages/top/DataForScience/GeminiAI)
![GitHub repo size](https://img.shields.io/github/repo-size/DataForScience/GeminiAI)
![GitHub last commit](https://img.shields.io/github/last-commit/DataForScience/GeminiAI)

[![Graphs For Science](https://img.shields.io/badge/Graphs_For_Science-Subscribe-blue)](https://graphs4sci.substack.com/)
[![Data Science Briefing](https://img.shields.io/badge/Sunday_Briefing-Subscribe-blue)](https://data4science.ck.page/a63d4cc8d9)

# Gemini API with Vertex AI for Developers

### Code and slides for the Data For Science webinar series: [Gemini API with Vertex AI for Developers](https://www.oreilly.com/live-events/gemini-api-with-vertexai-for-developers/0642572299484/) (O’Reilly).

This course explores Google’s generative AI stack: the **Gemini API** (Google AI Studio and Vertex AI) on **Google Cloud**. You’ll work through text and multimodal use cases, deployment and MLOps patterns on Vertex AI, and end-to-end solution design (RAG, agents, and pipelines). The notebooks are meant to be run in order so concepts and credentials build from one module to the next.

## Course structure

### 1. Gemini API and Vertex AI fundamentals
- Generative AI overview
- Gemini API introduction
- Vertex AI overview

### 2. Gemini API for text generation
- Prompt engineering for text models
- Text generation with the Gemini API
- Information extraction with text models

### 3. Multimodal applications with the Gemini API
- Image and video understanding
- Hands-on: captioning and visual Q&A
- Multimodal inputs for richer applications
- Real-world multimodal use cases

### 4. Vertex AI and deployment strategies
- MLOps practices with Vertex AI (including Kubeflow Pipelines samples)
- Model monitoring and explainability concepts
- Deploying Gemini-powered applications (e.g. Cloud Run-oriented examples)
- Scaling and optimization considerations for production

### 5. End-to-end generative AI solutions
- Architecture patterns: **RAG**, **agents**, and **multi-stage pipelines**
- Designing production-oriented generative AI systems
- Security, privacy, and responsible use

## Setup

**Requirements:** Python **3.10+** (the materials are tested with **3.12**). Dependencies are defined in `pyproject.toml` and locked with `uv.lock`.

### 1) Install dependencies (recommended: `uv`)

1. Install [uv](https://github.com/astral-sh/uv) if needed:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

2. Clone the repo and install into a local virtual environment:

```bash
git clone https://github.com/DataForScience/GeminiAI.git
cd GeminiAI
uv sync
```

`uv sync` creates `.venv` and installs Jupyter, Gemini/Vertex client libraries, **KFP** (Kubeflow Pipelines), and the rest of the stack. To use the environment explicitly:

```bash
source .venv/bin/activate   # Windows: .venv\Scripts\activate
```

### 2) API keys and Google Cloud

| What you need | Used for | Where to get it |
|---------------|----------|-----------------|
| **GEMINI_API_KEY** | Calling the Gemini API from notebooks (Google AI Studio key) | [Google AI Studio](https://aistudio.google.com/) |
| **GCP_PROJECT** | Vertex AI, deployment, and cloud examples | [Google Cloud Console](https://console.cloud.google.com/) *(free tier available)* |

Set environment variables in your shell or in a **`.env`** file in the project root (gitignored). The course uses **`GEMINI_API_KEY`** (not `GOOGLE_API_KEY`).

For **Vertex AI** and GCP APIs, enable the **Vertex AI API** on your project and authenticate with Application Default Credentials, for example:

```bash
gcloud auth application-default login
gcloud services enable aiplatform.googleapis.com --project=YOUR_PROJECT_ID
```

Exact `gcloud` steps also appear in the notebooks where relevant.

### 3) Launch Jupyter

From the project directory (with the env active, or via `uv run`):

```bash
uv run jupyter notebook
```

### Alternative: `pip` / `venv`

This repository is **not** configured as an installable Python package (no `src` layout / package discovery), so **`pip install -e .` is not supported**. Prefer **`uv sync`**.

If you cannot use `uv`, create a virtual environment and install the dependencies listed under **`[project].dependencies`** in `pyproject.toml`, for example:

```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install "google-cloud-aiplatform>=1.71.1" "google-genai>=1.68.0" "google-generativeai>=0.8.6" "jupyter>=1.1.1" "kfp>=2.13.0" "matplotlib>=3.10.8" "numpy>=2.2.6" "pandas>=2.3.3" "vertexai>=1.71.1" "watermark>=2.6.0"
```

The checked-in **`requirements.txt`** is a **minimal, older pin** (matplotlib / numpy / pandas / watermark only) and does **not** include the Gemini, Vertex AI, or KFP stack.

## Repository structure

```
GeminiAI/
├── 1. Gemini Fundamentals.ipynb      # Module 1
├── 2. Text Generation.ipynb          # Module 2
├── 3. Multimodal.ipynb               # Module 3
├── 4. Deployment.ipynb               # Module 4
├── 5. E2E Solutions.ipynb            # Module 5
├── Untitled.ipynb                    # D4Sci notebook template (branding / structure)
├── slides/
│   ├── GeminiAI.pdf                  # Primary slide deck
├── data/                             # Logos, author image, sample images/audio/video
├── d4sci.mplstyle                    # Matplotlib style for figures
├── pyproject.toml                    # Project metadata and dependencies
├── uv.lock                           # Locked versions for uv
├── requirements.txt                  # Legacy minimal deps only (see Setup)
├── LICENSE
```

## Suggested learning path

- Work through **Modules 1 → 5** in order.
- For slides only, open **`slides/GeminiAI.pdf`**.

| Notebook | Topic |
|----------|--------|
| `1. Gemini Fundamentals.ipynb` | Gemini API and Vertex AI fundamentals |
| `2. Text Generation.ipynb` | Gemini API for text generation |
| `3. Multimodal.ipynb` | Multimodal applications |
| `4. Deployment.ipynb` | Vertex AI and deployment strategies |
| `5. E2E Solutions.ipynb` | End-to-end generative AI solutions |

---

## Estimated API costs

Running all notebooks end-to-end typically costs on the order of **$1–3** in API usage, depending on how often you re-run cells and current pricing.

Vertex AI / Cloud Run / build steps in Module 4 can incur **additional GCP charges** if you execute them against a real project.

---

## Questions?

Reach out at [info@data4sci.com](mailto:info@data4sci.com) or open an issue if something isn’t working.

## Author

<table border="0">
 <tr>
	<td>
	  <img src="data/bgoncalves.png" alt="Bruno Gonçalves" width="150" height="150" style="border-radius: 50%; object-fit: cover;">
	</td>
	<td>
	  <h2>Bruno Gonçalves</h2>
	  <h3>Data For Science, Inc.</h3>
	  <p>
			Web: <a href="http://www.data4sci.com/">www.data4sci.com</a><br>
			Twitter/X: <a href="https://twitter.com/bgoncalves">@bgoncalves</a><br>
			LinkedIn: <a href="https://www.linkedin.com/in/bmtgoncalves/">@bmtgoncalves</a><br>
			Email: <a href="mailto:info@data4sci.com">info@data4sci.com</a><br>
			Schedule a Call: <a href="https://data4sci.com/call">https://data4sci.com/call</a>
	  </p>
	</td>
 </tr>
</table>
