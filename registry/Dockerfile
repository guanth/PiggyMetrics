FROM goodrainapps/maven:jdk8-alpine
MAINTAINER zhouyq  <zhouyq@goodrain.com>

# Caching Maven dependencies
COPY *.xml /app/
WORKDIR /app
RUN mvn -s maven-settings.xml  verify clean -Dmaven.repo.local=/tmp/cache --fail-never

# package
COPY . /app
RUN mvn -s maven-settings.xml -B -DskipTests=true -Dmaven.repo.local=/tmp/cache clean install

EXPOSE 8761

CMD ["java", "-Xmx200m", "-jar", "/app/target/registry.jar"]
