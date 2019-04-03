```
mvn spring-boot:run

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::        (v2.1.0.RELEASE)

Apr 03, 2019 10:34:23 PM org.springframework.cloud.config.client.ConfigServicePropertySourceLocator getRemoteEnvironment
INFO: Fetching config from server at : https://config-c61e8f98-72d0-444d-abfc-2668ace3af9b.apps.pcfdemo.net
Apr 03, 2019 10:34:23 PM org.springframework.cloud.config.client.ConfigServicePropertySourceLocator getRemoteEnvironment
INFO: Connect Timeout Exception on Url - https://config-c61e8f98-72d0-444d-abfc-2668ace3af9b.apps.pcfdemo.net. Will be trying the next url if available
Apr 03, 2019 10:34:23 PM org.springframework.cloud.config.client.ConfigServicePropertySourceLocator locate
WARNING: Could not locate PropertySource: I/O error on GET request for "https://config-c61e8f98-72d0-444d-abfc-2668ace3af9b.apps.pcfdemo.net/aaa/default": sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target; nested exception is javax.net.ssl.SSLHandshakeException: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target
Apr 03, 2019 10:34:23 PM org.springframework.boot.SpringApplication logStartupProfileInfo
INFO: No active profile set, falling back to default profiles: default
Apr 03, 2019 10:34:24 PM org.springframework.cloud.context.scope.GenericScope setSerializationId
INFO: BeanFactory id=4d42f19d-d7de-38e3-bf9b-9ac7199c5abc
Apr 03, 2019 10:34:24 PM org.springframework.context.support.PostProcessorRegistrationDelegate$BeanPostProcessorChecker postProcessAfterInitialization
INFO: Bean 'org.springframework.cloud.autoconfigure.ConfigurationPropertiesRebinderAutoConfiguration' of type [org.springframework.cloud.autoconfigure.ConfigurationPropertiesRebinderAutoConfiguration$$EnhancerBySpringCGLIB$$210bed0d] is not eligible for getting processed by all BeanPostProcessors (for example: not eligible for auto-proxying)
Apr 03, 2019 10:34:24 PM org.springframework.boot.StartupInfoLogger logStarted
INFO: Started SpringConfigApplication in 2.241 seconds (JVM running for 5.556)
[INFO] ------------------------------------------------------------------------

```

- download pcf cert.

```

cd $JAVA_HOME/jre/lib/security

# all the same with followings:
keytool -import                    -keystore cacerts -storepass changeit -alias pcfdemo -file <PATH-TO>/system.pcfdemo.net.pem
keytool -import      -trustcacerts -keystore cacerts -storepass changeit -alias pcfdemo -file <PATH-TO>/system.pcfdemo.net.pem
keytool -importcert  -trustcacerts -keystore cacerts -storepass changeit -alias pcfdemo -file <PATH-TO>/system.pcfdemo.net.pem


keytool -list -keystore cacerts | grep pcfdemo

## delete 
# keytool -delete  -alias pcfdemo  -keystore ${JAVA_HOME}/jre/lib/security/cacerts -storepass changeit



```

```
mvn spring-boot:run


Apr 03, 2019 10:36:37 PM org.springframework.cloud.config.client.ConfigServicePropertySourceLocator getRemoteEnvironment
INFO: Fetching config from server at : https://config-c61e8f98-72d0-444d-abfc-2668ace3af9b.apps.pcfdemo.net
Apr 03, 2019 10:36:38 PM org.springframework.cloud.config.client.ConfigServicePropertySourceLocator locate
WARNING: Could not locate PropertySource: label not found
Apr 03, 2019 10:36:38 PM org.springframework.boot.SpringApplication logStartupProfileInfo
INFO: No active profile set, falling back to default profiles: default
Apr 03, 2019 10:36:38 PM org.springframework.cloud.context.scope.GenericScope setSerializationId
INFO: BeanFactory id=4d42f19d-d7de-38e3-bf9b-9ac7199c5abc
Apr 03, 2019 10:36:38 PM org.springframework.context.support.PostProcessorRegistrationDelegate$BeanPostProcessorChecker postProcessAfterInitialization
INFO: Bean 'org.springframework.cloud.autoconfigure.ConfigurationPropertiesRebinderAutoConfiguration' of type [org.springframework.cloud.autoconfigure.ConfigurationPropertiesRebinderAutoConfiguration$$EnhancerBySpringCGLIB$$8bf0f4c9] is not eligible for getting processed by all BeanPostProcessors (for example: not eligible for auto-proxying)
Apr 03, 2019 10:36:39 PM org.springframework.boot.StartupInfoLogger logStarted
INFO: Started SpringConfigApplication in 2.564 seconds (JVM running for 6.262)
```

- https://docs.pivotal.io/spring-cloud-services/1-5/common/client-troubleshooting.html
- https://javarevisited.blogspot.com/2012/03/add-list-certficates-java-keystore.html
- https://knowledge.digicert.com/solution/SO4085.html
- https://www.lesstif.com/pages/viewpage.action?pageId=12451848
