FROM ubuntu:22.04 AS build
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -y git build-essential cmake make gcc g++ libsctp-dev lksctp-tools
RUN git clone --depth 1 -b v3.2.6 https://github.com/aligungr/UERANSIM /ueransim && cd /ueransim && make

FROM ubuntu:22.04
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -y libsctp1 iproute2 iputils-ping curl \
    && rm -rf /var/lib/apt/lists/*
COPY --from=build /ueransim/build /ueransim/build
