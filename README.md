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