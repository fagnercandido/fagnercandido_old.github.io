---
layout: default
---


# [](#header-1)Lição aprendida - Tipo de coluna inválido: getString not implemented for class oracle.jdbc.driver.t4cblobaccess or

Olá Pessoal,

Erros ocorrem. Então tentarei dar início numa série de post de erros que ocorrem com certa frequência e que ficam como lições aprendidas.

E para começar, este erro: Tipo de coluna inválido: getString not implemented for class oracle.jdbc.driver.T4CBlobAccessor
Este erro ocorreu numa aplicação com o banco de dados Oracle. E na internet as soluções são bem variadas. Uns falam do driver jdbc, outros do tipo de dado… Enfim, no meu caso foi: O campo existia no banco de dados, contudo, não estava mapeado. Com um agravante: É dado um Hibernate.initialize na tabela.

Para resolver, bastou mapear o campo.

Pronto, por hoje é só pessoal!

Abraços,
