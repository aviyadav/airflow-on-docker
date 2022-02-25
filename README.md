# airflow-on-docker

## docker-steps
>>>>

curl -LfO 'https://airflow.apache.org/docs/apache-airflow/2.1.2/docker-compose.yaml'

- mkdir -p ./dags ./logs ./plugins

- echo -e "AIRFLOW_UID=$(id -u)\nAIRFLOW_GID=0" > .env

- for windows hardcode the AIRFLOW_GID=5000

## [init]

- docker-compose up airflow-init


## [run]

- docker-compose up

  docker-compose run airflow-worker airflow info >>> airflow & airflow

## [URL]

http://localhost:8090

  airflow/airflow

## [TEST - WORKER CLI]

  airflow tasks test <dag_name> <task_name> <date_in_the_past>
  
  
	1. airflow tasks test first_airflow_dag get_datetime 2022-2-1

	2. airflow tasks test first_airflow_dag process_datetime 2022-2-1
	
	# create variables:
		 Admin — Variables
		 key: first_dag_csv_path
		 value: data/datetimes.csv

	(create the data folder in the landing folder in docker -- worker CLI)

	3. airflow tasks test first_airflow_dag save_datetime 2022-2-1
