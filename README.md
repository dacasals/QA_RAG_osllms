### Explore Open source LLM model + RAG for QA task.


#### Scraping data from a public website:
- Notebook [scrapper.ipynb](scrapper.ipynb) contains the recursive web-scraping code to extract available and public web content given a site URL.
- It supports web pages and pdf
- It starts with a link, and extracts the page text as well as metadata like URL, domain, language a year from the URL, date, and a list of hyperlinks.
- These hyperlinks are added to the queue to be processed.
- You can find a dataset scraped [here](https://drive.google.com/file/d/1GzSC4F0uGoHGcRHl9FEdvA3WLA7NIjvp/view?usp=drive_link).

#### Firt Rag appoach
- Check [notebook](qa_chatbot_thoughtworks.ipynb)
- Load a Mistral 7B model with quantization config.
- Compare base model answers vs a simple RAG version.
- As documents for RAG use the dataset created (text from Web and Pdfs) using public data extracted from https://www.thoughtworks.com, check the other notebook to see the scrapper.

  
##### Comments from this first  approach:
- Checking the sample generated at the end of the notebook, you can see that the RAG version reduces some hallucinations compared with the base mistral model.
- Also reduce the verbosity in the answer.
- The retriever strategy is very basic, it affects a lot the results.
The base model seems to be trained with data until 2022, so it fails for questions that involve more recent content, like the Rag topics, it supports the benefits of having a RAG strategy. But this should be compared with a fine-tuning approach.
- There is a bug in the model prediction because the batch call does not work, it is not using the extra GPU correctly.
- I am using LangChain, what about Llamaindex ? 
