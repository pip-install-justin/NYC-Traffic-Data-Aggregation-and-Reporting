Section 1 : Kafka

Step 1: Install Kafka Locally
Kafka requires Java 8+. If you don’t have it installed, install it first.

1.1 Install Java (if not installed)
Check Java version:
java -version

If not installed, install Java:

Ubuntu/Debian:

sudo apt update
sudo apt install default-jdk -y

macOS (Homebrew):

brew install openjdk


1.2 Download and Extract Kafka
Download the latest Apache Kafka (binary version) from the official Kafka website.
Extract the downloaded tarball.

wget https://downloads.apache.org/kafka/3.6.0/kafka_2.13-3.6.0.tgz  (this can be skipped as i have alaredy added the kafka jar in the dir)
tar -xzf kafka_2.13-3.9.0.tgz
cd kafka_2.13-3.9.0

Step 2: Start Kafka and Zookeeper
Kafka requires Zookeeper for managing brokers. Start both Zookeeper and Kafka Server.

2.1 Start Zookeeper
Run the following command in the Kafka directory:

bin/zookeeper-server-start.sh config/zookeeper.properties
Keep this running in the background.

2.2 Start Kafka Broker
Open another terminal and start Kafka:

bin/kafka-server-start.sh config/server.properties
Kafka is now running on localhost:9092.

Step 3: Create a Kafka Topic
You need to create a Kafka topic to publish taxi trip data.

Open another terminal and execute below command: 

bin/kafka-topics.sh --create --topic nyc_taxi_topic --bootstrap-server localhost:9092 --partitions 3 --replication-factor 1
Confirm that the topic was created:

bin/kafka-topics.sh --list --bootstrap-server localhost:9092


Now, run the nyc-taxi.ipynb jupyter notebook

after that, run flask-api.ipynb first and then spark-structured-streaming.ipynb parallely

Finally, run the nyc-taxi_dag.ipynb to check the results ^_^