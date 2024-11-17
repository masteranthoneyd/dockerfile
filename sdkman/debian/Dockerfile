FROM debian:latest

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update -y && apt-get install zip unzip curl bash -y
ADD sdk /bin/sdk
RUN curl "https://get.sdkman.io" | bash
ENTRYPOINT ["/bin/bash", "-c", "/bin/sdk"]