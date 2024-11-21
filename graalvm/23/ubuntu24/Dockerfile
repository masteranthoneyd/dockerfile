FROM yangbingdong/sdkman:ubuntu24

SHELL ["bash", "--login", "-c"]
ADD GRAALVM_VERSION .
RUN apt-get update -y && apt-get install build-essential libz-dev zlib1g-dev -y
RUN sdk install java $(cat GRAALVM_VERSION) && sdk use java $(cat GRAALVM_VERSION)
ENV JAVA_HOME=/root/.sdkman/candidates/java/current
ENV PATH=$JAVA_HOME/bin:$PATH
RUN which native-image

ENTRYPOINT ["/bin/bash","--login", "-c"]