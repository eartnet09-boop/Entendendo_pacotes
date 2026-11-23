# Typosquatting

## O que é

Typosquatting é a publicação de um pacote cujo nome imita uma dependência legítima por erro de digitação, grafia alternativa ou convenção visual semelhante. O objetivo é fazer o consumidor instalar o pacote errado.

## Como funciona

1. O atacante registra ou publica um nome próximo de uma biblioteca conhecida, como `requsts` em vez de `requests`.
2. Documentação, instruções antigas ou automação podem conter o nome incorreto.
3. O registro resolve o nome digitado e entrega o pacote alternativo.
4. O código do pacote pode executar ações durante a instalação ou quando importado.

## Exemplo real

Casos de nomes fraudulentos ou muito próximos de pacotes populares foram documentados em incidentes no npm e no PyPI. O relatório anual da Sonatype de 2024 descreve abuso recorrente de nomes e publicação maliciosa em registros; relatórios da ENISA sobre o panorama de ameaças incluem ataques à cadeia de fornecimento de software. No site [PyPI](https://pypi.org/) e no [npm](https://www.npmjs.com/) esses mecanismos são mitigados pela revisão de metadados e pela publicação de alertas, mas o consumidor ainda precisa revisar nomes.

## Como detectar

- Compare nomes de dependências com documentação oficial e allowlists.
- Pesquise packages recém-publicados com nomes próximos a componentes existentes.
- Use ferramentas como OSV-Scanner para verificar vulnerabilidades conhecidas e revisar scripts de instalação.
- Alertas de registro, logs de resolução e comparações de hash ajudam a identificar substituição.

## Como mitigar

- Fixe versões e audite o [lockfile](../defesas/lockfiles-e-pinning.md).
- Use escopos internos e [registro privado](../defesas/registro-privado-e-proxies.md).
- Desabilite scripts desnecessários conforme o [hardening por ecossistema](../defesas/hardening-por-ecossistema.md).
- Exija revisão humana para novas dependências antes da instalação.
