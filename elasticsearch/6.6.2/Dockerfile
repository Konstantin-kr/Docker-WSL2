FROM elasticsearch:6.6.2

#RUN /usr/share/elasticsearch/bin/elasticsearch-plugin install analysis-icu  
#RUN /usr/share/elasticsearch/bin/elasticsearch-plugin install analysis-phonetic


ADD plugins/analysis-icu-6.6.2.zip /usr/share/analysis-icu-6.6.2.zip
ADD plugins/analysis-phonetic-6.6.2.zip /usr/share/analysis-phonetic-6.6.2.zip

RUN /usr/share/elasticsearch/bin/elasticsearch-plugin install file:///usr/share/analysis-icu-6.6.2.zip
RUN /usr/share/elasticsearch/bin/elasticsearch-plugin install file:///usr/share/analysis-phonetic-6.6.2.zip


