FROM ubuntu:latest

RUN apt-get update
RUN apt-get install -y git
RUN apt-get install -y openssl
RUN apt-get install -y libssl-dev
RUN apt-get install -y cmake
RUN rm -rf /var/lib/apt/lists/*
    
RUN git clone https://github.com/h2o/h2o \
    && cd h2o \
    && git submodule update --init --recursive \
    && cmake . \
    && make h2o

ADD ./htdocs /var/www
ADD ./h2o.conf ./h2o/h2o.conf

WORKDIR /h2o    
ENTRYPOINT ["./h2o", "-c", "h2o.conf"]
