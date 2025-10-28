# Week 8 Homework: Batch Data Extraction

This week, your goal is to process the provided dataset of movie review data and extract the information specified below. 

## Instructions

### What To Do
First, **design a prompt** to get the information you want. 

Then, **write a command-line tool** to perform a batch request, it should have the following options:

Send Batch Request
1. Process the provided input file
2. Create a batch request to process each item with your prompt (see "Writing Your Prompt" below)
3. Sends the batch request to the OpenAI API
4. Saves the batch ID for later retrieval

Read Batch Result
1. Check status of batch
2. If batch is completed, retreive the results
3. Store results locally in a .jsonl file (you'll submit this later)

Process the Results 
1. Read the results (handling any errors, like poorly formed JSON, by writing a message to the console)
2. Convert results into a JSON array and output a single JSON file
3. Report the following metrics:
    * Which movie has the most reviews (or output "No duplicate reviews found")
    * The top 5 genres and how many reviews there were for each


### How To Do It
There's a guide here for how to process OpenAPI batch requests: https://platform.openai.com/docs/guides/batch

Note that the batch processor is _significantly_ asynchronous! As in, it may take _hours_ for the request to comlete. That's why the application is separated the way it is above.

The nice thing about batch requests is that they run when the load is lower, so they cost less... BUT that also means you may not get an immediate response. However, it's often fairly quick, so don't hestitate to check back in a few minutes.

#### The API Key
Use the API key from Moodle when sending your batch requests to OpenAI. 

#### The Data Set
We've provided a data set taken from this Kaggle data source: https://www.kaggle.com/datasets/lakshmi25npathi/imdb-dataset-of-50k-movie-reviews/data 

The original set was a CSV with only two columns. We removed the additional column you don't need and converted it to a .txt file. Each line is a single review, which should make your processing a lot simpler. NOTE: Each line starts and ends with "" from the original CSV structure, but that shouldn't really effect your prompt (might actually make it easier).

**You may use Generative AI as much as you want for writing this code** There is a lot of documentation out there for how to work with the Batch API, so use it to your advantage. This is 1-credit class. We don't want this to take forever :) but we do want you to be familiar with the process of making batch requests.

### Hints
* Batch processors use JSONL files, or JSON Lines, files. These are files with a **separate JSON object on each line**. 
* If you're having trouble with your JSONL file being marked as invalid format, here are some things to check:
    * Trailing newlines - Some systems are really picky about having an extra new line at the end, some REALLY don't want it. Try both.
    * Lines are too long - In some cases, really long lines will prevent the JSONL from parsing. This shouldn't be a problem (it takes a lot), but it's something to watch for if your prompt gets really long.


### Writing Your Prompt

The final result for each item in your batch should be in the following JSON format (each item is described below that):

```
{
    movie_name: <string>,
    recommended: <nullable boolean>,
    genre: <string>,
    your_interesting_fact: any
}
```

**Description of each item:**
* **movie_name**: The title of the movie. Not all reviews actually include this though, so for the ones that don't, use a null value. 
* **recommended**: Did the author of the review recommend the movie? This should be a tri-state boolean (true, false, null). Null should only be applied in the case where you really can't tell.
* **genre**: The genre of the movie being reviewed. Null should be applied when it's not evident from the review. 
* **your_interesting_fact**: Pick something you, as a movie viewer, would like to know before you watch a movie and see if you can extract it from the reviews. For example, trigger warnings (like the site: https://www.doesthedogdie.com/) or maybe you don't like long (or short movies) and want to get a feel for length. Whatever you choose, make sure at least some of the reviews can give you a result. 

## Reflection Questions
1. What was the most difficult part of this process?
1. What was the easiest?
1. What was most difficult and/or interesting about writing the prompt?
1. Thinking about a previous job or intership, or school work you've done at Rose, explain a situation in which you could use a similar tool.
1. How easy do you think it would be to generalize this tool to other data sets and prompts? Explain why.

## Submission Instructions
Zip up and submit the following to the Week 8 dropbox:

* reflection.md - A file containing your answers to the Reflection Questions
* prompt.md - A file containing your prompt
* result.jsonl - The result you got from the batch request
* final.json - The updated json after you parsed the jsonl file
* screenshot.png - A screenshot of the output from the Process the Results step
* code.zip - A zip file containing the code you used to do the batch requests

