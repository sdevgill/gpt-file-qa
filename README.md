# GPT File Q&A

This Python Notebook is designed to process text data, tokenize it, create embeddings, and build a question-answer system using the OpenAI GPT-3.5-turbo model. I mostly use it to transcribe video/podcasts with Whisper and ask questions to the transcription, pretty cool imo.

## Prerequisites

- Python >=3.11
- Poetry >=1.4.0

## Installation

0. Clone the repository and `cd` into it:

```bash
git clone git@github.com:sdevgill/gpt-file-qa.git && cd gpt-file-qa
```

1. Install the dependencies with Poetry:

```bash
poetry install
```

2. Copy the `.env.example` file to `.env` and fill in with your OpenAI API key:

```bash
cp .env.example .env
```

3. Run the Jupyter Notebook (or just use it within VSCode)

```bash
poetry run jupyter notebook
```

## Usage

You can modify the script to process different text files, adjust the maximum token count, or ask different questions to the question-answer system. To run the script, simply execute the notebook in a Jupyter environment. Make sure to add your text content in the text/file.txt file.

## Notebook Flow

1. Create Folders for Input and Processed Files: The script first creates two directories, text/ and processed/. The text/ directory is used to store .txt files that will be processed, and the processed/ directory is used to store processed data.

2. Text Files Processing: The script reads all .txt files from the text/ directory, processes them by removing unnecessary lines and characters, and then saves this processed data in a CSV file in the processed/ directory.

3. Tokenization: The script uses the tiktoken library to tokenize the processed text data. It counts the number of tokens in each text and provides a visual representation of the distribution of token count.

4. Splitting into Chunks: Texts that have a number of tokens greater than a specified maximum (500 by default) are split into smaller chunks to ensure the token limit is not exceeded.

5. Text Embeddings: The script uses the OpenAI API to create embeddings for each chunk of text and saves this data into a new CSV file in the processed/ directory.

6. Question Answer System: The script uses the embeddings to find the most similar context for a given question. It then uses the OpenAI ChatCompletion API to generate an answer based on the identified context. The answer is written to a .txt file in the processed/ directory.

## Notes

The model used for text embeddings and question answering is text-embedding-ada-002 and gpt-3.5-turbo respectively as of the date this README was created. You can use gpt-4 for better results, but it will cost you more.
