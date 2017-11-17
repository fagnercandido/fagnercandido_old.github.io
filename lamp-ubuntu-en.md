---
layout: default
---


# [](#header-1)Usando setResultTransform do Hibernate
Quando usamos consultas nativas, NativeQuery, podemos converter o resultado para um bean. Contudo, ele irá pedir que os campos sejam todos em maiúsculo. 
Para resolver isso, é simples, basta fazer o seguinte:

```java
   SQLQuery query = session.createSQLQuery(hql.toString());
   query.setResultTransformer(Transformers.aliasToBean(NomeVO.class));
   query.addScalar("nomeCampo").addScalar("nomeCampo");
```


