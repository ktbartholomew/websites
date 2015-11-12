FROM haproxy:1.6.1

RUN apt-get update && \
    apt-get install -y\
    python \
    python-pip

RUN pip install Jinja2
RUN touch /var/run/haproxy.pid

COPY haproxy.cfg /usr/local/etc/haproxy/haproxy.cfg

CMD haproxy -D -f /usr/local/etc/haproxy/haproxy.cfg -p /var/run/haproxy.pid; while true; do sleep 60; done
