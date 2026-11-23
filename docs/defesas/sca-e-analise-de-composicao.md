# SCA e análise de composição

## O que é

SCA (Software Composition Analysis) identifica componentes de terceiros e avalia vulnerabilidades, licenças e outros riscos. O resultado é útil apenas quando corresponde ao grafo efetivo e usa dados atualizados.

## Como funciona

- Um scanner lê manifesto, lockfile, imagem ou artefato.
- Extrai componentes, versões e relações.
- Correlaciona componentes com bases como OSV, NVD/CVE e bases comerciais.
- Produz achados com severidade, contexto e recomendação.

## Ferramentas

| Ferramenta | Tipo | Licença | Integração |
|---|---|---|---|
| OWASP Dependency-Check | SCA | Open source | CI e linha de comando |
| Snyk | SCA/comercial | Comercial com opções gratuitas | CI, IDE e containers |
| Dependabot | Atualização | GitHub | Pull requests automáticos |
| Renovate | Atualização | Open source/comercial | Plataformas Git e CI |
| OSV-Scanner | Consulta de vulnerabilidades | Open source | Linha de comando e CI |

## Como detectar

- Falhas em CI relacionadas a dependências.
- Vulnerabilidades transitivas sem alteração direta.
- Versões sem correspondência em bases ou vulnerabilidades sem CVE.
- Componentes presentes no artefato final mas ausentes no SBOM.

## Como mitigar

- Coloque SCA no gate de CI após a resolução efetiva.
- Compare resultados com SBOM e lockfiles.
- Trate vulnerabilidades sem CVE por pacote, versão e evidência.
- Revise falso positivo, alcance e exposição antes de bloquear.
- Consulte [ferramentas essenciais](../ferramentas/ferramentas-essenciais.md).
