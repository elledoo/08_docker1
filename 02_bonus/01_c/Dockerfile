#docker build . -t myc
#docker run --rm myc
FROM alpine

RUN apk update && apk update && apk add nano && apk add gcc &&\
	apk add libc-dev

ADD ./source .

RUN gcc main.c

#CMD ["sh"]
CMD ["./a.out"]
