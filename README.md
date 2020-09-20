# First Step
1. Create pom.xml and write like below
```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>com.belajar</groupId>
	<artifactId>belajar-web</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<name>belajar-web</name>
	<description>Belajar Web Tradisional</description>
	<packaging>war</packaging>

	<dependencies></dependencies>

</project>
```

2. Open Your Terminal
3. Change Directory to web-practice
4. Type "mkdir -p src/main/{java, webapp}"
5. Type "touch src/main/webapp/index.html"
6. Open index.html and write the html tag
7. Back to your terminal and type "mvn clean tomcat:run"
8. Open your browser and type http://localhost:8080/belajar-web

# Second Step
## deploy to tomcat server
1. Type the configuration below in pom.xml
```
<build>
	<plugins>
		<plugin>
			<groupId>org.apache.maven.plugins</groupId>
			<artifactId>maven-war-plugin</artifactId>
			<configuration>
				<failOnMissingWebXml>false</failOnMissingWebXml>
			</configuration>
		</plugin>
	</plugins>
</build>
```
and become like this
```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>com.belajar</groupId>
	<artifactId>belajar-web</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<name>belajar-web</name>
	<description>Belajar Web Tradisional</description>
	<packaging>war</packaging>

	<dependencies></dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-war-plugin</artifactId>
				<configuration>
					<failOnMissingWebXml>false</failOnMissingWebXml>
				</configuration>
			</plugin>
		</plugins>
	</build>
</project>
```
2. Save the pom.xml and open your terminal
3. Type mvn clean package
4. And now, you can see the file belajar-web.war in "target/belajar-web.war"
5. Download Tomcat 8 and extract the zip file
6. cd to/your/path/apache-tomcat-8.5.58/
7. Type "./bin/startup.sh"
```
Using CATALINA_BASE:   /d/Software/apache-tomcat-8.5.58
Using CATALINA_HOME:   /d/Software/apache-tomcat-8.5.58
Using CATALINA_TMPDIR: /d/Software/apache-tomcat-8.5.58/temp
Using JRE_HOME:        C:\Program Files\Java\jdk-12.0.2
Using CLASSPATH:       /d/Software/apache-tomcat-8.5.58/bin/bootstrap.jar:/d/Software/apache-tomcat-8.5.58/bin/tomcat-juli.jar
Using CATALINA_OPTS:
Tomcat started.
```
8. Copy belajar-web.war to "/apache-tomcat-8.5.58/webapps/" and please wait until file extract done.
9. Type "tail -f logs/catalina.out"
```
20-Sep-2020 14:01:19.639 INFO [localhost-startStop-1] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory [D:\Software\apache-tomcat-8.5.58\webapps\host-manager]
20-Sep-2020 14:01:19.697 INFO [localhost-startStop-1] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory [D:\Software\apache-tomcat-8.5.58\webapps\host-manager] has finished in [58] ms
20-Sep-2020 14:01:19.698 INFO [localhost-startStop-1] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory [D:\Software\apache-tomcat-8.5.58\webapps\manager]
20-Sep-2020 14:01:19.747 INFO [localhost-startStop-1] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory [D:\Software\apache-tomcat-8.5.58\webapps\manager] has finished in [49] ms
20-Sep-2020 14:01:19.747 INFO [localhost-startStop-1] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory [D:\Software\apache-tomcat-8.5.58\webapps\ROOT]
20-Sep-2020 14:01:19.817 INFO [localhost-startStop-1] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory [D:\Software\apache-tomcat-8.5.58\webapps\ROOT] has finished in [70] ms
20-Sep-2020 14:01:19.824 INFO [main] org.apache.coyote.AbstractProtocol.start Starting ProtocolHandler ["http-nio-8080"]
20-Sep-2020 14:01:19.856 INFO [main] org.apache.catalina.startup.Catalina.start Server startup in 2147 ms
20-Sep-2020 14:24:30.217 INFO [localhost-startStop-2] org.apache.catalina.startup.HostConfig.deployWAR Deploying web application archive [D:\Software\apache-tomcat-8.5.58\webapps\belajar-web.war]
20-Sep-2020 14:24:30.372 INFO [localhost-startStop-2] org.apache.catalina.startup.HostConfig.deployWAR Deployment of web application archive [D:\Software\apache-tomcat-8.5.58\webapps\belajar-web.war] has finished in [154] ms
```
10. Open your browser and type "http://localhost:8080/belajar-web/"

## undeploy from tomcat server
1. Open "/apache-tomcat-8.5.58/webapps/" delete belajar-web.war and please wait until file extractor is erased.
2. tail -f "logs/catalina.out"
```
20-Sep-2020 14:01:19.697 INFO [localhost-startStop-1] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory [D:\Software\apache-tomcat-8.5.58\webapps\host-manager] has finished in [58] ms
20-Sep-2020 14:01:19.698 INFO [localhost-startStop-1] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory [D:\Software\apache-tomcat-8.5.58\webapps\manager]
20-Sep-2020 14:01:19.747 INFO [localhost-startStop-1] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory [D:\Software\apache-tomcat-8.5.58\webapps\manager] has finished in [49] ms
20-Sep-2020 14:01:19.747 INFO [localhost-startStop-1] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory [D:\Software\apache-tomcat-8.5.58\webapps\ROOT]
20-Sep-2020 14:01:19.817 INFO [localhost-startStop-1] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory [D:\Software\apache-tomcat-8.5.58\webapps\ROOT] has finished in [70] ms
20-Sep-2020 14:01:19.824 INFO [main] org.apache.coyote.AbstractProtocol.start Starting ProtocolHandler ["http-nio-8080"]
20-Sep-2020 14:01:19.856 INFO [main] org.apache.catalina.startup.Catalina.start Server startup in 2147 ms
20-Sep-2020 14:24:30.217 INFO [localhost-startStop-2] org.apache.catalina.startup.HostConfig.deployWAR Deploying web application archive [D:\Software\apache-tomcat-8.5.58\webapps\belajar-web.war]
20-Sep-2020 14:24:30.372 INFO [localhost-startStop-2] org.apache.catalina.startup.HostConfig.deployWAR Deployment of web application archive [D:\Software\apache-tomcat-8.5.58\webapps\belajar-web.war] has finished in [154] ms
20-Sep-2020 14:31:20.982 INFO [ContainerBackgroundProcessor[StandardEngine[Catalina]]] org.apache.catalina.startup.HostConfig.undeploy Undeploying context [/belajar-web]
```
3. Open your browser and type "http://localhost:8080/belajar-web"

## Stop Tomcat Service
1. ./bin/shutdown.sh
```
Using CATALINA_BASE:   /d/Software/apache-tomcat-8.5.58
Using CATALINA_HOME:   /d/Software/apache-tomcat-8.5.58
Using CATALINA_TMPDIR: /d/Software/apache-tomcat-8.5.58/temp
Using JRE_HOME:        C:\Program Files\Java\jdk-12.0.2
Using CLASSPATH:       /d/Software/apache-tomcat-8.5.58/bin/bootstrap.jar:/d/Software/apache-tomcat-8.5.58/bin/tomcat-juli.jar
Using CATALINA_OPTS:
NOTE: Picked up JDK_JAVA_OPTIONS:  --add-opens=java.base/java.lang=ALL-UNNAMED --add-opens=java.base/java.io=ALL-UNNAMED --add-opens=java.rmi/sun.rmi.transport=ALL-UNNAMED
```
3. FINISH