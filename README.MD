<p>If you are having the problem: NoSuchMethodError: net.minidev.json.JSONObject com.nimbusds.jose.Header.toJSONObject() org.springframework.security.oauth2.jwt.NimbusJwtDecoder.createJwt Maybe in your pom.xml you are importing spring-boot-starter-oauth2-resource-server and oauth2-oidc-sdk. These 2 have nimbus-jose-jwt as a dependency and they are conflicting, so you need to do a exclusion dependency in one of this dependencies.<br/><strong>Example:</strong></p>

```
<dependency>
    <groupId>com.nimbusds</groupId>
    <artifactId>oauth2-oidc-sdk</artifactId>
    <version>${oauth2-oidc-sdk.version}</version>
    <exclusions>
        <exclusion>
          <groupId>com.nimbusds</groupId>
          <artifactId>nimbus-jose-jwt</artifactId>
        </exclusion>
     </exclusions>
</dependency>
```
