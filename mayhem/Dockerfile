FROM --platform=linux/amd64 ubuntu:22.04 as builder

RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y build-essential git

COPY . /repo
WORKDIR /repo
RUN gcc -o vcompiler v.c
RUN git clone https://github.com/vlang/v /v
RUN cp -r /v/* /repo
RUN rm -rf /v

FROM --platform=linux/amd64 ubuntu:22.04 as package
RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y build-essential
COPY --from=builder /repo /repo