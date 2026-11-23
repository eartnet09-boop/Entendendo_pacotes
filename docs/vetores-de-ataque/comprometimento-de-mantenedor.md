# Comprometimento de mantenedor

## O que é

Comprometimento de mantenedor ocorre quando identidade, credencial ou workflow de publicação de uma pessoa ou equipe confiável é tomado ou usado indevidamente. Pacotes legítimos passam a distribuir conteúdo alterado sem envolver a aplicação consumidora diretamente.

## Como funciona

1. O atacante obtém ou reutiliza uma sessão, token, chave ou conta de publicação.
2. Ele publica uma versão ou modifica metadados pelo canal legítimo.
3. Dependentes podem receber a alteração por resolução de versão ou atualização automática.
4. A alteração é distribuída pelo registry como se fosse uma publicação autêntica.

## Exemplo real

Incidentes envolvendo contas de mantenedores foram documentados em ecossistemas npm e PyPI. Casos públicos têm mostrado desde exposição de credenciais até sequestro de conta. A lição comum é que segurança da identidade de publicação é tão importante quanto segurança do código-fonte.

## Como detectar

- Monitore publicação fora de horário ou por identidade inesperada.
- Exija autenticação multifator para contas de manutenção e publicação.
- Compare hashes, proveniência e commit associado a cada artefato.
- Revise logs de token, releases e alterações de metadados.

## Como mitigar

- Use autenticação multifator resistente a phishing e credenciais de publicação temporárias.
- Reduza escopos e revogue tokens que não estejam em uso.
- Use ambientes de CI isolados e identidades distintas para build e publicação.
- Exija aprovação humana e proveniência verificável para releases.
- Consulte [SLSA e proveniência](../defesas/slsa-e-proveniencia.md).
