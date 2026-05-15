# Project Analysis

MedChat is an Arabic medical chatbot project built from five connected parts:

1. `nlp_pipeline`: normalizes Arabic medical questions, classifies intent, and extracts drug entities.
2. `bert_safety_classifier`: fine-tunes AraBERT/BERT to classify query safety as `Low`, `Medium`, or `High`.
3. `dosage_reasoning`: uses patient profile features plus few-shot reasoning data to produce personalized dosage guidance through Groq-hosted LLM calls.
4. `rag_system`: builds drug-aware retrieval over the cleaned medicine core data and integration notebooks that combine NLP, safety, dosage, and retrieval.
5. `gui`: a browser chat interface with local chat state, Arabic UX, and ElevenLabs text-to-speech support.

The original project folders were named by person number. This clean version renames them by responsibility so the repository is easier to review and present.

Important cleanup work done before upload:

- Replaced hardcoded API keys with environment variables.
- Removed `.env`, temporary key files, `__pycache__`, local Vercel metadata, and generated Chroma stores.
- Excluded model weights, training optimizer states, zipped model exports, and raw archives that exceed GitHub limits.
- Renamed screenshots and notebooks into predictable locations.
- Cleared notebook outputs to avoid leaking local paths and to keep the repository smaller.

