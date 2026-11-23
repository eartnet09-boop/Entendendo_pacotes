# Glossário

Este glossário define os termos usados neste guia. A sigla da entrada é expandida na primeira menção e a linguagem é voltada à segurança defensiva.

| Termo | Definição |
|---|---|
| **Pacote** | Unidade distribuível de código, metadados e recursos publicada em um registro de pacotes. Sua integridade importa porque o conteúdo pode ser executado por scripts de instalação ou incorporado diretamente em uma aplicação. |
| **Dependência direta** | Pacote declarado explicitamente pelo projeto ou por sua equipe. Deve ter responsável, versão conhecida e revisão de atualizações. |
| **Dependência transitiva** | Pacote instalado por outra dependência, sem declaração direta no projeto. Vulnerabilidades nessa cadeia podem ser menos visíveis e exigir análise do grafo completo. |
| **Lockfile** | Arquivo que registra versões exatas e, em alguns ecossistemas, hashes resolvidos do grafo de dependências. Deve ser revisado e versionado para reduzir variações entre ambientes. |
| **SemVer** (Versionamento Semântico) | Convenção `MAJOR.MINOR.PATCH`: mudanças incompatíveis incrementam MAJOR, funcionalidades compatíveis incrementam MINOR e correções incrementam PATCH. A convenção ajuda na mudança controlada, mas não prova segurança. |
| **Registry** | Serviço que hospeda, autentica, indexa e distribui pacotes. O registro é parte da cadeia de confiança e deve ter política clara de origem e acesso. |
| **SBOM** (Software Bill of Materials) | Lista estruturada de componentes, versões e relações presentes em um software ou artefato. Permite resposta rápida a vulnerabilidades e auditoria de conformidade. |
| **CycloneDX** | Formato aberto de SBOM voltado a segurança da cadeia de software. Pode representar componentes, vulnerabilidades e metadados de serviços em formatos comuns como JSON e XML. |
| **SPDX** (System Package Data Exchange) | Padrão aberto para comunicação de inventário de software, licenças e informações de componentes. É útil em auditorias de conformidade e inventário. |
| **SLSA** (Supply-chain Levels for Software Artifacts) | Conjunto de níveis progressivos para confiabilidade de builds e proveniência. Cada nível define controles mais fortes sobre origem, construção e integridade dos artefatos. |
| **Proveniência** | Evidência verificável sobre origem e processo que produziu um artefato. Em segurança, permite verificar se o binário corresponde ao código e ao pipeline autorizado. |
| **SCA** (Software Composition Analysis) | Análise que identifica componentes de terceiros e avalia riscos como vulnerabilidades, licenças e integridade. Deve consumir inventários confiáveis e bases atualizadas. |
| **SRI** (Subresource Integrity) | Mecanismo de integridade usado em recursos web que confirma o conteúdo recebido por meio de uma função hash esperada. Evita que mudanças não autorizadas sejam executadas silenciosamente. |
| **CPE** (Common Platform Enumeration) | Convenção estruturada para identificar plataformas e aplicações em bases e ferramentas de gestão de vulnerabilidades. Pode gerar correspondências, mas exige contexto para evitar falso positivo. |
| **OSV** (Open Source Vulnerabilities) | Projeto e esquema de dados para representar vulnerabilidades em software de código aberto por ecossistema e versão. É usado por scanners para correlacionar componentes afetados. |
| **Typosquatting** | Registro de nome semelhante a uma dependência legítima para induzir erro de digitação ou confusão. A defesa inclui revisão humana, allowlists e resolução de nomes. |
| **Dependency Confusion** | Técnica que explora resolvedores quando um nome interno também existe em um registro público. Escopos internos, registros privados e regras de índice são controles essenciais. |
| **Supply Chain Attack** | Ataque que compromete um componente, processo ou identidade usada antes ou durante a entrega do software. Ameaças podem ocorrer em código-fonte, build, registro ou distribuição. |
| **Build Provenance** | Registro ou atestado sobre quem iniciou um build, em qual fonte e quais processos produziram o artefato. Deve ser verificável por assinatura ou sistema de confiança. |
| **Artefato** | Resultado concreto de uma construção, como pacote, imagem de contêiner, biblioteca ou binário. Artefatos precisam de identidade, integridade e rastreabilidade. |
| **Attestation** | Declaração assinada sobre uma propriedade verificável de um artefato ou processo. A assinatura permite que consumidores comprovem que uma afirmação veio de uma origem autorizada. |

Documentos relacionados: [o que é um pacote](fundamentos/o-que-e-um-pacote.md), [lockfiles e pinning](defesas/lockfiles-e-pinning.md), [SBOM e inventário](defesas/sbom-e-inventario.md), [SLSA e proveniência](defesas/slsa-e-proveniencia.md) e [análise de composição](defesas/sca-e-analise-de-composicao.md).
