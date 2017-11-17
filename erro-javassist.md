---
layout: default
---


# [](#header-1)SpringBoot+Orika

Olá Pessoal,

Ao trabalhar com microserviços, é desejável ter um modelo de mapeamento entidade-vo e vice-versa. No mercado existem diversas opções que realizam estes mapeamentos. Temos o Dozer, Mapper, Orika e outros. O que me chamou atenção foi o Orika, por conta do desempenho. O mesmo utiliza uma fábrica e pré mapeamento das entidades. O Dozer por exemplo, utiliza reflexão, sendo bem mais lento, embora, seja de utilização mais trivial.
Ao inserir o mesmo como dependência em um projeto com SpringBoot, o erro abaixo começou a ocorrer:


```java
Error starting ApplicationContext. To display the auto-configuration report re-run your application with 'debug' enabled.
2017-11-15 14:35:17.302 ERROR 32055 --- [  restartedMain] o.s.boot.SpringApplication               : Application startup failed

org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaAutoConfiguration.class]: Invocation of init method failed; nested exception is org.hibernate.boot.archive.spi.ArchiveException: Could not build ClassFile
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1628) ~[spring-beans-4.3.8.RELEASE.jar:4.3.8.RELEASE]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:555) ~[spring-beans-4.3.8.RELEASE.jar:4.3.8.RELEASE]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:483) ~[spring-beans-4.3.8.RELEASE.jar:4.3.8.RELEASE]
	at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:306) ~[spring-beans-4.3.8.RELEASE.jar:4.3.8.RELEASE]
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:230) ~[spring-beans-4.3.8.RELEASE.jar:4.3.8.RELEASE]
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:302) ~[spring-beans-4.3.8.RELEASE.jar:4.3.8.RELEASE]
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:197) ~[spring-beans-4.3.8.RELEASE.jar:4.3.8.RELEASE]
	at org.springframework.context.support.AbstractApplicationContext.getBean(AbstractApplicationContext.java:1081) ~[spring-context-4.3.8.RELEASE.jar:4.3.8.RELEASE]
	at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:856) ~[spring-context-4.3.8.RELEASE.jar:4.3.8.RELEASE]
	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:542) ~[spring-context-4.3.8.RELEASE.jar:4.3.8.RELEASE]
	at org.springframework.boot.context.embedded.EmbeddedWebApplicationContext.refresh(EmbeddedWebApplicationContext.java:122) ~[spring-boot-1.5.3.RELEASE.jar:1.5.3.RELEASE]
	at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:737) [spring-boot-1.5.3.RELEASE.jar:1.5.3.RELEASE]
	at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:370) [spring-boot-1.5.3.RELEASE.jar:1.5.3.RELEASE]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:314) [spring-boot-1.5.3.RELEASE.jar:1.5.3.RELEASE]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1162) [spring-boot-1.5.3.RELEASE.jar:1.5.3.RELEASE]
	at org.springframework.boot.SpringApplication.run(SpringApplication…
```

E, para surpresa, o javassist é que ocasionava o erro.
Uma possível solução foi na dependência do Orika, realizar o exclude:

```xml
<dependency>
        <groupId>ma.glasnost.orika</groupId>
        <artifactId>orika-core</artifactId>
        <version>${orika.version}</version>
        <exclusions>
                <exclusion>
                        <groupId>org.javassist</groupId>
                        <artifactId>javassist</artifactId>
                </exclusion>
        </exclusions>
</dependency>

```

E adicionar manualmente a dependência do javassit:
```xml
<dependency>
        <groupId>org.javassist</groupId>
        <artifactId>javassist</artifactId>
        <version>${javassist.version}</version>
</dependency>

```

Té mais,
