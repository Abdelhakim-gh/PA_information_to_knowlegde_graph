# PA_information_to_knowlegde_graph

![](assets/11.png)

## Project Overview

The project processes text documents about public administration procedures and regulations to extract entities, relationships and build a knowledge graph that can be queried and analyzed.

## Key Components

- Text document parsing and preprocessing
- Named entity recognition and relationship extraction
- Ontology extraction and data modeling
- Ontology transformation to graph data
- Ontology embedding
- Knowledge graph construction
- Neo4j graph database integration
- GraphWidget visualization
- RAG framework for question answering
- Question answering capabilities using LLM and graph data

## Technology Stack

- **Python**: The primary programming language used for scripting and data processing.
- **Langchain**: A library for building applications with language models.
- **Neo4j**: A graph database used to store and query the knowledge graph.
- **Ollama**: An API for serving and interacting with language models.
- **LLama 3.1 8b model**: A large language model used for natural language processing tasks.
- **mxbai-embed-large model**: A model used for generating embeddings.
- **Google Colab**: A cloud-based Jupyter notebook environment used for running the code.

## Architecture

![](assets/12.png)

## Project Structure

```bash
.
├── assets/
│   ├── *.png
│   └── AP_Rapport_KG.pdf
│
├── dataset/
│   ├── data.pdf
│   ├── data.txt
│   └── 10.png
│
├── neo4j/
│   ├── neo4j_query_table_data_2024-12-26.csv
│   └── neo4j_query_table_data_2024-12-26.json
│
├── enhancing_rag_with_graph.ipynb
├── KG.ipynb
├── progress.json
└── README.md
```

## Dataset

![](dataset/10.png)

- The document highlights the transition to digital procurement processes
  processes, improving efficiency and transparency.
- It establishes clear responsibilities for the various stakeholders involved in public
  public procurement, ensuring accountability.
- The emphasis on electronic bidding and reverse auctions reflects a modern
  modern approach to procurement, cutting red tape and simplifying
  simplifying processes.
- Strict eligibility criteria and evaluation processes are essential to ensure that public procurement
  that public procurement is competitive and fair.
- The document describes the procedural safeguards necessary to protect public funds
  and maintain the integrity of procurement decisions.
