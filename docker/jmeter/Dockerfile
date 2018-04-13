FROM java:8-jre-alpine

#  Version
ENV   JMETER_VERSION  3.2

# Download and unarchive jmeter
RUN mkdir -p /opt && \
    wget -qO- http://apache.01link.hk//jmeter/binaries/apache-jmeter-${JMETER_VERSION}.tgz | tar xz -C /opt/ && \
    ln -s /opt/apache-jmeter-${JMETER_VERSION} /opt/jmeter 

# Set environment
ENV PATH ${PATH}:/opt/jmeter/bin

# Set working directory
WORKDIR /opt/jmeter/bin

CMD ["/bin/sh"]
