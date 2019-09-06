FROM jenkins/jenkins:2.193-alpine

# 18.03.1-ce
ENV DOCKERVERSION=18.09.2
USER root
RUN curl -fsSLO https://download.docker.com/linux/static/stable/x86_64/docker-${DOCKERVERSION}.tgz \
  && tar xzvf docker-${DOCKERVERSION}.tgz --strip 1 \
                 -C /usr/local/bin docker/docker \
  && rm docker-${DOCKERVERSION}.tgz

COPY . /tmp/.

RUN \
  mv /tmp/executors.groovy \
     /usr/share/jenkins/ref/init.groovy.d/executors.groovy \
  && mv /tmp/entrypoint.sh /usr/local/bin/jentrypoint \
  && chmod +x /usr/local/bin/jentrypoint

USER jenkins

ENTRYPOINT ["sh", "/usr/local/bin/jentrypoint" ]