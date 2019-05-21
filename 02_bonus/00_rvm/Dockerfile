FROM debian:latest

RUN apt-get -y update && apt-get -y upgrade &&\
	apt-get -y install curl gnupg2  procps

RUN command curl -sSL https://rvm.io/pkuczynski.asc | gpg2 --import -

RUN \curl -sSL https://get.rvm.io | bash -s stable && \
	\curl -sSL https://get.rvm.io | bash -s stable --ruby && \
	\curl -sSL https://get.rvm.io | bash -s stable --rails && \
	\curl -sSL https://get.rvm.io | bash -s -- --ignore-dotfiles
RUN echo "source /usr/local/rvm/scripts/rvm" >> ~/.bashrc

RUN mkdir opt/app/ 
#ADD ./project/  /opt/app/ 
WORKDIR /opt/app/ 

EXPOSE 3000

CMD ["bash"]
