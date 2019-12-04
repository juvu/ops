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

RUN elasticsearch-plugin install -b https://github.com/medcl/elasticsearch-analysis-ik/releases/download/v7.2.0/elasticsearch-analysis-ik-7.2.0.zip
RUN elasticsearch-plugin install -b https://github.com/medcl/elasticsearch-analysis-pinyin/releases/download/v7.2.0/elasticsearch-analysis-pinyin-7.2.0.zip

ENTRYPOINT ["./elasticsearch-7.4.2/bin/elasticsearch"]
