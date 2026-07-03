# YouTube Transcript Summarizer using Hugging Face

## Project Overview
This project automatically extracts the transcript from a YouTube video and generates a concise summary using a Hugging Face Transformer model.

It is designed to help users quickly understand the main ideas of a video without watching it entirely.

## Features
- Extracts transcripts directly from YouTube videos.
- Supports English transcripts.
- Splits long transcripts into smaller chunks to handle model input limits.
- Summarizes each chunk individually.
- Combines all summaries into a final summarized output.
- Works with videos of different lengths.

## Project Workflow
- Extract the YouTube video ID.
- Download the transcript.
- Convert the transcript into plain text.
- Split the transcript into manageable chunks.
- Generate a summary for each chunk using the transformer model.
- Merge all summaries into a final summary.

## Technologies Used
- PyTorch
- youtube-transcript-api
- Python
- Hugging Face Transformers
- SentencePiece
- Kaggle Notebook

## Installation
Install the required libraries:  
```
pip install transformers torch youtube-transcript-api sentencepiece
```

## How It Works
### Step 1 — Extract the Video ID
The YouTube URL is parsed to retrieve the video ID.
Example:
```
https://www.youtube.com/watch?v=VIDEO_ID
```
put it in url:
```
    url = "https://www.youtube.com/watch?v=VIDEO_ID"
```

### Step 2 — Fetch the Transcript

The project uses the youtube-transcript-api package to download the video's transcript.

Example output:

Hello everyone...
Today we're going to learn...
Artificial Intelligence...

### Step 3 — Convert Transcript into Plain Text

All transcript segments are combined into one continuous string that can be processed by the summarization model.

### Step 4 — Split Long Transcripts

Transformer models have a maximum input length.

Instead of sending the entire transcript at once, the project automatically splits the transcript into smaller chunks.

Example:
```
Transcript
│
├── Chunk 1
├── Chunk 2
├── Chunk 3
└── Chunk 4
```
This prevents input-length errors and allows the project to summarize long videos efficiently.

### Step 5 — Summarize Each Chunk

Each chunk is summarized independently using the Hugging Face summarization pipeline.

Example:

Chunk 1  
↓  
Summary 1

Chunk 2  
↓  
Summary 2

### Step 6 — Merge the Summaries

Finally, all generated summaries are combined into one comprehensive summary representing the entire video.

Summary 1
+
Summary 2
+
Summary 3

↓  
Final Summary

## Future Improvements
- Support multilingual transcripts.
- Use token-based chunking instead of word-based chunking.
- Export summaries to Notepad or Word.
