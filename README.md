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
            - as we use the Netty server (ie Spring WebFlux), TODO
                    - https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#boot-features-security-webflux
                    public SecurityWebFilterChain springSecurityFilterChain(ServerHttpSecurity http) ....
            - see notes below when using Spring MVC


# Achieve customized security when using Spring MVC
@Configuration
public class WebSecurityConfig extends WebSecurityConfigurerAdapter {

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http.formLogin()
                .loginPage("/login.html")
                .loginProcessingUrl("/login")
                .permitAll();

        http.logout().logoutUrl("/logout");

        http.csrf().disable();

        http.authorizeRequests()
                .antMatchers("/login.html", "/**/*.css", "/img/**", "/third-party/**")
                .permitAll();

        http.authorizeRequests()
                .antMatchers("/**")
                .hasRole("USER");
        http.httpBasic();
    }

    @Autowired
    public void configureGlobal(AuthenticationManagerBuilder auth) throws Exception {
        // TODO Have these credentials in a props file
        auth.inMemoryAuthentication().withUser("user").password("pass").roles("USER");
    }
}
