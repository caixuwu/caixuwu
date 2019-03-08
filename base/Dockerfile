FROM python:3.7.0-alpine3.8
LABEL mantainer="caixuwu <caixuwu@outlook.cn>"

ADD requirements /usr/local/
ADD base/hadoop_conf/hadoop /usr/local/

RUN apt-get update \
    && apt-get install -y --no-install-recommends openjdk-9-jdk-headless make g++ git \
    && cd /usr/local/ \
    && curl -sSL http://mirrors.tuna.tsinghua.edu.cn/apache/spark/spark-2.4.0/spark-2.4.0-bin-hadoop2.7.tgz -o spark.tar \
    && curl -sSL http://mirrors.tuna.tsinghua.edu.cn/apache/hadoop/common/hadoop-2.7.7/hadoop-2.7.7-src.tar.gz -o hadoop.tar.gz \
    && tar zxf java.tar.gz . \
    && tar zxf spark.tar . \
    && tar zxf hadoop.tar.gz . \
    && mv /usr/local/hadoop /usr/local/hadoop/etc
    && mv /usr/local/conf /usr/local/spark
#    && git clone --recursive https://github.com/dmlc/xgboost
    && pip --no-cache-dir install -r /usr/local/requirements \
    && apt-get purge -y --auto-remove git make \
    && rm java.tar.gz \
    && rm spark.tar \
    && rm hadoop.tar.gz

ENV SPARK_HOME /usr/local/spark
ENV PYSPARK_PYTHON python3
ENV HADOOP_HOME /usr/local/hadoop
#ENV SCALA_HOME=/Users/caixuwu/scala-2.10.7
#ENV PYTHON_HOME /Users/caixuwu/anaconda3
#ENV JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_40.jdk/Contents/Home
ENV SPARK_MASTER_IP localhost
ENV SPARK_WORKER_MEMORY 1000m
ENV SPARK_DIST_CLASSPATH $(/usr/local/hadoop/bin/hadoop classpath)
ENV HADOOP_CONF_DIR /usr/local/hadoop/etc/hadoop
ENV YARN_CONF_DIR /usr/local/hadoop/etc/hadoop
ENV PYSPARK_DRIVER_PYTHON python3
