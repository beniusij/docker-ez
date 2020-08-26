FROM solr:7.7.3-slim

WORKDIR /opt/solr

# Prepare config
RUN mkdir -p server/ez/template
COPY config/* server/ez/template/

RUN cp server/solr/configsets/_default/conf/solrconfig.xml server/ez/template \
 && cp server/solr/configsets/_default/conf/stopwords.txt server/ez/template \
 && cp server/solr/configsets/_default/conf/synonyms.txt server/ez/template \
 && cp server/solr/solr.xml server/ez \
 && sed -i.bak '/<updateRequestProcessorChain name="add-unknown-fields-to-the-schema".*/,/<\/updateRequestProcessorChain>/d' server/ez/template/solrconfig.xml \
 && sed -ie 's/${solr.autoSoftCommit.maxTime:-1}/${solr.autoSoftCommit.maxTime:20}/' server/ez/template/solrconfig.xml

# Set our core config as home
ENV SOLR_HOME /opt/solr/server/ez

# Make sure core is created on startup
CMD ["solr-create", "-c", "collection1", "-d", "/opt/solr/server/ez/template"]