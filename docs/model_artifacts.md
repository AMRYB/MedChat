# Model and Generated Artifacts

Some trained outputs are intentionally not committed because GitHub rejects files above 100 MB and the original workspace contains multi-GB checkpoints.

Expected local artifact locations:

- `nlp_pipeline/models/intent_model_no_leakage/model.safetensors`
- `nlp_pipeline/models/ner_model/model.safetensors`
- `bert_safety_classifier/models/rxchat_safety_model_final_fixed/model.safetensors`
- `dosage_reasoning/models/safety_classifier.pkl`
- `rag_system/chroma_store/` or another regenerated ChromaDB directory

The repository keeps code, datasets, tokenizer/config metadata, notebooks, and reports. Re-train or place the model weights locally before running inference APIs that load Hugging Face models.

Security note: API keys found in the original local files were replaced or excluded from this clean repository. Rotate any key that was previously committed or shared.

