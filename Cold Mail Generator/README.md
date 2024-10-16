# Cold Email Generator Project

This project is a Cold Email Generator designed to streamline the process of extracting job postings from a website, querying relevant experience links from a portfolio, and crafting personalized cold emails to potential clients. The project leverages the LangChain framework and various AI components to automate these steps efficiently.

## Project Setup

The project installs necessary libraries and dependencies, including `langchain`, `langchain_groq`, and `chromadb`. Here’s a step-by-step breakdown of how the code functions:

### 1. **Language Model Initialization**

The code utilizes the `ChatGroq` model from LangChain, a large language model suited for versatile text generation. 

```python
from langchain_groq import ChatGroq

llm = ChatGroq(
    temperature=0, 
    groq_api_key='gsk_9j4Ef3Q0fqnT1PCue8aZwvT8', 
    model_name="llama-3.1-70b-versatile"
)
```

- The model is initialized with a fixed temperature for deterministic responses.
- An API key is specified for accessing the `Groq` service, allowing the model to generate responses.

### 2. **Data Extraction from a Webpage**

The project scrapes job listings from a specified URL using `WebBaseLoader`.

```python
from langchain_community.document_loaders import WebBaseLoader

loader = WebBaseLoader("https://careers.bat.com/job/bangladesh/expression-of-interest-territory-officer/27325/16749958016")
page_data = loader.load().pop().page_content
```

- This code extracts the HTML content from the job listing page, storing the text for further processing.

### 3. **Job Posting Extraction**

A `PromptTemplate` is used to extract specific details from the job posting, such as the role, required experience, skills, and description.

```python
from langchain_core.prompts import PromptTemplate

prompt_extract = PromptTemplate.from_template(
        """
        ### SCRAPED TEXT FROM WEBSITE:
        {page_data}
        ### INSTRUCTION:
        The scraped text is from the career's page of a website.
        Your job is to extract the job postings and return them in JSON format containing the 
        following keys: `role`, `experience`, `skills` and `description`.
        Only return the valid JSON.
        ### VALID JSON (NO PREAMBLE):    
        """
)
```

- This template processes the raw text and instructs the model to extract job-specific information in JSON format.
- The JSON parser converts the extracted text into structured JSON data for easier manipulation.

### 4. **Portfolio Querying and CSV Uploading**

The code then imports a CSV file containing the user’s portfolio and stores it in a vector database (`ChromaDB`). 

```python
import pandas as pd
from google.colab import files

uploaded = files.upload()
df = pd.read_csv(file_name)
```

- This code uploads the CSV file, reads it into a Pandas DataFrame, and iterates through the rows to add them to `ChromaDB`.
- The vector database enables efficient querying of experience links based on the job description.

### 5. **Querying Relevant Links from Portfolio**

The project sets up `ChromaDB` as a persistent client to store and retrieve relevant experience links based on the job requirements.

```python
import uuid
import chromadb

client = chromadb.PersistentClient('vectorstore')
collection = client.get_or_create_collection(name="portfolio")
```

- It checks if the portfolio collection is empty; if so, it populates it with documents (tech stack details) and metadata (links).
- Using a query, it retrieves the most relevant links to showcase the user's portfolio in relation to the job description.

### 6. **Cold Email Generation**

Finally, the extracted job description and the relevant links are used to generate a cold email with a customized message template.

```python
prompt_email = PromptTemplate.from_template(
        """
        ### JOB DESCRIPTION:
        {job_description}
        ### INSTRUCTION:
        You are Rafid, a business development executive at Dohatec. ...
        Do not provide a preamble.
        ### EMAIL (NO PREAMBLE):
        
        """
)
```

- This template outlines specific instructions for creating a cold email that highlights the capabilities of the company and links to relevant portfolio items.
- The generated email is then printed, providing a tailored outreach email that can be sent directly to the client.

## Conclusion

The Cold Email Generator Project efficiently automates the process of gathering job postings, querying relevant experience, and crafting a professional cold email. By leveraging LangChain’s language model capabilities and ChromaDB for vector storage, this project offers a streamlined solution for business development and outreach efforts.


## Learned from: 
https://www.youtube.com/watch?v=CO4E_9V6li0&list=PLeo1K3hjS3uvLuF4Tq1i1KqNM2QvIyzFK
