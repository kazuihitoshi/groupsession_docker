FROM tomcat:9
RUN apt-get update && apt-get install -y git openssh-client ant wget unzip

ENV JDK_ARCHIVE_NAME=Openjdk11u-dcevm-linux-x64.tar.gz
ENV JDK_DOWNLOAD_URL=https://github.com/TravaOpenJDK/trava-jdk-11-dcevm/releases/download/dcevm-11.0.15%2B1/${JDK_ARCHIVE_NAME}
ENV JAVA_HOME="/usr/local/java/dcevm-11.0.15+1"
ENV PATH="$JAVA_HOME/bin:$PATH"

# Download JDK
RUN set -e; \
    echo "Downloading JDK..."; \
    mkdir -p /usr/local/java && \
    wget -q -O - "${JDK_DOWNLOAD_URL}" \
    | tar -xzf - -C /usr/local/java \
    || (echo "JDK download failed. Please check if the URL is still valid:" \
         && echo "https://github.com/TravaOpenJDK/trava-jdk-11-dcevm/" \
         && echo "download try ${JDK_ARCHIVE_NAME} but not found" \
         && exit 1)

## debug setting start
ENV JAVA_OPTS="-XXaltjvm=$JAVA_HOME/lib/server -javaagent:$JAVA_HOME/lib/hotswap/hotswap-agent.jar -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=*:5005 --add-opens=java.base/jdk.internal.loader=ALL-UNNAMED"

EXPOSE 8080 5005
## debug setting end
