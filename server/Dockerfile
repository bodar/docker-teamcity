# docker run -dt -p 8111:8111 bodar/teamcity-server

FROM bodar/teamcity-base

RUN curl -Lk https://download.jetbrains.com/teamcity/TeamCity-9.1.6.tar.gz | \
  tar -C /opt -xz

ENV TEAMCITY_SERVER_MEM_OPTS -Xmx1G -Xms1G -XX:MaxMetaspaceSize=256m 
ENV TEAMCITY_SERVER_OPTS -XX:+UseParNewGC -XX:+UseConcMarkSweepGC -XX:+CMSClassUnloadingEnabled -XX:OnOutOfMemoryError=\"kill -9 %p\" -Dsun.net.inetaddr.ttl=60
ENV TEAMCITY_DATA_PATH /data/BuildServer
VOLUME ${TEAMCITY_DATA_PATH}

EXPOSE 8111

RUN mkdir -p ${TEAMCITY_DATA_PATH}/lib/jdbc && \
  cd ${TEAMCITY_DATA_PATH}/lib/jdbc && \
  wget --timeout=1 https://jdbc.postgresql.org/download/postgresql-9.4.1208.jar

COPY database.properties.template run /opt/TeamCity/

CMD bash /opt/TeamCity/run
