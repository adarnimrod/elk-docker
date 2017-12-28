ARG KIBANA_VERSION
FROM docker.elastic.co/kibana/kibana-oss:${KIBANA_VERSION}
ARG KIBANA_VERSION
ARG LOGTRAIL_VERSION
ENV KIBANA_VERSION ${KIBANA_VERSION}
ENV LOGTRAIL_VERSION ${LOGTRAIL_VERSION}
RUN ./bin/kibana-plugin install "https://github.com/sivasamyk/logtrail/releases/download/v${LOGTRAIL_VERSION}/logtrail-${KIBANA_VERSION}-${LOGTRAIL_VERSION}.zip"
COPY logtrail.json ./plugins/logtrail/logtrail.json
