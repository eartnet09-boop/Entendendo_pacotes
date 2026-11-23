# Registro privado e proxies

## O que é

Um registro privado hospeda pacotes internos ou atua como proxy de pacotes públicos. Ele reduz dispersão de origens e permite auditoria centralizada.

## Como funciona

- Clientes usam um URL ou namespace aprovado.
- Pacotes públicos podem ser armazenados em cache por um proxy.
- Pacotes internos são publicados em um escopo separado.
- Políticas controlam quais fontes podem ser resolvidas.

## Quando usar

Use registro privado para pacotes internos, feeds privados, cache e auditoria. Verdaccio, Artifactory, Nexus e feeds privados no PyPI podem servir esse papel, conforme o ecossistema.

## Como detectar

- Revise logs de origem, nome e versão efetiva.
- Procure resolução por mais de um registro sem justificativa.
- Compare pacotes públicos com nomes internos ou escopos.
- Monitore downloads de pacotes não publicados pela organização.

## Como mitigar

- Reserve namespaces ou escopos internos.
- Use allowlist de registries no CI e no resolvedor.
- Configure `--index-url` para uma única fonte PyPI aprovada; não use `--extra-index-url` para fontes privadas.
- Use proxy/cache como ponto de auditoria e expire artefatos conforme política.
- Relacione a defesa à [Dependency Confusion](../vetores-de-ataque/dependency-confusion.md).
