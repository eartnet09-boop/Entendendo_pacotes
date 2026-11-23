# Registro e distribuição

## Como um pacote é publicado

O processo típico começa no código-fonte ou build, passa pela geração do artefato, inclui metadados e termina no upload autenticado para um registry. Depois da publicação, o registro distribui o pacote para build pipelines e máquinas consumidoras.

```text
build -> metadados -> autenticacao -> upload -> indexacao -> download
```

Mudanças em qualquer etapa podem alterar o conteúdo entregue. Por isso, proveniência e políticas de acesso devem acompanhar o processo.

## Assinatura e verificação

Assinatura criptográfica permite verificar autoria ou integridade, mas não substitui revisão do código. A maioria dos ecossistemas oferece mecanismos opcionais ou diferenciais de assinatura; implementações específicas variam.

Tecnologias como Sigstore e cosign podem representar identidades de publicação e atestados. O consumidor deve verificar a assinatura contra identidade, workflow e política esperados, não apenas contra um certificado que exista.

## Público vs privado

Registries públicos oferecem ampla disponibilidade e descoberta, mas exigem controles contra nomes semelhantes e pacotes maliciosos. Registries privados são úteis para armazenar artefatos internos, aplicar cache, controlar fontes permitidas e impedir resolução pública ambígua.

Use um registro privado quando o pacote contém propriedade interna, há requisitos de auditoria ou o ambiente precisa operar com fontes aprovadas. Repositórios privados não eliminam risco: dependências externas ainda precisam de análise.

Veja [registro privado e proxies](../defesas/registro-privado-e-proxies.md).

## Papel do mirror ou proxy

Um mirror ou proxy pode centralizar downloads, manter cache auditável e bloquear componentes indevidos. Funciona como ponto de controle, mas exige monitoramento de disponibilidade e integridade. Sem pinning ou lista permitida, um proxy pode apenas repetir a mesma resolução do registro público.
