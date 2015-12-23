FROM nikhilrp/java8

MAINTAINER nikhilrp <podduturi.nikhil@gmail.com>

RUN wget -q -O - http://mirror.vorboss.net/apache/zookeeper/zookeeper-3.4.7/zookeeper-3.4.7.tar.gz | tar -xzf - -C /opt
RUN mv /opt/zookeeper-3.4.7/conf/zoo_sample.cfg /opt/zookeeper-3.4.7/conf/zoo.cfg
RUN ln -s /opt/zookeeper-3.4.7 /opt/zookeeper

ENV JAVA_HOME /usr/lib/jvm/java-8-oracle
ENV ZK_HOME /opt/zookeeper
RUN sed  -i "s|/tmp/zookeeper|$ZK_HOME/data|g" $ZK_HOME/conf/zoo.cfg; mkdir $ZK_HOME/data

ADD start-zk.sh /usr/bin/start-zk.sh
EXPOSE 2181 2888 3888

WORKDIR /opt/zookeeper
VOLUME ["/opt/zookeeper/conf", "/opt/opt/zookeeper/data"]

CMD /usr/sbin/sshd && start-zk.sh
