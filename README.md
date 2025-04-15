# ReactiveDBTutorial
сначала делаєм Spring boot проект з завісімостями 
-Liquibase(Migration)
-Reactive Web
-Spring Data R2DBC 
(Дополнітельна інфориація Spring boot:3.4.4 java:21)
і откриваємо проект

в aplication.proporties вводим 

spring.r2dbc.url=r2dbc:mysql://${MYSQL_HOST:localhost}:3306/reactiveweb
spring.r2dbc.username=root
spring.r2dbc.password=20090620

spring.datasource.url=jdbc:mysql://${MYSQL_HOST:localhost}:3306/reactiveweb
spring.datasource.username=root
spring.datasource.password=20090620
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

spring.liquibase.change-log=classpath:db/changelog/db.changelog-master.yaml
spring.liquibase.enabled=true

 в pom.xml додайєм драйвер mysql шоб liquibase могла взаэмодіяти з бд:
<dependency>
    <groupId>com.mysql</groupId>
    <artifactId>mysql-connector-j</artifactId>
    <version>8.3.0</version>
</dependency>
<dependency>
  	<groupId>io.asyncer</groupId>
	<artifactId>r2dbc-mysql</artifactId>
 	<version>1.1.3</version>
</dependency>
і также найди завісімость
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-jdbc</artifactId>
</dependency>
і поміняй її на
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-jdbc</artifactId>
</dependency>
а потом додай конфігурацію 
LiquibaseConfig.java

і саме главне акуратно работай з db.changelog-master.yaml бо я не зробив id autoIncrement і 3 часа шукав шо не так 
