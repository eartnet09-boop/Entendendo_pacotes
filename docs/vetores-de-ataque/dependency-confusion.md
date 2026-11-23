# Dependency Confusion

## O que é

Dependency Confusion é o uso de um nome interno de pacote no registro público para induzir um resolvedor a preferir ou baixar o pacote externo, em vez da biblioteca privada. O problema aparece quando nomes internos não são reservados nem isolados.

## Como funciona

1. Uma organização usa um nome privado exclusivo, sem publicá-lo no registro público.
2. Um resolvedor também consulta o registro público.
3. Um pacote externo com o mesmo nome pode ser considerado elegível.
4. Quando o resolvedor usa regras de prioridade ou versão favoráveis ao externo, o código errôneo pode entrar no build.

## Exemplo real

O problema foi descrito publicamente por Alex Birsan em 2021 e recebeu amplo registro em relatórios de fornecedores e pesquisadores. A falha não é um tipo único de pacote malicioso: é uma diferença entre contextos de resolução interna e pública.

## Como detectar

- Liste dependências privadas que existem em fontes públicas.
- Monitore resolução de nomes em logs de CI e de registros.
- Compare a origem efetiva, o nome do pacote e o hash entregue.
- Execute revisões de configuração em ferramentas que suportam múltiplos índices.

## Como mitigar

- Use escopos e namespaces internos, como `@minha-org/nome`.
- Configure um [registro privado ou proxy](../defesas/registro-privado-e-proxies.md) como fonte aprovada.
- Não use `--extra-index-url` para fontes privadas no PyPI; prefira `--index-url` com origem única ou infraestrutura intermediária.
- Fixe versões no [lockfile](../defesas/lockfiles-e-pinning.md).
- Verifique o índice efetivo em CI e negue registros não autorizados.
