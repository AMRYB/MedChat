# MedChat

MedChat is an Arabic medical assistant / RxChat deep learning project. It combines Arabic NLP, AraBERT safety classification, personalized dosage reasoning, drug RAG retrieval, and a web GUI.

This project is for academic demonstration only. It must not be used as a replacement for professional medical advice.

## Project Structure

```text
MedChat/
  nlp_pipeline/              Arabic normalization, intent classification, drug NER
  bert_safety_classifier/    AraBERT/BERT safety-risk classifier and Flask API
  dosage_reasoning/          Personalized dosage FastAPI service
  rag_system/                Drug RAG notebooks, cleaned drug data, retrieval reports
  gui/                       Chat UI and text-to-speech server
  docs/                      Project analysis and artifact notes
```

## Main Components

`nlp_pipeline`

- Normalizes Arabic patient questions.
- Predicts intent such as dosage, interaction, side effects, and contraindication.
- Extracts drug names with a token-classification NER model.
- Uses fuzzy matching as a backup for drug name correction.

`bert_safety_classifier`

- Trains an AraBERT/BERT sequence classifier on Arabic safety data.
- Classifies risk as `Low`, `Medium`, or `High`.
- Provides a Flask API at `/predict`.

`dosage_reasoning`

- Defines a patient profile schema: age, weight, gender, chronic conditions, kidney function, and liver function.
- Trains/loads a small RandomForest risk classifier from the dosage examples.
- Builds few-shot prompts and calls a Groq-hosted model using `GROQ_API_KEY`.
- Exposes a FastAPI endpoint: `POST /dosage`.

`rag_system`

- Uses cleaned drug core data for retrieval.
- Contains RAG and integration notebooks using LlamaIndex, ChromaDB, Groq, and drug-aware retrieval logic.
- Includes a retrieval test report in `rag_system/reports/`.

`gui`

- Browser chat interface for the final demo.
- Includes local chat history, account switching, message actions, and ElevenLabs text-to-speech.
- Runs with Node.js from `gui/server.js`.

## Setup

Python:

```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

GUI:

```bash
cd gui
copy .env.example .env
npm install
npm run dev
```

Environment variables:

```bash
GROQ_API_KEY=your_groq_api_key_here
GROQ_MODEL=qwen/qwen3-32b
ELEVENLABS_API_KEY=your_elevenlabs_api_key_here
```

## Run Services

NLP API:

```bash
cd nlp_pipeline
uvicorn api.main:app --reload --port 8001
```

BERT safety API:

```bash
cd bert_safety_classifier
python api/person2_api.py
```

Dosage API:

```bash
cd dosage_reasoning
python dosage_calculator.py
```

GUI:

```bash
cd gui
npm run dev
```

## Artifacts Not Committed

Large trained weights and generated stores are excluded from Git because the original files exceed GitHub limits. See `docs/model_artifacts.md` for expected local paths.

Examples:

- `*.safetensors`
- `optimizer.pt`
- ChromaDB stores
- zipped model exports
- raw `.rar` archives

## Team Contributions

- Amr Yasser: RAG system and GUI.
- Mohamed Ayman and Omar Ragab: AraBERT/BERT safety model.
- Mohamed Galal: the remaining NLP and dosage modules found in the project, including Arabic normalization/intent/NER and personalized dosage reasoning utilities.

