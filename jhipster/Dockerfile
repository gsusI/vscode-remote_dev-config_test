FROM jhipster/jhipster

EXPOSE 8080:8080
EXPOSE 9001:9000
EXPOSE 3001:3001

USER root
RUN sudo apt-get update
RUN sudo apt-get install -y screen
RUN sudo apt-get install -y htop
USER jhipster
RUN ulimit -v 3000000