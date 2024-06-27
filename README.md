
# BITSinfo

Answering BITS and BITSAT related queries using RAG LLM.

BITS (Birla Institute of Technology and Science) is a premier private institute of higher education in India. It is known for its engineering, science, and management programs and has campuses in Pilani, Goa, Hyderabad, and Dubai. BITSAT is the entrance examination for admission to the integrated first-degree programs at BITS campuses.

In this project, we try to answer different queries which student have every year regarding BITS and its admission procedure. For each question, a RAG-based implementation will first find the relevant information from the documents which BITS has provided and then pass them as context to an LLM to answer the queries. 

The project exposes an HTTP REST endpoint. It uses Pathway's LLM App features to build LLM-enabled data pipeline in Python and join data from the input sources, leverages Gemini API to generate responses.

Currently, the project uses a Google Drive Folder with all the necessary information sourced from the official BITSAT website.


## Demo

Here is a quick demo of the app.


## How to run the project
### Prerequisites
- Make sure Python is installed on your machine.
- Download and Install Pip to manage project packages.
- Create an Gemini account and generate a new API Key.
- git
- Docker Desktop: This tool allows you to run applications in isolated containers. Download Docker Desktop.



### Clone the repository

```bash
  git clone https://link-to-project
```

### Navigate to the project directory

```bash
  cd my-project
```

### Modify the `.env` file and put your Gemini API Key

```bash
  GEMINI_API_KEY=*******
```

### Build the Docker Image

```bash
  docker build -t BITSinfo .
```

### Run the Docker Container

```bash
  docker run -v "${PWD}/data:/app/data" -p 8000:8000 BITSinfo
```

### Check the List of Files

```bash
  curl -X 'POST'   'http://localhost:8000/v1/pw_list_documents'   -H 'accept: */*'   -H 'Content-Type: application/json'
```
This will return the list of files.

### Run the RAG service

```bash
  curl -X 'POST' \
  'http://0.0.0.0:8000/' \
  -H 'accept: */*' \
  -H 'Content-Type: application/json' \
  -d '{
  "prompt": "What are the different modes of admission in BITS?"
}'
```

## Further Improvements

There are more things we can achieve with this project:

- Provide an user-friendly UI with Streamlit.
- Incorporate additional data from the BITS official website.
- Reduce the response generation time.
