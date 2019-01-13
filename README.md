# springAdminServer


# To build
./gradlew clean build


# To run
cd build/libs
java -jar springAdminServer-0.0.1-SNAPSHOT.jar


# To test
http://localhost:8085
    - default security:
            - simply add in build.gradle: implementation 'org.springframework.boot:spring-boot-starter-security'
            - user = user
            - pwd = 0afe57af-0c73-4afe-9b2d-ea56fcc257e8 (found in the console logs)


    - customized security:
            - using Tomcat:
                    TODO Now that I have added WebSecurityConfig
                    TODO DefaultHandlerExceptionResolver : Resolved [org.springframework.web.HttpRequestMethodNotSupportedException: Request method 'POST' not supported]
            - using Netty:
                    TODO See docs for Spring WebFlux)
                    TODO https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#boot-features-security-webflux
                    TODO public SecurityWebFilterChain springSecurityFilterChain(ServerHttpSecurity http) ....

