# Nereus

Nereus
A Distributed Stream Band Join System with Adaptive Range Partitioning

Stream band join querys all of the data from another stream within given range of each new tuple. Resource efficient band join relys on proper range partitioning. However, for static range partitioning, the data distribution of real-world is skewed. The skewness causes serious load skewness in many instances.

Nereus is a distributed stream band join system, ensuring a appropriate number of partitions and load balancing with low migration cost. Extensive experiment results reported for real-world datasets generated from consumer electronics show that Nereus greatly improve the system performance, compared to existing method.


## Building Nereus

Nereus source code is maintained using [Maven](http://maven.apache.org/). Generate the excutable jar by running

    mvn clean package

## Running Nereus

Nereus is built on top of [Storm](https://storm.apache.org/). After deploying a Storm cluster, you can launch BiStream by submitting its jar to the cluster. Please refer to Storm documents for how to [set up a Storm cluster](https://storm.apache.org/documentation/Setting-up-a-Storm-cluster.html) and [run topologies on a Storm cluster](https://storm.apache.org/documentation/Running-topologies-on-a-production-cluster.html).
Running 

    storm jar /home/join/Nereus/target/Nereus-1.0-SNAPSHOT.jar soj.biclique.KafkaTopology -n 40 -ks 1 -pr 100 -ps 100 -f1 4 -f2 4  -infile sorted_20161101  -wr 40000 -ws 40000 -tr 46000 -ts 46000 --s band -t 2 -nps 3 -ns 600 -mig -jump -conti -e1 50 -e2 50   
