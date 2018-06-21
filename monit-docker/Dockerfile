FROM centos:7

LABEL MAINTAINER="Hongbo LU <gitawego@gmail.com>"

# Compile and install monit and confd
ENV MONIT_VERSION=5.25.2 \
	MONIT_HOME=/opt/monit \
	MONIT_URL=https://mmonit.com/monit/dist \
	SERVICE_VOLUME=/opt/tools \
	PATH=$PATH:/opt/monit/bin
ENV MONIT_NAME=monit-${MONIT_VERSION}
ENV MONIT_FILENAME=${MONIT_NAME}-linux-x64.tar.gz

# Compile and install monit
RUN curl -k -o ${MONIT_FILENAME} ${MONIT_URL}/binary/${MONIT_VERSION}/${MONIT_FILENAME} \
	&& tar xf ${MONIT_FILENAME} \
	&& rm -f ${MONIT_FILENAME} \
	&& mv ${MONIT_NAME} ${MONIT_HOME} \
	&& mkdir -p ${MONIT_HOME}/log/

COPY ./start.sh ${MONIT_HOME}/bin/
RUN chmod +x ${MONIT_HOME}/bin/start.sh
ENTRYPOINT ["/bin/bash","-c","${MONIT_HOME}/bin/start.sh"]
