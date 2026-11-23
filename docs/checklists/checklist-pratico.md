# Checklist prático

Use os checkboxes em pull requests, revisão de arquitetura e controles de pipeline. Cada item aponta para a defesa correspondente.

## Desenvolvedor

- [ ] Commitei o lockfile do projeto e o CI usa instalação reproduzível: [Lockfiles e pinning](../defesas/lockfiles-e-pinning.md).
- [ ] Dependências diretas e transitivas foram revisadas antes da aprovação: [Análise de composição](../defesas/sca-e-analise-de-composicao.md).
- [ ] Usei apenas registros e índices aprovados: [Registro privado e proxies](../defesas/registro-privado-e-proxies.md).
- [ ] Desabilitei scripts de instalação que não são necessários: [Hardening por ecossistema](../defesas/hardening-por-ecossistema.md).
- [ ] Atualizei dependências em mudanças pequenas e revisei o changelog: [Lockfiles e pinning](../defesas/lockfiles-e-pinning.md).
- [ ] Gere o SBOM do artefato efetivamente construído: [SBOM e inventário](../defesas/sbom-e-inventario.md).
- [ ] Verifiquei origem e proveniência antes do deploy: [SLSA e proveniência](../defesas/slsa-e-proveniencia.md).
- [ ] Revoguei tokens antigos e ativos de publicação que não são necessários: [Comprometimento de mantenedor](../vetores-de-ataque/comprometimento-de-mantenedor.md).

## Engenheiro de segurança

- [ ] O pipeline bloqueia vulnerabilidades críticas acordadas pela política: [SCA](../defesas/sca-e-analise-de-composicao.md).
- [ ] SBOM é publicado e correlacionado ao hash do artefato: [SBOM e inventário](../defesas/sbom-e-inventario.md).
- [ ] Runners são efêmeros e segredos usam escopo mínimo: [Ataques a build e CI](../vetores-de-ataque/ataques-a-build-e-ci.md).
- [ ] A política proíbe `--extra-index-url` em instalações privadas PyPI: [Hardening por ecossistema](../defesas/hardening-por-ecossistema.md).
- [ ] Releases usam identidade curta e atestado verificável: [SLSA e proveniência](../defesas/slsa-e-proveniencia.md).
- [ ] Namespaces internos estão reservados ou protegidos: [Dependency Confusion](../vetores-de-ataque/dependency-confusion.md).
- [ ] A versão mínima de liberação é aplicada quando disponível: [Hardening por ecossistema](../defesas/hardening-por-ecossistema.md).
- [ ] Ativos são monitorados por nome novo, hash inesperado e origem não autorizada: [Pacotes maliciosos](../vetores-de-ataque/pacotes-maliciosos.md).
- [ ] Executei verificações com ferramentas do [catálogo essencial](../ferramentas/ferramentas-essenciais.md).
