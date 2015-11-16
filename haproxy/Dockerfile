FROM haproxy:1.6.2

RUN apt-get update && \
    apt-get install -y\
    python \
    python-pip

RUN pip install Jinja2
RUN touch /var/run/haproxy.pid

COPY haproxy.cfg /usr/local/etc/haproxy/haproxy.cfg
COPY private/* /usr/local/etc/haproxy/

CMD haproxy -D -f /usr/local/etc/haproxy/haproxy.cfg -p /var/run/haproxy.pid; while true; do sleep 60; done
