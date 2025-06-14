FROM tomcat:9
RUN apt-get update && apt-get install -y git openssh-client ant wget unzip

ENV JDK_ARCHIVE_NAME=OpenJDK11U-jdk_x64_linux_hotspot_11.0.24_8.tar.gz
ENV JDK_DOWNLOAD_URL=https://github.com/adoptium/temurin11-binaries/releases/download/jdk-11.0.24%2B8/${JDK_ARCHIVE_NAME}
ENV JAVA_HOME="/usr/local/java/jdk-11.0.24+8"
ENV PATH="$JAVA_HOME/bin:$PATH"

# Download JDK
RUN set -e; \
    echo "Downloading JDK..."; \
    mkdir -p /usr/local/java && \
    wget -q -O - "${JDK_DOWNLOAD_URL}" \
    | tar -xzf - -C /usr/local/java \
    || (echo "JDK download failed. Please check if the URL is still valid:" \
         && echo "https://github.com/adoptium/temurin11-binaries" \
         && echo "download try ${JDK_ARCHIVE_NAME} but not found" \
         && exit 1)
	 
## debug setting start
#ENV JAVA_OPTS="-agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=*:5005"
EXPOSE 8080 5005
## debug setting end
