# Configurações centralizadas

Integrantes: Fernando, Felipe Montalvão e Victor Hugo.

Publique o conteúdo desta pasta na raiz de um repositório GitHub chamado `repo-configs`, na branch `main`.
Este é um repositório independente do código das quatro aplicações.

| Serviço | DEV | PROD | Porta |
| --- | --- | --- | --- |
| Vendas | cliente-vendas-dev.properties | cliente-vendas-prod.properties | 8081 |
| Estoque | cliente-estoque-dev.properties | cliente-estoque-prod.properties | 8082 |
| Relatórios | cliente-relatorios-dev.properties | cliente-relatorios-prod.properties | 8083 |

`mensagem.boasvindas` define o texto de `/mensagem`; `server.port` define a porta;
`app.ambiente` identifica o ambiente exibido em `/configuracao`.
Os acentos são escritos com escapes Unicode compatíveis com arquivos Java Properties.
DEV e PROD usam as mesmas portas porque representam execuções alternativas, não simultâneas na mesma máquina.

O Config Server usa `${CONFIG_GIT_URI}` para acessar este repositório. Consulte
`http://localhost:8888/cliente-vendas/dev/main` após iniciar o servidor.
O campo `version` da resposta informa o SHA do commit Git consultado.

Para demonstrar versionamento, altere a mensagem DEV de Vendas e faça um commit na branch `main`.
Depois execute `POST http://localhost:8081/actuator/refresh` no cliente Vendas.
A nova mensagem aparece sem reiniciar a aplicação. A mudança de porta exige reinicialização.
Guarde segredos fora deste repositório.

## Projeto cliente

Código, relatório e instruções: https://github.com/FernandoAlves049/trabalho-config-server
