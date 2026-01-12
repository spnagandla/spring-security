Ok How am i doing this task Adding the spring security to a project and allow based on the roles
to the particular endpoint but i did not connected to the db this is just a task to learn spring security.


Step 1: add the dependency to POM

<dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-security</artifactId>
    </dependency>


When we add this by default th spring security is added and you cant access them.

Step 2: Make the security config class and annotate it with @Configuration

Step 3: Make the UserDetailsService and make it a bean and make the spring manage it.

Step 4: Now create the users and amdin two users basically and passing them to the in memory database so
        thy are created until the lifetime of the application.
        
        And also we are encodingthe password using the decryptpassword

Step 5: Ad the Security Filter chain and add the basic auth

Step 6: now we will add the request matchers to expose endpoints based on the role using the requestmatchers

          .requestMatchers("/contacts/public/**").permitAll()
                        .requestMatchers(HttpMethod.GET, "/contacts").hasAnyRole("USER", "ADMIN")
                        .requestMatchers(HttpMethod.POST, "/contacts").hasRole("ADMIN")
                        .requestMatchers(HttpMethod.DELETE, "/contacts").hasRole("ADMIN")
                        .anyRequest().authenticated())