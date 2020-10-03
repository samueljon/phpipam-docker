# phpIPAM Apache container 

FROM samueljon/phpipam-base:latest

ARG BUILD_DATE
ARG VCS_REF
ARG VERSION
ARG BRANCH

LABEL org.label-schema.build-date=$BUILD_DATE \
      org.label-schema.name="phpIPAM Apache Container" \
      org.label-schema.description="phpIPAM is an open-source web IP address management application (IPAM). Its goal is to provide light, modern and useful IP address management." \
      org.label-schema.url="https://phpipam.net/" \
      org.label-schema.vcs-ref=$VCS_REF \
      org.label-schema.vcs-url="https://github.com/phpipam/phpipam/" \
      org.label-schema.vendor="phpIPAM" \
      org.label-schema.version=$VERSION \
      org.label-schema.schema-version="1.0" \
      maintainer="Gary Allan <github@gallan.co.uk>"

WORKDIR /

# Download phpIPAM
RUN sed -i 's/Listen 80/Listen 8080/' /etc/apache2/httpd.conf
RUN /install_phpipam $BRANCH $VCS_REF

# Run Apache
EXPOSE 8080

ENTRYPOINT ["/sbin/tini", "--"]
CMD /start_apache2
