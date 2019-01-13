# springAdminServer


# To build
./gradlew clean build


# To run
cd build/libs
java -jar springAdminServer-0.0.1-SNAPSHOT.jar


# To test
http://localhost:8085
    - default security when you simply add in build.gradle: implementation 'org.springframework.boot:spring-boot-starter-security'
            - user = user
            - pwd = 0afe57af-0c73-4afe-9b2d-ea56fcc257e8 (found in the console logs)
            
