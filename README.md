# PA_information_to_knowlegde_graph

![](assets/11.png)

## Project Overview

The project processes text documents about public administration procedures and regulations to extract entities, relationships and build a knowledge graph that can be queried and analyzed.

## Methodology

We propose a methodology to transform unstructured textual data into knowledge graphs (KGs) using the Llama 3.1 (8B) language model and the Neo4j graph database. This approach, inspired by resources like the GitHub project “GraphRAG-with-Llama-3.1,” focuses on an integrated, high-performance solution for extracting, structuring, and querying knowledge:

- **Entity and Relation Extraction**:  
  Llama 3.1 (8B) processes text segments to identify key entities (e.g., people, places, concepts) and the relationships linking them (e.g., “works for,” “lives in,” “caused by”), enriched with attributes such as confidence or causality.

- **Structured Integration in Neo4j**:  
  Extracted entity–relation–entity triplets are stored incrementally in Neo4j. As new data is analyzed, the graph updates continuously, allowing intuitive exploration of connections.

- **Natural Language Querying**:  
  Users ask questions in plain language (e.g., “Who works for company X?”). Llama 3.1 translates these queries into Cypher commands to retrieve information from Neo4j, enabling discovery of complex or unexpected relationships.

Centered on Llama 3.1 (8B) and Neo4j, this methodology delivers a robust, scalable way to handle unstructured data, turn it into actionable graphs, and query it effectively. It captures advanced contextual nuances while providing the flexibility and scalability needed for use cases such as healthcare, scientific research, and recommendation systems.

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

## Steps

### Setup

- Install necessary libraries like langchain, neo4j, and ollama.
- Configure and start the Ollama server to serve the LLaMA 3.1 language model.

### Data Processing

- Define classes to represent nodes, relationships, and documents within the graph.
- Process text documents, extracting entities and relationships using the LLaMA model.
- Serialize and save the extracted data in a JSON format.

### Graph Creation

- Load the serialized data and create GraphDocument objects.
- Connect to a Neo4j database and store the graph documents, including nodes, relationships, and source documents.
- Create a full-text index on the node IDs for efficient searching.

### Querying and Answering

- Implement a function to extract entities from user questions.
- Perform a full-text search in Neo4j to retrieve relevant nodes.
- Combine graph data with relevant vector data (if available) to provide a comprehensive context.
- Use the LLaMA model to generate answers based on the combined context.

## Guide

1. Install Required Packages.

   - Use "%pip install …" to install libraries like langchain, neo4j, tiktoken, etc.
   - Install pciutils with "!sudo apt-get install -y pciutils".
   - Install Ollama via "!curl -fsSL https://ollama.com/install.sh | sh".

2. Configure the Ollama API & Download the Model.

   - Set environment variables and run "ollama serve" in a new thread.
   - Pull the LLama 3.1 model with "!ollama pull llama3.1".

3. Define Classes for Nodes and Relationships.

   - Classes Node and Relationship store id/type/properties and link two nodes.
   - Documents hold metadata and page_content.
   - GraphDocument combines nodes, relationships, and document source.

4. Process and Serialize Documents into Graphs.

   - Use ChatOllama (model="llama3.1") for entity/relationship extraction.
   - Define a serialize_document function to convert objects to JSON.
   - Convert each document chunk into a GraphDocument, save progress to "progress.json".

5. Load and Transform JSON into GraphDocuments.

   - Read data from "progress.json".
   - Rebuild GraphDocuments (nodes, relationships, source document).

6. Configure Neo4j Connection and Add Documents.

   - Retrieve Neo4j URI, username, password from environment variables.
   - Create a GraphDatabase driver and a Neo4jGraph instance.
   - Add GraphDocuments using graph.add_graph_documents.

7. Create a Full-Text Index in Neo4j.

   - Run a Cypher query in a write transaction to build a full-text index.

8. Define Functions for Entity Extraction and Graph Retrieval.

   - extract_entities_from_text uses LLama to find entities.
   - graph_retriever runs full-text searches in Neo4j and retrieves relationships.

9. Build a Full Retriever and a Q&A Chain.

   - Combine graph data (graph_retriever) and vector data (vector_retriever).
   - Use a ChatPromptTemplate and chain them with the language model.

10. Run Q&A.

- Invoke the chain on a question.
- Display the final answer, showing references to “Graph data” or “Vector data”.
