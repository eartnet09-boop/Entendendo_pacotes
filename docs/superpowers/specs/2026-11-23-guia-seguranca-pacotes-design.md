# Design — Guia de Segurança de Pacotes e Cadeia de Suprimentos de Software

Data: 2026-11-23
Status: aprovado pelo usuário

## Intent (o porquê)

Construir um repositório GitHub de documentação em pt-BR, profissional e didático, que sirva como referência defensiva sobre pacotes de software: anatomia, gerenciadores, vetores de ataque à cadeia de suprimentos e defesas práticas (SBOM, SLSA, SCA, hardening por ecossistema). Público: desenvolvedores, DevSecOps, AppSec e estudantes.

## Goals

- Cobrir a estrutura obrigatória da Seção 3 do prompt (Minimal Root, máxima navegabilidade).
- Cada arquivo de ataque/defesa com seção fixa: o que é / como funciona / exemplo real / como detectar / como mitigar.
- Diagramas Mermaid (ciclo de vida do pacote; defesa em camadas), tabelas comparativas e blocos de código com comandos exatos de hardening.
- Dados com fonte e ano verificados via busca web (ENISA, OpenSSF, OWASP, Sonatype); formulação qualitativa quando não houver fonte confiável.
- Links relativos entre arquivos, siglas expandidas na primeira menção de cada arquivo.
- Commits semânticos, um por etapa da ordem sugerida.

## Non-goals / Anti-goals

- Nenhum código malicioso, PoC de ataque ou payload — apenas descrição conceitual e defesa.
- Nenhum dado inventado; sem número sem fonte verificável.
- Não descrever gerenciadores de forma enciclopédica — priorizar o "porquê de segurança".
- Não tocar nos outros projetos da pasta pai.

## Constraints

- Idioma: pt-BR. Tom: técnico, direto, orientado à defesa.
- Repositório git independente em `/home/exped/Projetos/repositório_pacotes`.
- Conteúdo exclusivamente documental (Markdown + Mermaid).

## Approaches (decisões)

| Decisão | Escolha | Por quê |
|---|---|---|
| Nome do repo | `guia_seguranca_pacotes_supply_chain` | opção padrão sugerida pelo usuário |
| Licença | MIT | comum em guias técnicos; uma linha para trocar se preferir CC-BY-SA |
| Dados estatísticos | buscar via web antes de escrever | o usuário exige fonte + ano e proíbe inventar dados |
| Commits | `git init` + um commit semântico por etapa | ordem: README → glossário → fundamentos → vetores → defesas → ferramentas → checklists |
| Padrão por arquivo | seções fixas idênticas entre vetores e defesas | leitura paralela e previsibilidade |

## Parts do "how" decididas

- Estrutura de diretórios idêntica à Seção 3 do prompt.
- README com badges (Shields.io), tabela de respostas rápidas, Mermaid do ciclo de vida com ataques/defesas marcados, Quick Start em 3 passos.
- `SECURITY.md` com canal de contato e caráter puramente educacional.
- `.github/copilot-instructions.md` orientando assistentes de código sobre o repositório.

## O que fica para o executor

- Pesquisar dados atuais (2025-2026) com fonte e ano.
- Escrever todos os arquivos conforme Seções 4-6.
- Validar Mermaid e links relativos ao final.
- Executar os commits na ordem definida.
