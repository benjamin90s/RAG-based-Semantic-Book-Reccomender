# 📚 Semantic Book Recommendation System

An AI-powered **semantic book recommender** that combines **Google Vertex AI embeddings**, **Chroma vector database**, and **RAG (Retrieval-Augmented Generation)** with **Gemini** to deliver personalized book recommendations.  
It enriches semantic search with **zero-shot genre classification (BART)** and **emotion analysis (DistilRoBERTa)** for **tone-based filtering**, and provides an interactive **Gradio dashboard** for natural language queries.  

---

## 🚀 Features

- **Semantic Search**: Finds books based on meaning, not just keywords, using Google Vertex AI embeddings + Chroma.  
- **Category Classification**: Uses zero-shot classification (BART) to predict Fiction/Nonfiction for missing genres.  
- **Emotion-Aware Recommendations**: Extracts dominant emotions (joy, fear, sadness, etc.) from book descriptions with DistilRoBERTa.  
- **RAG with Gemini**: Summarizes and justifies top recommendations using Vertex AI LLM.  
- **Interactive UI**: Built with Gradio for category filtering, tone-based ranking, and user-friendly book discovery.  

---

## 🗂️ Dataset

- Source: [7k+ Books with Metadata](https://www.kaggle.com/datasets/dylanjcastillo/7k-books-with-metadata)  
- Preprocessing:
  - Removed incomplete entries
  - Created `tagged_description` (ISBN + description)
  - Generated embeddings with Vertex AI
  - Added simplified categories + emotion scores  

---

## ⚙️ Tech Stack

- **Languages & Tools**: Python, Git  
- **Libraries**: Pandas, NumPy, Matplotlib, Seaborn, HuggingFace Transformers, LangChain, Gradio  
- **Models**:
  - `text-embedding-004` (Vertex AI embeddings)
  - `facebook/bart-large-mnli` (zero-shot classification)
  - `j-hartmann/emotion-english-distilroberta-base` (emotion analysis)
  - `gemini-2.0-flash` (LLM for RAG-based summaries)
- **Infrastructure**: Chroma (Vector DB), Google Cloud Vertex AI  

---

## 📊 Workflow

1. **Data Cleaning** → Remove missing fields, enrich metadata  
2. **Embedding Generation** → Vertex AI embeddings for descriptions  
3. **Vector Indexing** → Store in Chroma for semantic search  
4. **Category & Emotion Enrichment** → Zero-shot + DistilRoBERTa  
5. **Query Handling**:
   - Retrieve semantically similar books
   - Filter by category (Fiction/Nonfiction/Children’s etc.)
   - Rank by tone (Joy, Sadness, Fear, etc.)
6. **RAG** → Gemini generates a summary with justifications  
7. **UI** → Gradio dashboard for interactive recommendations  

---

## 🖼️ Demo

### Query Example  
> *"A book to teach children about nature"*  

- Returns relevant **Children’s Nonfiction** books  
- Sorts by tone if selected (e.g., “Happy” → joy score)  
- Gemini summarizes top 3 picks with short explanations  

*(Add screenshot of Gradio UI here)*

---

## 🔧 Installation

```bash
# Clone repo
git clone https://github.com/yourusername/semantic-book-recommender.git
cd semantic-book-recommender

# Install dependencies
pip install -r requirements.txt

# Run the app
python app.py
