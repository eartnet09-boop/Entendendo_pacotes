# SBOM e inventário

## O que é

SBOM (Software Bill of Materials) é uma lista estruturada de componentes presentes em um software ou artefato. O inventário ajuda equipes a localizar componentes afetados por vulnerabilidades e a documentar dependências terceiras.

## Como funciona

- Um analisador identifica componentes no diretório, arquivo de lock, imagem ou artefato construído.
- Cada componente recebe nome, versão, fornecedor ou package URL e relações quando disponíveis.
- O SBOM é publicado junto ao artefato ou armazenado no repositório de evidências.
- Ferramentas de SCA correlacionam componentes com bases de vulnerabilidades.

## CycloneDX vs SPDX

| Aspecto | CycloneDX | SPDX (System Package Data Exchange) |
|---|---|---|
| Mantenedor | OWASP | Linux Foundation |
| Foco | Segurança de software e cadeia de componentes | Inventário, licenças e metadados |
| Formatos | JSON e XML | JSON, YAML, RDF, tag-value |
| Bom para | CI, resposta a vulnerabilidade e integridade | Auditoria, licenças e conformidade |

## Como gerar

Exemplo com syft:

```bash
syft dir:. -o cyclonedx-json > sbom.json
```

Prefira gerar a partir do artefato final ou da build efetiva. Não confie apenas em um SBOM produzido antes da resolução.

## Como detectar

- Compare o SBOM com o lockfile e o diretório de dependências.
- Monitore componentes sem versão ou origem.
- Detecte componentes presentes no artefato, mas ausentes no código-fonte declarado.
- Associe o SBOM à identidade do build.

## Como mitigar

- Gere SBOM em CI e retenha-o com o artefato.
- Assine ou ateste o SBOM quando necessário.
- Use o SBOM como entrada para SCA e resposta a incidentes.
- Consulte [ferramentas essenciais](../ferramentas/ferramentas-essenciais.md).
