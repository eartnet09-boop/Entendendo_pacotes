# SLSA e proveniência

## O que é

SLSA (Supply-chain Levels for Software Artifacts) é um modelo de progressão que define controles sobre integridade de build e proveniência. Proveniência é uma declaração verificável sobre quem iniciou o processo e como um artefato foi produzido.

## Como funciona

- A origem registra o commit e o workflow autorizado.
- O builder gera o artefato em ambiente controlado.
- Uma proveniência assinada descreve fonte, parâmetros e identidade do builder.
- O consumidor verifica assinatura, identidade e política antes de implantar.

## Níveis

| Nível | Exigência principal | Valor de segurança | Esforço |
|---|---|---|---|
| L1 | Proveniência documentada | Rastreabilidade básica | Baixo |
| L2 | Build sobre plataforma de proveniência resistente | Identidade e origem mais confiáveis | Médio |
| L3 | Build isolado e reforçado | Maior confiança em origem e integridade | Alto |

L3 é uma meta comum para builds críticos automatizados, mas a adoção deve considerar plataforma, fornecedor e processo real.

## Como detectar

- Procure artefatos sem proveniência ou com proveniência não verificável.
- Alerta para workflow diferente do esperado ou identidade não autorizada.
- Compare commit, builder, tags e hash do artefato.
- Examine se o sistema de build usa segredos excessivos ou rede ampla.

## Como mitigar

- Migre builds para plataformas que emitam proveniência.
- Use identidade curta e separada para publicação.
- Assine artefatos e atestados, por exemplo com Sigstore/cosign.
- Verifique atestados no deploy:

```bash
cosign verify-attestation --type slsaprovenance <imagem-ou-artefato>
```

- Consulte [ataques a build e CI](../vetores-de-ataque/ataques-a-build-e-ci.md) e [ferramentas essenciais](../ferramentas/ferramentas-essenciais.md).
