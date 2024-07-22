
# 🌟 GraphRAG-Local-Implementation-With-Ollama-LMStudio 🌟

Welcome to the magical world of GraphRAG! This project demonstrates how to set up and use GraphRAG with local instances of Ollama and LM Studio to conjure up an entity graph from text data. Prepare your wands as we dive into a step-by-step journey of data wizardry! 🧙‍♂️🧙‍♀️

## Table of Contents

- [Introduction](#introduction)
- [Downloading and Setting Up Ollama & LM Studio](#downloading-and-setting-up-ollama--lm-studio)
- [Configuring Models and Embeddings](#configuring-models-and-embeddings)
- [Indexing Data with GraphRAG](#indexing-data-with-graphrag)
- [Querying Data: Global Search](#querying-data-global-search)
- [Local Search Issue](#local-search-issue)
- [Fun with Data](#fun-with-data)
- [Contribution](#contribution)
- [License](#license)

## Introduction

GraphRAG is like the Marauder's Map 🗺️ of data science—it transforms unstructured text into a structured graph, revealing hidden connections and relationships. This project shows how to wield GraphRAG with Ollama and LM Studio, turning plain text into insightful graphs. We've even tested it with a few chapters from **Harry Potter and the Deathly Hallows: Part 1 (Chapters 2-7)** to keep the magic alive! ⚡📚

## Downloading and Setting Up Ollama & LM Studio

Before we begin our spellbinding journey, let's get our tools ready:

1. **Download Ollama** from [ollama.com](https://ollama.com).
2. **Download LM Studio** from [LM Studio](https://lmstudio.com).

In your terminal, cast the following spell to pull the Gemma 2 model:

```bash
ollama pull Gemma 2
```

Next, open LM Studio, search for the `nomic` embedding model, download it (84 MB), and configure your local server:

1. Open LM Studio and go to the model search.
2. Search for `nomic embed text`.
3. Download the model and note its path.
4. Start the server with the downloaded model.

## Configuring Models and Embeddings

To set up your magical workspace:

1. Start the LM Studio server with the embedding model and note the URL.
2. Note the Ollama server URL, which typically runs on port 11434.
3. Install GraphRAG in your terminal:

```bash
pip install graphRAG
```

4. Initialize GraphRAG:

```bash
python -m graph_rag.index --init --root .
```

5. Modify the `settings.yaml` file created in your root directory:

```yaml
model:
  name: "Gemma 2"
  api_base: "http://localhost:11434/v1"

embedding_model:
  path: "/path/to/nomic/embed/text"  # Use the path noted earlier
  quantized_version: "Q4"

chunk_size: 300
chunk_overlap: 100

base_directory: "./input"
```

## Indexing Data with GraphRAG

Place your text data in the `input` folder. For this demo, we've used chapters from **Harry Potter and the Deathly Hallows: Part 1**. To index the data, run:

```bash
python -m graph_rag.index --root .
```

This process converts unstructured data into a structured graph format. Expecto indexo! 🌟

## Querying Data: Global Search

Ask your indexed data questions using the global search method:

```bash
python -m graph_rag.query --root . --method global --query "What are the top themes in this story?"
```

The model will generate a response based on the indexed data. 🎤✨

## Local Search Issue

Currently, the local search feature might face compatibility issues.

## Fun with Data

We're currently working on building an entity graph from the indexed chapters of **Harry Potter and the Deathly Hallows: Part 1 (Chapters 2-7)**. Stay tuned for updates and join us on this enchanting adventure! 🧩🔮

## Contribution

We welcome contributions from fellow data wizards! Feel free to submit a Pull Request and join the fun. 🧙‍♂️🧙‍♀️

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
