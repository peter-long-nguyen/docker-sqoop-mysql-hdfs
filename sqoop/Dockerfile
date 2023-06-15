FROM dvoros/hadoop:3.1.0
MAINTAINER dvoros

USER root

ENV SQOOP_HOME /usr/local/sqoop

RUN curl -s https://archive.apache.org/dist/sqoop/1.4.7/sqoop-1.4.7.bin__hadoop-2.6.0.tar.gz | tar -xz -C /usr/local
RUN ln -s /usr/local/sqoop-1.4.7.bin__hadoop-2.6.0 $SQOOP_HOME

RUN mkdir -p /jdbc
COPY mysql-connector-j-8.0.33.tar.gz /jdbc/mysql-connector-j-8.0.33.tar.gz

RUN tar -xvf /jdbc/mysql-connector-j-8.0.33.tar.gz -C /jdbc \
    && rm /jdbc/mysql-connector-j-8.0.33.tar.gz \
    && mv /jdbc/mysql-connector-j-8.0.33/mysql-connector-j-8.0.33.jar $SQOOP_HOME/lib/ \
    && rm -rf /jdbc/mysql-connector-j-8.0.33/

ENV HADOOP_HOME=/usr/local/hadoop
ENV HADOOP_MAPRED_HOME=$HADOOP_HOME
ENV HADOOP_COMMON_HOME=$HADOOP_HOME
ENV HADOOP_HDFS_HOME=$HADOOP_HOME
ENV YARN_HOME=$HADOOP_HOME
ENV HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native

ENV PATH $PATH:$HADOOP_HOME/bin:$SQOOP_HOME/bin:$HADOOP_HOME/sbin:$HADOOP_HOME/bin

COPY bootstrap.sh /etc/bootstrap.sh
RUN chown root.root /etc/bootstrap.sh
RUN chmod 700 /etc/bootstrap.sh

CMD ["/etc/bootstrap.sh"]