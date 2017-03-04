# Set the base image to hnbuzz because it's already set up
FROM elasticsearch:1.7.4

RUN echo 'path.repo: ["/opt/elasticsearch/backup"]' >> /usr/share/elasticsearch/config/elasticsearch.yml

COPY docker-entrypoint.sh /
