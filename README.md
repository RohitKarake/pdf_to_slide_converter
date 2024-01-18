### Notebook to convert pdf into slides

## Following are the challenges that are addressed in the provided notebook:

```
1. The first challenge is that we want to create slides for different sections of the paper hence we can't use a readily available text summarization model over the entire pdf.
2. The title generation for each section should be relevant to the content of that slide
3. We should use Extractive Summarization as it gives the most important sentences from the given text whereas Abstractive Summarization can give irrelevant output sometimes.
Also, for Abstractive models to work well, it need to understand the context of the given data, which will be done by fine-tuning such models whereas Extractive Models preserve original content. For long documents, it is always a better practice to summarize the text using the Extractive method and then apply Abstractive to the results as Abstractive models have a limitation on the length of the input tokens.
4. Figure extraction and finding its position for the relevant slide.
5. Generation of bullet points for the summarized content.

```

# In this notebook for the problem statement of pdf to slide generation following procedure is followed:

- Convert pdf into XML file using Grobid
- Extract title, headers, and text section-wise from XML file
- Text processing
- Extractive Summarization using BERT Summarizer
- Predict the title from the summarized text for that section using the Flan-T5 base model
- Combine all the text into a single object for evaluation
- Extract titles and content from the reference ppt of the paper from kaggle dataset
- Perform Evaluation using Rouge Score
- Create slides from the summarized data and titles
- Create a final function that will take file_path as input and give ppt as the output
- Check by uploading the file and checking the reference.pptx file after using the above function