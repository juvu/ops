FROM arm32v7/openjdk:11-slim

EXPOSE 9200

RUN apt-get update && \
    apt-get install -y --no-install-recommends wget && \
    wget -q https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.4.2-linux-x86_64.tar.gz && \
    tar -xzf elasticsearch-7.4.2-linux-x86_64.tar.gz && \
    rm -rf elasticsearch-*.tar.gz && \
    rm -rf /var/lib/apt/lists/*

COPY elasticsearch.yml /elasticsearch-7.4.2/config/elasticsearch.yml
COPY jvm.options /elasticsearch-7.4.2/config/jvm.options

ENTRYPOINT ["./elasticsearch-7.4.2/bin/elasticsearch"]
