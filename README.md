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

## Features
* Analysed ask price and bid price of our Forex data.
* Showing variation of volume of share has sold with respect to ‘Date’.
* Showing variation in opening and closing of shares with respect to ‘Date’.

## Getting Started
GitHub clone URL: https://github.com/rajib1007/Project_3.git
##### STEP: - 1

INSTALL REQUIRED TOOLS TO PROCEED WORK & SET PATH 

sudo apt-get install openjdk-8-jdk

wget https://dlcdn.apache.org/spark/spark-3.1.2/spark-3.1.2-bin-hadoop3.2.tgz

tar xvzf spark-3.1.2-bin-hadoop3.2.tgz

wget https://archive.apache.org/dist/kafka/2.0.0/kafka_2.11-2.0.0.tgz

tar xvzf kafka_2.11-2.0.0.tgz

##### STEP: - 2
FOLLOW THIS LINK INSTALL JUPYTER NOTEBOOK ON UBUNTU

https://www.digitalocean.com/community/tutorials/how-to-set-up-jupyter-notebook-with-python-3-on-ubuntu-20-04-and-connect-via-ssh-tunneling


##### STEP: - 3
GOTO KAFKA DIRECTORY AND RUN ZOOKEEPER AND KAFKA SERVER

cd kafka_2.11-2.0.0/

bin/zookeeper-server-start.sh config/zookeeper.properties

bin/kafka-server-start.sh config/server.properties

##### STEP: - 4
CREATE A TOPIC project3 WITH REPLICATION FACTOR 1 AND PARTITION 1

bin/kafka-topics.sh --create --zookeeper localhost:2181 --topic <topic name> --replication-factor 1 --partitions 1

##### STEP: - 5
CREATE A producer.py FILE TO FETCH DATA FROM API AND PASS TO TOPIC <topic name>
  
1. CREATE ACCOUNT ON api.tiingo.com
  
https://api.tiingo.com/
  
2. run producer.py file

##### STEP: - 6
  
START CONSUMER API IN NEW TERMINAL
  
bin/kafka-console-consumer.sh --topic <topic_name> --bootstrap-server localhost:9092

##### STEP: - 7
  
CREATE ANOTHER .py FILE TO STRUCTURE THE JSON DATA INTO SPARK DATAFRAME AND DO SOME OPERATION OR A USECASE
  
1.	CREATE TOPIC askPriceOutput 
  
bin/kafka-console-consumer.sh –topic <output_topic_file> --bootstrap-server localhost:9092
  
2.	usecase2.py

##### STEP: - 8
  
1.	GOTO SPARK BIN FOLDER
  
cd /spark-3.1.2-bin-hadoop3.2/bin/
  
2.	RUN SPARK-SUBMIT JOB WITH usecase.py FILE AND STORE THE OUTPUT ON askPriceOutput TOPIC
  
spark-submit --packages org.apache.spark:spark-sql-kafka-0-10_2.12:3.1.2 <file_path.py>

##### STEP: - 9
OUTPUT WILL BE SHOWING ON askPriceOutput TOPIC’S CONSUMER

##### STEP: - 10
OPEN JUPYTER NOTEBOOK AND INSTALL matplotlib library and kafka-python ON IT


## Contributers
 
* https://github.com/piyushgoyal1620
* https://github.com/Akhil-03
* https://github.com/GurramEswarNaidu
* https://github.com/6618karan
* https://github.com/20171CSE0103
* https://github.com/suleman804
* https://github.com/kanand2306
* https://github.com/kareemv46
* https://github.com/Trupti2502
  
## License
This project uses the following license: [<MIT License>](<https://github.com/rajib1007/Project_3/blob/main/LICENSE>).
