# Gemini API: Text, Safety, and Citations (Notebook Demo)

A clean, student‑friendly demo showing how to use the **Google Gemini API** (no Google Cloud billing) for:
- Text generation (`generate_content`)
- Safety feedback (prompt blocking + candidate safety ratings)
- Citation metadata (when available)

> **Why this repo?**  
> Many older tutorials use *Vertex AI Text Bison* (`TextGenerationModel` / `.predict()` and `_prediction_response[...]`).  
> This notebook uses the **new `google-generativeai` SDK** with **Gemini 2.5** models and *clean accessors* (e.g., `response.text`).

## 📦 Setup

1. **Create a free API key** at https://aistudio.google.com/app/apikey  
   (Choose *Default Gemini Project*, name the key, copy it.)

2. **Clone** this repo and install deps:
   ```bash
   pip install -r requirements.txt
   ```

3. **Set your API key** (recommended via `.env`):
   ```bash
   echo 'GOOGLE_API_KEY=AIza...your-key...' > .env
   ```

4. **Open the notebook**:
   ```bash
   jupyter notebook gemini_safety_citations.ipynb
   ```

## 🔍 Notebook Outline

- **00 – Intro**: Overview, differences vs Vertex AI (Bison).
- **01 – Configure**: Load API key (env var or `.env`), pick a model.
- **02 – List Models**: Show which models your key can use.
- **03 – Generate**: `model.generate_content(prompt)` → `response.text`.
- **04 – Safety**: Inspect `response.prompt_feedback` and `candidate.safety_ratings`.
- **05 – Citations**: Read `response.candidates[0].citation_metadata.citations` (if present).
- **06 – Helpers**: `get_safety(response)`, `get_citations(response)`, `pretty_print_safety(...)`.

## ❗️Notes

- **Citations** appear only when the model provides *grounded* output. Use `gemini-2.5-pro` for best results.
- **Safety**: If a prompt is blocked, inspect `response.prompt_feedback["block_reason"]`.
- This demo avoids all Vertex AI / Billing requirements.

## 📝 License

MIT — feel free to reuse in research & coursework.