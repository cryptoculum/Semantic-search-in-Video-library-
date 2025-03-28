# Video Transcript Search with FAISS and Cross-Encoder Re-ranking

This project is designed to search and retrieve relevant video transcript segments using a combination of FAISS for efficient search and a Hugging Face cross-encoder for improved ranking.

## Features
- Uses FAISS for fast similarity search across video transcript embeddings.
- Incorporates a cross-encoder model for re-ranking results and improving search relevance.
- Filters results to include only video transcript data (not additional reference text).
- Provides clear search result formatting, including timestamps and video references.

## Project Structure
```
/Transcript/youtube
├── build_faiss_index.py      # Builds the FAISS index from embeddings
├── create_metadata.py        # Generates metadata from transcripts and text files
├── generate_embeddings.py    # Generates embeddings using SentenceTransformer
├── query_faiss.py            # Queries the FAISS index with improved re-ranking
├── metadata.json             # Metadata file containing transcript details
├── embeddings.json           # Embeddings file used for FAISS search
├── faiss_index.index         # The FAISS index file
├── youtube text/             # Folder containing additional text data
└── json/                     # Folder containing video transcript JSON files
```

## Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/video-transcript-search.git
cd video-transcript-search
```

### 2. Install Dependencies
```bash
pip install faiss-cpu sentence-transformers torch
```

### 3. Generate Metadata
```bash
python create_metadata.py
```

### 4. Generate Embeddings
```bash
python generate_embeddings.py
```

### 5. Build FAISS Index
```bash
python build_faiss_index.py
```

### 6. Run Search with Enhanced Ranking
```bash
python query_faiss.py
```

## How to Use
- When prompted in `query_faiss.py`, enter your search query (e.g., `talk about woman`).
- The system will return the most relevant transcript entries along with:
  - **Rank** (sorted by relevance)
  - **Video ID** (for reference)
  - **Start/End Time** (for precise location in the video)
  - **Transcript Text**

### Example Output
```
Search Results:
==================================================
Rank: 1
Video: video12345
Time: 00:05:12 - 00:05:30
Text: The speaker highlights the importance of empowering women in society.
Distance: 0.2534
--------------------------------------------------
Rank: 2
Video: video54321
Time: 00:12:00 - 00:12:25
Text: The conversation explores the role of women in leadership.
Distance: 0.2741
--------------------------------------------------
```

## Improving Search Results
- For better results, we've added a re-ranking method using a Hugging Face cross-encoder model.
- This helps refine the top search results by evaluating their relevance in more detail.

## Future Improvements
- Introducing keyword-based metadata for enhanced filtering.
- Implementing fuzzy search to match partial or less precise queries.
- Adding a web-based UI for easier search interface.

## Contributions
Contributions are welcome! Feel free to fork the repository, open issues, or submit pull requests.

## License
This project is licensed under the MIT License.

