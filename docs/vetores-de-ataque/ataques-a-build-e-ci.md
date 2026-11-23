# Ataques a build e CI

## O que é

Ataques a build e CI comprometem o processo que transforma código-fonte em artefato. Um pipeline protegido apenas no repositório pode publicar binários alterados quando executores, segredos ou dependências de build são comprometidos.

## Como funciona

1. O atacante compromete o pipeline, um runner, uma ação reutilizável ou uma entrada de build.
2. O processo gera um artefato não equivalente ao código-fonte esperado.
3. Metadados ou versões podem fazer o artefato parecer uma build legítima.
4. Consumidores recebem o artefato pela confiança do registro ou canal de distribuição.

## Exemplo real

O incidente da Codecov em 2021 mostrou como uma alteração em um componente de CI pode afetar variáveis sensíveis de clientes. O ataque à cadeia SolarWinds em 2020 demonstrou o impacto de comprometimento no processo de construção e distribuição. Ambos reforçam a necessidade de verificar artefatos independentemente do canal.

## Como detectar

- Compare artefatos reproduzíveis ou compare hashes esperados.
- Monitore runners, actions/plugins, processos filhos e variáveis de ambiente.
- Verifique identidade de build, commit, workflow e proveniência.
- Gere SBOM a partir do artefato publicado, não apenas do checkout.

## Como mitigar

- Use runners efêmeros e rede limitada.
- Conceda segredos somente ao job que os usa e aplique escopo mínimo.
- Pinne actions por commit ou hash e revise atualizações.
- Separe build de publicação e use identidade curta.
- Adote níveis progressivos de [SLSA e proveniência](../defesas/slsa-e-proveniencia.md).
