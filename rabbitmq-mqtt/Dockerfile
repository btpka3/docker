FROM rabbitmq:3.6.10-alpine

LABEL name="rabbitmq-mqtt"
LABEL maintainer="btpka3 <btpka3@163.com>"
LABEL version="0.2.0"
LABEL description="rabbitmq with mqtt"


RUN rabbitmq-plugins enable --offline rabbitmq_management   \
    && rabbitmq-plugins enable --offline rabbitmq_mqtt      \
    && rabbitmq-plugins enable --offline rabbitmq_web_mqtt  \
    && rabbitmq-plugins enable --offline rabbitmq_stomp

EXPOSE 15671 15672

EXPOSE 1883 8883

#RUN echo =====RABBITMQ_VERSION: ${RABBITMQ_VERSION}
#ADD https://dl.bintray.com/rabbitmq/community-plugins/rabbitmq_web_mqtt-3.6.x-14dae543.ez \
#    /usr/lib/rabbitmq/lib/rabbitmq_server-$RABBITMQ_VERSION/plugins/
#RUN chmod go+r /usr/lib/rabbitmq/lib/rabbitmq_server-$RABBITMQ_VERSION/plugins/rabbitmq_web_mqtt-3.6.x-14dae543.ez
#EXPOSE 15675

RUN rabbitmq-plugins enable --offline rabbitmq_web_mqtt