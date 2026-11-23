# O que é um pacote

## O que é

Um pacote é uma unidade distribuível que contém metadados, código ou arquivos compilados e declarações de dependências. Ele é publicado em um registry, pode ser associado a uma assinatura ou proveniência e consumido por um gerenciador.

## Anatomia

Um tarball ou arquivo de pacote normalmente contém um manifesto, arquivos de conteúdo e metadados de publicação. Em npm, por exemplo, o pacote inclui `package.json`; em Java, o artefato é identificado por coordenadas de Maven. Scripts de ciclo de vida, hooks, plugins e regras de build podem executar código adicional.

Árvore conceitual de um pacote:

```text
pacote/
├── manifesto
├── codigo ou artefatos compilados
├── arquivos de recursos
├── scripts de instalacao/build
└── declaracao de dependencias
```

## Versionamento semântico

| Mudança | Exemplo | Impacto |
|---|---|---|
| MAJOR | `1.9.0` -> `2.0.0` | Pode quebrar compatibilidade |
| MINOR | `1.9.0` -> `1.10.0` | Adiciona recursos compatíveis |
| PATCH | `1.9.0` -> `1.9.1` | Corrige defeitos compatíveis |

O Versionamento Semântico (SemVer) melhora previsibilidade, mas não garante que uma nova versão seja segura ou que seu hash corresponda ao histórico esperado.

## Dependências diretas vs transitivas

Dependências diretas são declaradas pela equipe. Dependências transitivas entram pelo grafo criado por dependências diretas e podem permanecer fora da revisão de software. Arquivos de lock e análise completa do grafo são necessários para identificar componentes efetivamente instalados.

Relatórios de gestão de componentes e scanners demonstram que vulnerabilidades podem existir em níveis transitivos, mas cada projeto deve medir seu próprio grafo em vez de aplicar contagens gerais sem evidência local.

## Por que isso importa para segurança

Um pacote pode afetar integridade, disponibilidade e confidencialidade na instalação, no build e na execução. Controles mínimos incluem lockfiles, allowlists, pinning, análise de vulnerabilidades e verificação da origem.

Veja também: [gerenciadores de pacotes](gerenciadores-de-pacotes.md), [registro e distribuição](registro-e-distribuicao.md) e [lockfiles e pinning](../defesas/lockfiles-e-pinning.md).
