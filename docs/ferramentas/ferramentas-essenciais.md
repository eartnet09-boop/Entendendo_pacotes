# Ferramentas essenciais

Nesta tabela, “grátis” indica disponibilidade sem licença comercial exigida para uso básico; políticas e recursos gerenciados podem ter limites.

| Ferramenta | Propósito | Ecossistemas | Tipo | Comando de exemplo |
|---|---|---|---|---|
| **syft** | Gerar SBOM em formatos CycloneDX ou SPDX | Containers, diretórios e artefatos | Open source/grátis | `syft dir:. -o cyclonedx-json > sbom.json` |
| **cosign / Sigstore** | Assinar, atestar e verificar artefatos | Containers e artefatos com integração | Open source/grátis | `cosign verify-attestation <artefato>` |
| **OSV-Scanner** (Open Source Vulnerabilities) | Consultar vulnerabilidades por componente | npm, PyPI, Go, Maven, Cargo e outros | Open source/grátis | `osv-scanner --lockfile package-lock.json` |
| **OpenSSF Scorecard** | Avaliar práticas de segurança de projetos open source | Repositórios GitHub | Open source/grátis | `scorecard --repo=github.com/org/repo` |
| **Dependabot** | Atualizar dependências e indicar vulnerabilidades | Vários, em repositórios GitHub | Grátis | Configurado no GitHub |
| **Renovate** | Automatizar revisões e atualização de dependências | Vários, em plataformas Git | Open source/comercial gerenciado | Configurado por `renovate.json` |
| **OWASP Dependency-Check** | Analisar composição e vulnerabilidades | Java, Node.js e outros | Open source/grátis | `dependency-check --scan . --format JSON` |

## Combinação recomendada

Fluxo inicial:

```text
syft -> OSV-Scanner -> cosign -> OpenSSF Scorecard
```

1. `syft` gera o inventário do artefato.
2. `OSV-Scanner` correlaciona componentes e vulnerabilidades.
3. `cosign` verifica assinatura ou atestado antes do deploy.
4. OpenSSF Scorecard fornece contexto sobre práticas do projeto, sem substituir análise humana.

Complementos:

- Use [SBOM e inventário](../defesas/sbom-e-inventario.md) para definir o artefato esperado.
- Use [SCA](../defesas/sca-e-analise-de-composicao.md) como gate no pipeline.
- Use [SLSA e proveniência](../defesas/slsa-e-proveniencia.md) para verificar origem e build.
- Use [lockfiles e pinning](../defesas/lockfiles-e-pinning.md) para tornar a resolução reproduzível.
