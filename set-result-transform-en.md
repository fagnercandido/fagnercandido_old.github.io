---
layout: default
---


# [](#header-1)Using setResultTransform of Hibernate
When using native queries, NativeQuery, we can convert the result to a bean. However, he will ask that the fields be all in magnitude. 
To solve this, it's simple, just do the following:

```java
   SQLQuery query = session.createSQLQuery(hql.toString());
   query.setResultTransformer(Transformers.aliasToBean(NomeVO.class));
   query.addScalar("nomeCampo").addScalar("nomeCampo");
```


