# Python Tutor AI (RAG)

A beginner-friendly Python-learning chatbot built with Streamlit, OpenRouter, embeddings, cosine-similarity retrieval, and your supplied Markdown curriculum.

## Project files

- `app.py` — Streamlit UI, tutor prompt, retrieval and answer generation.
- `python_knowledge_base.md` — the supplied Python curriculum.
- `embeddings.py` — OpenRouter client, Markdown chunking, and embeddings.
- `rag.py` — cosine-similarity retrieval.
- `.env.example` — configuration template; it contains no secret key.
- `requirements.txt` — Python dependencies.

## Windows setup (VS Code / Command Prompt)

1. Extract the ZIP into a folder.
2. Install Python 3.10 or newer if it is not installed.
3. Open that folder in VS Code.
4. Create and activate a virtual environment:

   ```bat
   py -m venv .venv
   .venv\Scripts\activate
   ```

5. Install dependencies:

   ```bat
   python -m pip install --upgrade pip
   pip install -r requirements.txt
   ```

6. Copy `.env.example` to `.env` and edit `.env` with your own OpenRouter key. Never share or commit `.env`.
7. Run the app:

   ```bat
   streamlit run app.py
   ```

Streamlit will show a local URL, normally `http://localhost:8501`.

## Notes

- The first startup sends the knowledge-base chunks to the configured embedding endpoint. This may take time and incur API usage costs.
- Keep `python_knowledge_base.md` in the same directory as `app.py`.
- If you change the Markdown knowledge base or embedding model, restart the app and clear Streamlit's cached resources if needed.
- Chat answers can use general Python knowledge when no source chunk is retrieved; the interface indicates when no relevant source was found.
- The model and embedding model are configured separately. Do not put a chat-only model in `OPENROUTER_EMBEDDING_MODEL`.

## Troubleshooting

- **Missing API key:** ensure `.env` exists beside `app.py` and contains `OPENROUTER_API_KEY=...`.
- **Embedding API error:** verify that your OpenRouter account/model supports embeddings and that the model name is correct.
- **Module not found:** activate `.venv` and run `pip install -r requirements.txt` again.
- **Knowledge base not found:** confirm the filename is exactly `python_knowledge_base.md`.
