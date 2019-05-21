#docker build . -t myocaml
#
FROM debian

RUN apt-get -y update && apt-get -y upgrade && apt-get -y install ocaml

ENV PATH=$PATH:/usr/local/go/bin

RUN mkdir -p src/hello

WORKDIR /src/hello

ADD ./source .

RUN /bin/bash -c "ocamlc -o hello hello.ml"
#CMD ["bash"]

CMD ["./hello"]
