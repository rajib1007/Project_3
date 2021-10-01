# STOCK DATA STREAMING AND ANALYSIS

## DESCRIPTION
This project is basically for collecting  enormous data and analysing it. It includes live streaming of data from FOREX trading API and Electric Vehicle stocks API. The data is fetched and processed using REST API, Kafka Streaming and Spark streaming.Troughout this project stocks of Forex data and Electric Vehicle parts making companies data were analysed, and business use cases were implemented. The analysed data is then visualized by plotting different graphs using python libraries.

## TECHNOLOGIES USED:
* Python 3.9
* Kafka 2.8.0
* Spark 3.1.2
* Pyspark
* kafka-python 
* matplotlib

# Features
* Analysed ask price and bid price of our Forex data.
* Showing variation of volume of share has sold with respect to ‘Date’.
* Showing variation in opening and closing of shares with respect to ‘Date’.

# Getting Started

* STEP: - 1

INSTALL REQUIRED TOOLS TO PROCEED WORK & SET PATH 

sudo apt-get install openjdk-8-jdk
wget https://dlcdn.apache.org/spark/spark-3.1.2/spark-3.1.2-bin-hadoop3.2.tgz
tar xvzf spark-3.1.2-bin-hadoop3.2.tgz
wget https://archive.apache.org/dist/kafka/2.0.0/kafka_2.11-2.0.0.tgz
tar xvzf kafka_2.11-2.0.0.tgz

* STEP: - 2
FOLLOW THIS LINK INSTALL JUPYTER NOTEBOOK ON UBUNTU
https://www.digitalocean.com/community/tutorials/how-to-set-up-jupyter-notebook-with-python-3-on-ubuntu-20-04-and-connect-via-ssh-tunneling


* STEP: - 3
GOTO KAFKA DIRECTORY AND RUN ZOOKEEPER AND KAFKA SERVER

cd kafka_2.11-2.0.0/

bin/zookeeper-server-start.sh config/zookeeper.properties
![image](https://user-images.githubusercontent.com/63140467/135638690-8d7bc0f0-3f8b-4d16-8c43-43992a3c6abe.png)

bin/kafka-server-start.sh config/server.properties
![image](https://user-images.githubusercontent.com/63140467/135638729-012be315-054d-4cec-a874-3b3302398ff4.png)
  
* STEP: - 4
CREATE A TOPIC project3 WITH REPLICATION FACTOR 1 AND PARTITION 1

bin/kafka-topics.sh --create --zookeeper localhost:2181 --topic <topic name> --replication-factor 1 --partitions 1

* STEP: - 5
CREATE A producer.py FILE TO FETCH DATA FROM API AND PASS TO TOPIC <topic name>
  
1. CREATE ACCOUNT ON api.tiingo.com
https://api.tiingo.com/
  
2. run producer.py file
![image](https://user-images.githubusercontent.com/63140467/135638922-fbbf53a8-c1b6-4321-a2d1-85f137a76aa2.png)

*  STEP: - 6
START CONSUMER API IN NEW TERMINAL
  
bin/kafka-console-consumer.sh --topic project3 --bootstrap-server localhost:9092
 
![image](https://user-images.githubusercontent.com/63140467/135639264-5bffbfaf-3b2e-4f1e-a926-17cdbfe109b7.png)

* STEP: - 7
  
CREATE ANOTHER .py FILE TO STRUCTURE THE JSON DATA INTO SPARK DATAFRAME AND DO SOME OPERATION OR A USECASE
  
1.	CREATE TOPIC askPriceOutput 
  
bin/kafka-console-consumer.sh –topic askPriceOutput --bootstrap-server localhost:9092
  
2.	usecase2.py

* STEP: - 8
1.	GOTO SPARK BIN FOLDER
  
cd /spark-3.1.2-bin-hadoop3.2/bin/
  
2.	RUN SPARK-SUBMIT JOB WITH usecase.py FILE AND STORE THE OUTPUT ON askPriceOutput TOPIC
  
spark-submit --packages org.apache.spark:spark-sql-kafka-0-10_2.12:3.1.2 /home/ubuntu/Desktop/usecase2.py
![image](https://user-images.githubusercontent.com/63140467/135639620-80df8cf4-ed3b-4821-b74b-b30e499fa8b9.png)

* STEP: - 9
OUTPUT WILL BE SHOWING ON askPriceOutput TOPIC’S CONSUMER
![image](https://user-images.githubusercontent.com/63140467/135639687-7a1d018c-2b42-4e03-a019-d29ca00300c2.png)


* STEP: - 10
OPEN JUPYTER NOTEBOOK AND INSTALL matplotlib library and kafka-python ON IT


