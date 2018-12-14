# SpringBoot
This documentation is used for begin learner to know about the basics of Spring Boot

1.Spring Boot project must have Spring Boot's parent
	add parent in pom.xml
	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>2.1.1.RELEASE</version>
	</parent>   
	parent include dependencies release number.

2. import web support dependency for spring boot to add tomcat and SpringMVC configuration
	<dependency>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-web</artifactId>
	</dependency>

3. import Spring boot plugin :  use spring-boot:run to call the plugin to run the application
		<plugin>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-maven-plugin</artifactId>
		</plugin>

4. Application start point usually is the class named "XxxxxApplication"
	some annotations: @Controller    springmvc controller annotation
					  @SpringBootApplication   core annotation
					  @Configuration
	
	main method includes SpringApplication.run(XxxxxApplication.class,args);
	

5. @SpringBootApplication combined annotation 

6. @EnableAutoConfiguration

7. @ComponentScan default scan @SpringBootApplication classes' same level files and sub files

8. Close auto configuration
	@SpringBootApplication(exclude = {RedisAutoConfiguration.class})
	
9. Banner  txt file copy to resources
			close Banner: SpringApplication application = new SpringApplication(XxxxxApplication.class);
							application.setBannerMode(Mode.OFF);
							application.run(args);
							
10. SpringBoot configuration : application.properties / application.yml at resources folder

12. start pom is used to automatic configuration for the related framework

13. xml configue file 
	@ImportResource("classpath:xxx.xml")

14. The path of static resources needs to be: /META-INF/resources/, /resources/,/static/,/public/
	spring.resources.static-locations = classpath:/META-INF/resources/,classpath:/resources/,classpath:/static/,classpath:/public/

15. Spring Boot auto configuration
	When Spring Boot create the instance of Spring Application, it will auto load META-INF/Spring.factories file to get all configuration files into Spring container
	
16. Message converter
	Add bean class to XxxxxApplication (@Configuration)
	@Bean
	public StringHttpMessageConverter stringHttpMessageConverter() {
		StringHttpMessageConverter converter = new StringHttpMessageConverter(Charset.forName("UTF-8")); //ISO-9959-1
		return converter;
	}
17. when we want to config SpringMVC by ourselves, for example, add a HandlerInterceptor. need to extends WebMvcConfigurerAdapter and override the method in super class
