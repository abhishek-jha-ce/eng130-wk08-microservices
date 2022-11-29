FROM mongo:4.0.4

LABEL MAINTAINER=abhishek@sparta

WORKDIR /usr/src/db/

COPY ./mongod.conf /etc/

EXPOSE 27017

CMD ["mongod"]