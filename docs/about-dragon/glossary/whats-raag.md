---
description: >-
  Ever wanted to have a chat with a LLM (Large Language Model) like GPT-4o, but
  with the ability to ask it questions about your data? RaaG is the answer to
  your needs!
---

# What's RaaG?

{% hint style="info" %}
RaaG is the acronyme for "RAG as a GPT"
{% endhint %}

## Why do we need dRAGon RaaG? <a href="#why-do-we-need-dragon-raag" id="why-do-we-need-dragon-raag"></a>

You can already use LangChain or LlamaIndex to query your data, so why do you need RaaG?

As you know, a typical RAG application is composed of two main components with each several sub-tasks :

1. **Indexing**: This involves the offline process of ingesting data from a source and indexing it.
   1. **Load**: The data is loaded using Document Loaders.
   2. **Split**: The loaded data is divided into smaller chunks using Document Splitters.
   3. **Store**: The chunks are stored and indexed for future searching, typically utilizing a VectorStore and an Embeddings model.
2. **Retrieval and Generation**: This is the core RAG chain that operates during runtime, handling user queries.
   1. **Retrieve**: Relevant data chunks are fetched from the storage in response to a user query using a Retriever.
   2. **Generate**: A ChatModel/LLM generates an answer by incorporating the user query and the retrieved data into a prompt.

Let's say you want to build a RAG pipeline using LangChain: You would need to write code to handle each of these sub-tasks, which can be quite complex and time-consuming.

## How does dRAGon RaaG simplify the process? <a href="#how-does-dragon-raag-simplify-the-process" id="how-does-dragon-raag-simplify-the-process"></a>

So instead of having an app code like this:

```python
from langchain import hub
from langchain_postgres.vectorstores import PGVector
from langchain_community.document_loaders import WebBaseLoader
from langchain_core.output_parsers import StrOutputParser
from langchain_core.runnables import RunnablePassthrough
from langchain_openai import OpenAIEmbeddings
from langchain_text_splitters import RecursiveCharacterTextSplitter
from langchain_openai import ChatOpenAI

os.environ["OPENAI_API_KEY"] = "YOUR_API_KEY"

loader = WebBaseLoader(
    web_paths=("https://dragon.okinawa")
)
docs = loader.load()

text_splitter = RecursiveCharacterTextSplitter(chunk_size=500, chunk_overlap=50)
splits = text_splitter.split_documents(docs)

connection = "postgresql+psycopg://user:paswword@server:5433/vectors"
collection_name = "my_rag_chunks"
embeddings = OpenAIEmbeddings()

vectorstore = PGVector(
    embeddings=embeddings,
    collection_name=collection_name,
    connection=connection,
    use_jsonb=True,
)

retriever = vectorstore.as_retriever()
prompt = hub.pull("rlm/rag-prompt")

def format_docs(docs):
    return "\n\n".join(doc.page_content for doc in docs)

llm = ChatOpenAI(model="gpt-4o")

rag_chain = (
    {"context": retriever | format_docs, "question": RunnablePassthrough()}
    | prompt
    | llm
    | StrOutputParser()
)

rag_chain.invoke("What's dRAGon?")
```

You will simply use the following code with a dRAGon powered RAG pipeline:

```python
from langchain_openai import OpenAI

llm = OpenAI(
    model_name="your-dragon-raag-farm-name",
    openai_api_base="http://your.dragon.host:1985/api/raag/v1",
)

prompt = "What's dRAGon?"
llm.invoke(prompt)
```

dRAGon simplifies the process of building a RAG pipeline by providing a single interface to manage all these components by providing an OpenAI API compliant endpoint to interact with your RAG pipeline.

## Components involved in dRAGon RaaG <a href="#components-involved-in-dragon-raag" id="components-involved-in-dragon-raag"></a>

```mermaid
flowchart LR
    request[Chat Request] --> endpoint
    subgraph raag1 [RaaG]
        endpoint[OpenAI Compliant Endpoint] --> Router
        subgraph farm1 [Farm]
            Router-->SiloN
            Router-->GranaryN
            Aggregator
            click SiloN href "/about-dragon/glossary/whats-a-silo" "What's a Silo?"
            click GranaryN href "/about-dragon/glossary/whats-a-granary" "What's a Granary?"
        end
    end
    SiloN-->Aggregator
    GranaryN-->Aggregator
    Aggregator-->Response
```

## Tutorials

* [LangChain : Chat with a Farm](../../tutorials/raag-api/langchain-chat-with-a-farm.md)
* [FAQ : SQL Ingestor as a RAG Data Provider](../../tutorials/raag-api/faq-sql-ingestor-as-a-rag-data-provider.md)
