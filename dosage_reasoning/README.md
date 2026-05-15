# Dosage Reasoning

This module exposes a FastAPI service for personalized dosage reasoning.

Inputs:

- `drug_name`
- `patient_profile.age`
- `patient_profile.weight_kg`
- `patient_profile.gender`
- `patient_profile.chronic_conditions`
- `patient_profile.kidney_function`
- `patient_profile.liver_function`

Output:

- recommended dose
- visible reasoning summary
- safety flag
- doctor referral flag
- risk category: `LOW`, `MEDIUM`, or `HIGH`

Run:

```bash
set GROQ_API_KEY=your_groq_api_key_here
python dosage_calculator.py
```

Default port: `8003`.

The generated RandomForest classifier is saved to `models/safety_classifier.pkl` and is intentionally ignored by Git.
