# ML \- RAG \- PIPELINE

[NoteBook \- Link](https://colab.research.google.com/drive/10iPyqiON8b7flek0JoiTaZ9U8Bmtpa_y?usp=sharing)


## Summary

1. **Load Data**: The Hugging Face documentation dataset is loaded.  
2. **Chunking**: The documents are split into smaller chunks using a recursive character text splitter to manage context size.  
3. **Embedding**: The chunks are converted into numerical representations (embeddings) using a sentence transformer model (`thenlper/gte-small`). A FAISS index is created for efficient similarity search.  
4. **QA Generation and Evaluation Setup**: A prompt is defined to generate question-answer pairs from the document chunks. Critique prompts are set up to evaluate the generated questions based on groundedness, relevance, and standalone quality. A Gemini model is configured for these evaluations.  
5. **RAG Implementation**: A function `answer_with_rag` is defined to retrieve relevant document chunks based on a user query, optionally re-rank them, and then use a large language model ***(`mistralai/Mixtral-8x7B-Instruct-v0.1`)*** to generate an answer based on the retrieved context.  
6. **Evaluation**: The RAG pipeline is evaluated using a pre-defined evaluation dataset. The generated answers are compared to true answers and evaluated by the ***gemini-2.5-flash*** model based on correctness.  
7. **Analysis**: The evaluation results are aggregated and analyzed to compare the performance of different RAG configurations (though only one configuration was run in the notebook state).

In essence, the pipeline retrieves relevant document snippets for a given question and uses an LLM to synthesize an answer based on those snippets, aiming for more accurate and contextually relevant responses. 