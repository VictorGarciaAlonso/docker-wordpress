FROM wordpress:latest
#the next args are defined on the docker-compose file
ARG WORDPRESS_DB_USER
ARG WORDPRESS_DB_PASSWORD
ARG WORDPRESS_DB_NAME
ARG WORDPRESS_DB_HOST

#installing the php agent
RUN curl -L "https://download.newrelic.com/php_agent/archive/9.9.0.260/newrelic-php5-9.9.0.260-linux.tar.gz" | tar -C /tmp -zx \
 && export NR_INSTALL_USE_CP_NOT_LN=1 \
 && export NR_INSTALL_SILENT=1 \
 && /tmp/newrelic-php5-*/newrelic-install install \
 && rm -rf /tmp/newrelic-php5-* /tmp/nrinstall*

RUN sed -i -e s/\"REPLACE_WITH_REAL_KEY\"/<your key here>/ \
 -e s/newrelic.appname[[:space:]]=[[:space:]].\*/newrelic.appname="<your app name here>"/ \
 -e s/\;newrelic.daemon.address[[:space:]]=[[:space:]].\*/newrelic.daemon.address="newrelicdaemon:31339"/ \
    /usr/local/etc/php/conf.d/newrelic.ini
#apache needs to be restarted in order for the agent to start gathering data
RUN /etc/init.d/apache2 restart
