---
layout: default
---


# [](#header-1)Servidor de compartilhamento HTTP
A dica a seguir surgiu da necessidade, ou quase isso, de compartilhar um diretório o mais rápido possível. O fato é que, a linguagem de programação Python, nos oferece recursos diversos, o potencial da mesma é inquestionável.

A situação foi a seguinte: queríamos compartilhar algumas músicas, alguns sugeriram o NFS, outros pendrives, a ideia era o compartilhamento o mais rápido possível entre todos, em uma mesma rede, por fim, um colega fez o seguinte no diretório a ser compartilhado:
```shell
$ python -m SimpleHTTPServer númeroPorta
```
Pronto, desta forma, levantamos um servidor Python HTTP na porta especificada, onde todo o conteúdo corrente do diretório será compartilhado, vale ressaltar que, a porta citada não deve estar em uso. Em seguida:

http://númeroIp:númeroDaPorta

Feito isso, compartilhamento concluído!!!

Abraços a todos, e qualquer sugestão, crítica construtiva serão bem-vindas.


