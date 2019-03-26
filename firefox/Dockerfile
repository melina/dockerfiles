FROM debian:sid-slim

RUN apt-get update && apt-get install -y firefox && \
    rm -rf /var/lib/apt/lists/*
        

RUN mkdir -p /home/firefox && \
    groupadd -g 999 firefox && \
    useradd -r -u 999 -g firefox firefox && \
    chown 999:999 -R /home/firefox

USER firefox
ENV HOME /home/firefox

CMD ["/usr/bin/firefox"]
