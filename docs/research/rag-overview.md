# M1.1 Research — RAG Architecture

## What is RAG?
However, the ChatGPT can only respond to us based on its training, meaning it cannot give responses to our confidential documents or anything that was added after its training. Furthermore, ChatGPT can provide false and made-up responses when it does not have the actual knowledge to do so, known as hallucinations. This is where the role of RAG comes into play.

## Traditional LLM vs RAG
However, in case of this task, a larger problem is lack of access to private/new data. As users are supposed to upload their own confidential documents which have not been accessed by the LLM in its training phase, an ordinary LLM would fail to provide any answers since there is no way for it to be aware of the contents of those files. The issue of hallucination is present here as well; however, this is only a potential problem since it can be considered once the access issue has been resolved.
## RAG Ingestion Pipeline
1. Document Upload      → FastAPI (file upload endpoint receives the file from the user)
2. Text Extraction      → PyMuPDF (PDF), python-docx (DOCX), pandas (CSV), Python built-in file read (TXT)
3. Cleaning/Normalization → Plain Python (regex/string operations to strip whitespace, headers, footers)
4. Chunking              → LangChain text splitters (e.g. RecursiveCharacterTextSplitter)
5. Embedding Generation  → OpenAI Embeddings API (via langchain-openai)
6. Vector Store Indexing → ChromaDB