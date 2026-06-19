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