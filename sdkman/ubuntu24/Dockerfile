FROM ubuntu:24.04

ENV DEBIAN_FRONTEND=noninteractive

ADD ubuntu.sources /etc/apt/sources.list.d/ubuntu.sources
RUN apt-get update -y && apt-get install zip unzip curl bash -y
ADD sdk /bin/sdk
RUN curl "https://get.sdkman.io" | bash
ENTRYPOINT ["/bin/bash", "-c", "/bin/sdk"]