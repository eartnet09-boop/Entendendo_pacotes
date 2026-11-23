# Pacotes maliciosos

## O que é

Pacotes maliciosos são componentes publicados ou substituídos para executar comportamento indevido durante instalação, build ou execução. A ameaça pode entrar por uma publicação legítima comprometida ou por um projeto criado diretamente para enganar consumidores.

## Como funciona

1. Um agente publica ou modifica um pacote em um registro.
2. A dependência parece adequada pelo nome, descrição ou versão.
3. Scripts `preinstall`, `postinstall`, plugins ou build hooks podem executar código automaticamente.
4. Código com a identidade do processo consumidor pode alcançar arquivos, credenciais ou rede disponíveis.

## Exemplo real

Em 2021, a equipe do pacote `ua-parser-js` no npm publicou versões comprometidas que continham código malicioso. Em 2022, `colors` e `faker` receberam alterações que afetaram aplicações consumidoras em casos documentados pela comunidade e pela Snyk. Estes exemplos mostram que o risco existe em pacotes instalados por repositórios confiáveis, não apenas em nomes falsos.

## Como detectar

- Compare a versão instalada com o lockfile e o SBOM.
- Revise scripts de ciclo de vida e plugins de build antes de atualizar.
- Monitore alterações inesperadas em rede, processo filho e arquivos durante CI.
- Use SCA, SAST, OSV-Scanner e inventário por artefato.

## Como mitigar

- Adote `ignore-scripts` em npm e desative hooks que não sejam necessários.
- Use proxies ou registries privados como ponto de revisão.
- Gere SBOM e execute [SCA](../defesas/sca-e-analise-de-composicao.md).
- Atualize em mudanças controladas e preserve o [lockfile](../defesas/lockfiles-e-pinning.md).
