# EDA-Netflix-Dataset-using-PySpark-on-Docker
This project demonstrates how to perform Exploratory Data Analysis (EDA) on the Netflix dataset using PySpark in a Jupyter Notebook environment. It involves setting up Spark, loading a dataset, performing basic data cleaning, and visualizing the results. All of it is runnning on a container in Docker.
##  How Does it Work?

1. Install Jupyter notebook. 

2. Install Docker Desktop.

### Download The Dataset

3. Download the "Netflix Movies and TV Shows" csv file for EDA:
```bash
https://www.kaggle.com/datasets/shivamb/netflix-shows 
```

### Pull Jupyter pyspark notebook Image

4. Pull "jupyter pyspark notebook" image from the following command:

```bash
docker pull jupyter/pyspark-notebook
```

### Run the PySpark Container with VS Code Integration

5. Start the container and access the PySpark shell on a Container using Docker:

```bash
docker run -p 8888:8888 -p 4040:4040 -v C:\Users\user\Desktop\EDA:/home/jovyan/work --name pyspark_container jupyter/pyspark-notebook
```

6. After running this command links will be present at the end, copy it and run it on your browser. Links will look like this:

```bash
http://localhost:8888/?token=your-token
```
and

```bash
http://localhost:4040/?token=your-token
```

-p 8888:8888: Maps the Jupyter Notebook port (if needed).

-p 4040:4040: Maps the Spark Web UI port.

-v C:\Users\user\Desktop\EDA:/home/jovyan/work: Shares your local folder with the container.

--name pyspark_container: Assigns a name to the container.

7. Open the Jupyter Notebook from the Link in the browser.

### Load the Dataset in pyspark in Jupyter Notebook

8. Once the dataset is accessible inside the Docker container, use the following PySpark code to load it:

```bash
# Import required libraries
from pyspark.sql import SparkSession

# Initialize Spark session
spark = SparkSession.builder.master("local").appName("Netflix EDA").getOrCreate()

# Load the dataset
df = spark.read.csv("/datasets/netflix.csv", header=True, inferSchema=True)

# Show the first few rows
df.show()
```

### Perform EDA

9. EDA is performed on the Dataset in the ipynb file uploaded.

10. After performing EDA upload it on Github.
