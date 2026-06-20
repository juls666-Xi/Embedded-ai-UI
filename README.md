How It Works

1. Loads the Model – When you click "Embed", the UI downloads the 8-bit quantized ONNX version of gte-small (~30 MB) from Hugging Face.
2. Computes Embeddings – Converts your text into a 384‑dimensional vector using mean pooling + L2 normalization.
3. Compares Similarity – Enter a second sentence and click = to compute cosine similarity between the two embeddings.

Using the Actual GGUF File

If you want to run the exact .gguf file you linked, use one of these tools:

Tool Command / Instructions
llama.cpp ./llama-embedding -m gte-small.Q8_0.gguf -p "Your text"
LM Studio Load the .gguf file and use the embedding endpoint
Python from llama_cpp import Llama; llm = Llama(model_path="gte-small.Q8_0.gguf", embedding=True)

The embeddings from the GGUF file and this UI will be identical because they come from the same base model.# Embedded-ai-UI

step‑by‑step guide to get the embedding UI running on your machine.

---

1. Save the HTML file

· Copy the entire HTML code I provided above.
· Open a text editor (Notepad, VS Code, etc.).
· Paste the code.
· Save the file as index.html (or any name you like, but keep the .html extension).

---

2. Open it in your browser

· Double‑click the saved file – it will open in your default web browser.
· No server needed – it runs entirely in your browser (client‑side).

---

3. First load & model download

· The first time you click “✨ Embed”, the UI will automatically download the model (Xenova/gte-small) from Hugging Face.
· This is a ~30 MB 8‑bit quantized ONNX model – the download happens once and is cached by your browser for future use.
· You’ll see a status message like “Loading model (8-bit quantized)…” – wait a few seconds.

---

4. Generate an embedding

· In the text box, type or paste any sentence (e.g., “That is a happy person”).
· Click “✨ Embed”.
· After a short moment, the 384‑dimensional vector will appear below, showing the first 12 values and the total dimension.
· The embedding is normalized (unit length) – ready for cosine similarity.

---

5. Compare two sentences (similarity)

· In the second input box (labelled “Compare similarity”), enter another sentence (e.g., “That is a very happy person”).
· Click the = button.
· The UI will compute the cosine similarity between the two embeddings and display a value between -1 and 1 (closer to 1 means more similar).
· The first sentence’s embedding is reused if you haven’t changed it – so it’s fast.

---

6. Keyboard shortcuts

· Press Enter (without Shift) in the main text area to trigger Embed.
· Press Enter in the comparison input box to trigger Similarity.

---

⚠️ Important notes

Issue Solution
Model loads slowly Be patient – it’s a ~30 MB download. Subsequent loads are instant thanks to browser caching.
“Failed to load model” Check your internet connection. The model is loaded from Hugging Face’s CDN.
Out of memory / slow The model runs in your browser’s WebAssembly environment – close other heavy tabs if needed.
I want the exact .gguf file The UI uses the ONNX version of the same model. For the GGUF file, use llama.cpp or LM Studio (see below).

---

7. (Optional) Using the actual .gguf file

If you prefer to run the .gguf file directly (the one you linked), here are two easy ways:

With llama.cpp (command line)

```bash
./llama-embedding -m gte-small.Q8_0.gguf -p "Your text here"
```

This will print the embedding vector to the console.

With Python + llama-cpp-python

```python
from llama_cpp import Llama
llm = Llama(model_path="gte-small.Q8_0.gguf", embedding=True)
embedding = llm.create_embedding("Your text")
print(embedding)
```

---

8. That’s it!

Everything runs 100% locally – no data leaves your browser. The UI is fully self‑contained in a single HTML file. Enjoy exploring semantic similarity with GTE‑Small! 🚀