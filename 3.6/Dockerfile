FROM java:openjdk-7-alpine

# Install Apache Solr
ENV SOLR_VERSION 3.6.2
ENV SOLR apache-solr-$SOLR_VERSION
ADD http://archive.apache.org/dist/lucene/solr/$SOLR_VERSION/$SOLR.tgz /opt/$SOLR.tgz
RUN tar -C /opt --extract --file /opt/$SOLR.tgz
RUN mv /opt/$SOLR /opt/solr

COPY ./config /temp/solr-drupal-config

RUN cd /temp/solr-drupal-config && cp -f \
   elevate.xml \
   mapping-ISOLatin1Accent.txt \
   protwords.txt \
   schema_extra_fields.xml \
   schema_extra_types.xml \
   schema.xml \
   solrconfig_extra.xml \
   solrconfig.xml \
   solrcore.properties \
   stopwords.txt \
   synonyms.txt \
   /opt/solr/example/solr/conf/

# Run Apache Solr
WORKDIR /opt/solr
EXPOSE 8983
CMD ["/bin/bash", "-c", "cd /opt/solr/example; java -jar start.jar"]
