#docker build . -t myrust

FROM debian

RUN apt-get -y update && apt-get -y upgrade && apt-get -y install curl gcc

RUN curl https://sh.rustup.rs -sSf | sh -s -- -y

ENV PATH=$HOME/.cargo/bin:$PATH

RUN mkdir -p src/hello

WORKDIR /src/hello

ADD ./source .

RUN ~/.cargo/bin/rustc hello.rs

#CMD ["bash"]
CMD ["./hello"]
