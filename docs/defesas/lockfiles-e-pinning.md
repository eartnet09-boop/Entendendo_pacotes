# Lockfiles e pinning

Lockfile é o registro da resolução exata de um grafo de dependências. Ele permite que build, CI e máquina local usem o mesmo conjunto de pacotes e reduz substituição inesperada por novas releases.

## O que é

Pinning fixa uma versão ou hash em vez de permitir que um resolvedor escolha a versão atual. Um lockfile registra o conjunto resolvido e deve ser versionado no repositório.

## Como funciona

- O resolvedor encontra versões compatíveis.
- O lockfile grava versões, integridade ou hashes disponíveis.
- O instalador usa o lockfile em ambientes controlados.
- Atualizações são executadas deliberadamente e revisadas.

## Lockfiles por ecossistema

| Ecossistema | Lockfile ou mecanismo | Prática |
|---|---|---|
| npm | `package-lock.json` | Commitar e usar `npm ci` em CI |
| Python | `poetry.lock` ou arquivo compilado com hashes | Commitar e instalar com hashes |
| Rust | `Cargo.lock` | Commitar em aplicações |
| Go | `go.sum` com `go.mod` | Commitar ambos |
| NuGet | `packages.lock.json` | Habilitar restauração com lock |
| Maven | POM com dependências fixadas | Evitar ranges e liberar revisão |

## Como detectar

- Compare o lockfile com o grafo instalado.
- Monitore versões alteradas sem mudança planejada.
- Verifique ausência de hashes em resolvedores que suportam pinning.
- Revise pull requests que atualizem lockfiles e SBOM.

## Como mitigar

- Commite e proteja o lockfile contra alteração automática não revisada.
- Use tag `main` e similares somente em projetos internos controlados; pins por hash são preferíveis para ações e artefatos.
- Atualize em lotes pequenos e revise changelogs.
- Gere SBOM após a resolução efetiva.
- Links relacionados: [SBOM](sbom-e-inventario.md), [SCA](sca-e-analise-de-composicao.md) e [hardening por ecossistema](hardening-por-ecossistema.md).
