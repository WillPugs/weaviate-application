# weaviate-application
## William Pugsley

[Solution to Weaviate's Machine Learning Engineer Challenge.](https://weaviate.notion.site/Machine-Learning-Engineer-Challenge-f3bc639b111a43f0b72d186454b2d288). This solution addresses challenges 1 and 2.2 from the Notion.

We will explore the [LinkedIn job postings (2023-2024) dataset](https://www.kaggle.com/datasets/arshkon/linkedin-job-postings/) from Kaggle. The purpose of this project is to cluster job postings in the machine learning field. We will engineer useful data fields, add them to a Weaviate collection using Cohere embedding, and extract the job postings related to machine learning using semantic search.

The workflow.ipynb notebook is self-contained and has the entire workflow from start to finish. It begins by an exploration of the Kaggle dataset. The salary information comes in a variety of formats across different data points. We convert all this information into a standardized format (USD, yearly salary).

We then extract a subset of the fields. This is done to reduce the dataset's size and simplify the workflow. Which fields we choose is easily modifiable. We also drop any data points with missing values for any of these fields. We could replace these with default values, such as 0 for the salary and "null" for the job description, and add these points to the database anyways. We would then need to handle their presence when we query the database. For simplicity and given the limited computational resources available, we will just drop these values.

With this complete dataset, we can push the data points to a Weaviate collections instance. Since our data is processed, the schema can be implicitly defined when pushing the data points. We use Cohere embed-multilingual-v3.0 to vectorize the data.

Next, we simply query the database for job postings related to machine learning using semantic searching. We now have access to any job postings related to ML, or any other field we wish to query.

As a proof of concept, here are some graphs created using the data from the queried job postings:

![views_applies](https://github.com/WillPugs/weaviate-application/assets/70442267/47e3302d-a231-48a3-8b43-1eafb0d246a7)

![salary_bar_plot](https://github.com/WillPugs/weaviate-application/assets/70442267/2278ba71-32ae-4670-847d-e899d0903c0e)

![salary_histogram](https://github.com/WillPugs/weaviate-application/assets/70442267/9c462084-d357-4082-8d91-9f1a970c3ef8)


Requires the postings.csv file from Kaggle to be in the directory as well as a secrets.txt file containing API keys and database URLs.
