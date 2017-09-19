# pipeline-performance-case-study
A case study on the performance of an NLP pipeline

## Context
I have to gain more insight into the performance of an NLP pipeline. 

### The pipeline 
The pipeline consists of several _processors_ that each perform a specific task on the document, then store and send the result to the next processor. They use message queues to communicate between the processors: each processor has its own queue. Multiple instances can be launched for each processor. Together, these will consume the messages in parallel.

### A first experiment 
Log files of a run of 10,000 text fields through the pipeline are present in log_data.csv. These hold a summary of each review's journey through the pipeline: when each review was picked up by a processor and when the processor was finished with that review.

### Analysis
I want to understand the performance of the pipeline, identify weaknesses/inefficiencies, and suggest possible improvements. While the individual processors are optimized to some degree, I do not have much insight on the performance of the pipeline as a whole, under a load of data. Even preliminary metrics like _average time per processor_ are interesting.

## Data
A description of the fields in log_data.csv is provided below:

* ```review_id```: Unique identifier of the review.
* ```processor```: Name of the processor.
* ```finished_at```: Timestamp of the end processing time.
* ```started_at```: Timestamp of the start processing time.
* ```duration```: Processing time (in ms) of the review.
* ```character_count```: Number of characters in the review.
