# Gerenciadores de pacotes

Gerenciadores resolvem nomes, versões e dependências transitivas, fazem download e podem executar scripts ou plugins. A escolha segura começa pelo registro usado, pelo arquivo de lock e pelas capacidades de verificação disponíveis.

| Gerenciador | Registro padrão | Lockfile ou forma equivalente | Resolução | Risco específico |
|---|---|---|---|---|
| npm | npm Registry | `package-lock.json` | Grafo e semver | Scripts de ciclo de vida e nomes ambíguos |
| pip/PyPI | PyPI ou índice configurado | `requirements*.txt` com hashes ou ferramenta de compile | Índice e compatibilidade | Índices múltiplos e conflitos de nome |
| Maven | Maven Central ou repos configurados | POM como declaração; build pode resolver ranges | Coordenadas GAV | Plugins e dependências transitivas |
| Go Modules | Proxy Go e sumdb, configuráveis | `go.sum` e `go.mod` | Versões de módulo | Contas e origens de módulos |
| NuGet | NuGet.org ou feeds privados | `packages.lock.json` | Dependências .NET | Fonte de feed e restauração de build |
| Cargo | crates.io | `Cargo.lock` | Resolução Rust de crates | Builds e dependências transitivas |

## npm

O npm combina resolução de semver, workspaces e scripts `preinstall`, `install` e `postinstall`. A equipe deve commitar `package-lock.json`, desabilitar scripts quando não forem necessários e auditar o grafo. O npm 11 introduz configuração de idade mínima de release; em versões antigas, use processo de atualização controlada.

## PyPI e pip

O pip resolve artefatos do índice configurado e usa preferencialmente um único índice confiável. Configurar `--index-url` limita a origem; `--extra-index-url` pode ampliar ambiguidades em ambientes privados. Requisitos fixados e hashes evitam substituição inesperada.

## Maven

Maven resolve dependências por coordenadas de grupo, artefato e versão. Plugins também são componentes de build e podem executar durante a construção. Configure repositórios, fixe versões e use regras de Enforcer para impedir ranges e dependências em release.

## Go Modules

Go Modules usa `go.mod` para declaração e `go.sum` para hashes de módulos. `GOPROXY` e `GOSUMDB` devem ser explícitos em ambientes sensíveis. `go mod verify` verifica os downloads já registrados no módulo.

## NuGet

O NuGet pode restaurar a partir de feeds públicos ou privados. O arquivo `packages.lock.json` torna o conjunto esperado reproduzível quando restaurado com lock habilitado. Pacotes privados devem usar nomes e feeds com escopo claro.

## Cargo

Cargo registra a resolução em `Cargo.lock` para aplicações e pode usar build scripts que executam em tempo de compilação. Revisar o lockfile e atualizar somente em mudanças planejadas reduz substituição inesperada.

Continue em [registro e distribuição](registro-e-distribuicao.md) e [hardening por ecossistema](../defesas/hardening-por-ecossistema.md).
