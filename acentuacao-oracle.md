---
layout: default
---


# [](#header-1)Acentuação Oracle
Olá PessoALL,

Recentemente enfrentamos um problema em produção bem singular: Ao salvar um dado no banco de dados, o mesmo não era inserido, erro, por excesso de caracteres.

Contudo, ao contar quantos caracteres existiam na sequência, era perfeitamente cabível. Até quê… Os acentos.

Ah, os acentos… Eles adicionam caracteres a mais no dado a ser salvo. Essa situação foi verificada no Oracle, sobre os outros SGBD’s não posso afirmar nada.

Solução: Simples, aumentamos o tamanho dos campos em suas tabelas.

Até mais e obrigado pela atenção

