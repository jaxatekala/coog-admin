FROM java:jre

ENV PDI_RELEASE=7.1 \
	PDI_VERSION=7.1.0.0-12 \
	PDI_HOME=/opt/pentaho-di \
	KETTLE_HOME=/pentaho-di 

RUN curl -L -o /tmp/pdi-ce-${PDI_VERSION}.zip http://downloads.sourceforge.net/project/pentaho/Data%20Integration/${PDI_RELEASE}/pdi-ce-${PDI_VERSION}.zip \
	&& unzip -q /tmp/pdi-ce-${PDI_VERSION}.zip -d $PDI_HOME \
	&& rm /tmp/pdi-ce-${PDI_VERSION}.zip

RUN apt-get -qq update 

RUN apt-get -y install postgresql-client-9.4

ENV PATH=$PDI_HOME/data-integration:$PATH

COPY dist/coog-bi/ETL $KETTLE_HOME/ETL
COPY dist/coog-bi/kettle $KETTLE_HOME/.kettle

COPY ep /ep

ENTRYPOINT ["/ep"]
