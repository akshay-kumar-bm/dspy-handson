# dspy-handson

Hands-on Jupyter notebooks exploring DSPy, the framework for programming (rather than prompting) language models.

## What it covers
Two notebooks in `dspy_notebook/`:

**01-notebook_getstarted.ipynb** - a guided tour:
- Configure DSPy with `openai/gpt-4o-mini` (key loaded from `.env`); optional MLflow tracking (commented out)
- Chain of Thought (`dspy.ChainOfThought`) on a probability problem, including multi-output signatures
- A small RAG pipeline: Wikipedia search via ColBERTv2 feeding a `ChainOfThought("context, question -> response")` module
- Class-based signatures: sentiment/emotion classification and structured information extraction
- A ReAct-style agent with tools (math evaluation via `dspy.PythonInterpreter`, Wikipedia search)
- A multi-stage article-generation pipeline (outline -> sections)
- Prompt optimisation with MIPROv2 on the HotPotQA dataset

**02-dspy-progaming.ipynb** - follows the DSPy "programming" docs: inline signatures, toxicity and sentiment classifiers, summarisation, `Literal`-typed emotion classification, citation-faithfulness checking, multimodal dog-breed classification from `images.jpg`, and a multi-hop `dspy.Module` (`Hop`) for claim verification.

## Tech stack
Python, DSPy, OpenAI API (gpt-4o-mini), MLflow (optional), Hugging Face `datasets`, python-dotenv, Jupyter.

## Setup
```bash
pip install -U dspy mlflow datasets python-dotenv
echo "OPENAI_API_KEY=..." > .env      # .env is git-ignored
jupyter notebook dspy_notebook/
```
MLflow cells expect a local server at `http://localhost:5000` and are commented out in notebook 01.

## Structure
```
dspy_notebook/
  01-notebook_getstarted.ipynb
  02-dspy-progaming.ipynb
  images.jpg
.gitignore   # venv, .env, mlruns
```

## Limitations
Learning notebooks only; no packaged app, no requirements file, no evaluation results written up. Several cells depend on external services (OpenAI, public ColBERTv2 Wikipedia endpoint).
