---
layout: default
---


# [](#header-1)JSF - Problemas com acentuação
Olá Pessoal,

Recentemente ao trabalhar com o JSF 2.x tive um problema bem estranho: ao usar acentuação, os meus forms eram submetidos com acentuação quebrada. Daí ocorriam duas situações: a primeira, era se houvesse algum problema com as validações (dados de negócio inconsistentes), o formulário voltava com a acentuação quebrada, e a segunda eram os dados serem inseridos inconsistentes.

Depois de muita pesquisa, uma solução simples: o atributo acceptcharset do form. Simples assim, basta adicionar este atributo, e colocar o encoding(utf-8, ISSO-8859-1…).

Pronto. Os formulários podem ser submetidos e a acentuação voltou ao normal.

Até a próxima.
