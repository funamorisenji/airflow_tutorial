# airflow_tutorial
--- 

A tutorial for get start on Apache Airflow by [Serps
aipong Navanuraksa](https://github.com/funamorisenji)

In this repository, I will show you how to get start on [Apache Airflow](https://airflow.apache.org/). I will use [Docker](https://www.docker.com/) to run [Airflow](https://airflow.apache.org/) and PostgreSQL. I will also show you how to create a simple DAG and run it.

[Apache Airflow](https://airflow.apache.org/) is an open-source platform for authoring, scheduling and monitoring data and computing workflows. First developed by [Airbnb](https://www.airbnb.com/), it is now under the [Apache Software Foundation](https://apache.org/). [Airflow](https://airflow.apache.org/) uses [Python](https://www.python.org/) to create workflows that can be easily scheduled and monitored. [Airflow](https://airflow.apache.org/) can run anything—it is completely agnostic to what you are running.

Benefits of [Apache Airflow](https://airflow.apache.org/) include:

- Ease of use—you only need a little python knowledge to get started.
- Open-source community—Airflow is free and has a large community of active users.
- Integrations—ready-to-use operators allow you to integrate Airflow with cloud platforms (Google, AWS, Azure, etc).
- Coding with standard Python—you can create flexible workflows using Python with no knowledge of additional technologies or frameworks.
- Graphical UI—monitor and manage workflows, check the status of ongoing and completed tasks.


First, you should understand the architecture of [Apache Airflow](https://airflow.apache.org/).

## Airflow Architecuture
--- 

![airflow_architecture.png](document%2Fimages%2Fairflow_architecture.png)

[Apache Airflow](https://airflow.apache.org/) consists of 3 main components.
- Web Server
- Scheduler
- Worker

The Airflow platform lets you build and run workflows, which are represented as Directed Acyclic Graphs (DAGs). A sample DAG is shown in the diagram below.

![DAGs-example.png](document%2Fimages%2FDAGs-example.png)

A DAG contains Tasks (action items) and specifies the dependencies between them and the order in which they are executed. A Scheduler handles scheduled workflows and submits Tasks to the Executor, which runs them. The Executor pushes tasks to workers.

Other typical components of an Airflow architecture include a database to store state metadata, a web server used to inspect and debug Tasks and DAGs, and a folder containing the DAG files.

![airflow-architecture-2.png](document%2Fimages%2Fairflow-architecture-2.png)

To get start with [Apache Airflow](https://airflow.apache.org/), I will use [Docker](https://www.docker.com/) to run it.

## Docker Compose 
--- 
I will use Docker Compose to run Airflow and PostgreSQL. You can see the `docker-compose.yaml` file in this [link](https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html) or go to folder `script/docker-compose.yaml` which is curretly newest for now (2024-01-15).

After you using `curl` to download the `docker-compose.yaml` file, you can run the following command to start Airflow and PostgreSQL.

```zsh
docker-compose up -d 
```

All the service should be start following. 

![docker-compose](document/images/docker-ps-check-container.png)

You can access web UI by using the following this [URL](http://localhost:8080/login/).

![apache-airflow-web-ui.png](document%2Fimages%2Fapache-airflow-web-ui.png)

Please enter the username and password as `airflow` and `airflow` respectively.

![airflow-web-ui-with-example-dag.png](document%2Fimages%2Fairflow-web-ui-with-example-dag.png)

_Note_: 
- You can see the example DAG in the web UI.
- You can turn off the example DAG by edit the `docker-compose.yaml` file. You can see the example DAG in the web UI.

```yaml
  airflow:
    image: ${AIRFLOW_IMAGE_NAME:-apache/airflow:2.1.2}
    environment:
      - AIRFLOW__CORE__LOAD_EXAMPLES=False
```


If you want to stop the service, you can run the following command.

```zsh
docker-compose down
```

## Known Issue
--- 
This is the known issue that I found when I try to run Airflow with Docker Compose (which I will try to fix it / update more issue later). 


### It's not working well with [Poetry](https://python-poetry.org/)
--- 





## Reference 
--- 
- [Apache Airflow](https://airflow.apache.org/)
- [Airflow Tutorial](https://airflow.apache.org/docs/apache-airflow/stable/tutorial.html)
- [Airflow Docker](https://airflow.apache.org/docs/apache-airflow/stable/start/docker.html)
- [Airflow Docker Compose](https://airflow.apache.org/docs/apache-airflow/stable/start/docker-compose.html)
- [Airflow GitHub](https://github.com/apache/airflow)
- [Airflow Use Case, Architecture, and best practice](https://www.run.ai/guides/machine-learning-operations/apache-airflow#Airflow-Architecture)
- 
