---
description: >-
  This entity is designed to store and retrieve chunks, the result of embeddings
  of documents. It is the basic building block of dRAGon.
---

# What's a Silo?

A Silo is composed of three main components :

```mermaid
flowchart LR
    subgraph silo1 [Silo]
    IngestorLoader
    EmbeddingModel
    VectorStore
    end
```

## How does it work?

The Ingestor Loader is responsible for loading the documents into the Silo : it can be done by reading files in a directory or by providing URLs.&#x20;

After the documents are loaded they are split into chunks (eg. paragraphs, sentences, etc.) by the Silo Splitter.&#x20;

Each chunk is then transformed into a vector by the Embedding Model, which is then stored in the Vector Store for later retrieval.

```mermaid
flowchart TB
    IngestorLoader-- Load files over file system, URLs, ... -->DocumentSplitter
    DocumentSplitter-- Split documents into chunks -->EmbeddingModel
    EmbeddingModel-- Vectorize each chunk for retrieval similarity -->VectorStore
```

## Diagrams

```mermaid
classDiagram
class Silo {
    +UUID uuid
    +String name
    +VectorStoreType vectorStore
    +EmbeddingModelType embeddingModel
    +IngestorLoaderType ingestorLoader
    +List~String~ vectorStoreSettings
    +List~String~ embeddingSettings
    +List~String~ ingestorSettings
}
class VectorStoreType {
    <<enumeration>>
    InMemoryEmbeddingStore
    PersistInMemoryEmbeddingStore
    PGVectorEmbeddingStore
}
Silo *-- VectorStoreType
class EmbeddingModelType {
    <<enumeration>>
    BgeSmallEnV15QuantizedEmbeddingModel
    OpenAiEmbeddingAda002Model
    OpenAiEmbedding3SmallModel
    OpenAiEmbedding3LargeModel
}
Silo *-- EmbeddingModelType
class IngestorLoaderType {
    <<enumeration>>
    None
    FileSystem
    URL
}
Silo *-- IngestorLoaderType
```

### VectorStoreSettings

#### PersistInMemoryEmbeddingStoreSettings

```mermaid
classDiagram
class PersistInMemoryEmbeddingStoreSettings {
  +int flushSecs
}
```

#### PGVectorEmbeddingStoreSettings

```mermaid
classDiagram
class PGVectorEmbeddingStoreSettings {
  +String host
  +Integer port
  +String database
  +String user
  +String password
}
```

### EmbeddingSettings

```mermaid
classDiagram
class EmbeddingSettings {
  +String apiKey
  +Integer chunkSize
  +Integer chunkOverlap
}
```

### IngestorSettings

#### DefaultIngestorLoaderSettings

```mermaid
classDiagram
class DefaultIngestorLoaderSettings {
  +String schedule
  +String timezone
  +Boolean indexNewDiscoveredDocuments
}
```
