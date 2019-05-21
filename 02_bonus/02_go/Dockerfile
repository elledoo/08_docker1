#docker build . -t mygo
#

FROM debian

RUN apt-get -y update && apt-get -y upgrade && apt-get -y install curl

RUN curl https://dl.google.com/go/go1.12.5.linux-amd64.tar.gz >  go1.12.5.linux-amd64.tar.gz &&\
	tar -C /usr/local -xzf go1.12.5.linux-amd64.tar.gz 

ENV PATH=$PATH:/usr/local/go/bin

RUN mkdir -p src/hello

WORKDIR /src/hello

ADD ./source .

RUN /bin/bash -c "go build"
#CMD ["bash"]

CMD ["./hello"]
