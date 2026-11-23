# Hardening por ecossistema

Estas configurações são um ponto de partida. Teste cada opção na versão real do gerenciador e confirme compatibilidade com o pipeline.

## npm

```bash
npm config set ignore-scripts true
npm config set allow-git false
npm config set audit true
# npm >= 11: restringe releases muito recentes
npm config set min-release-age 86400000
```

Desabilitar scripts evita hooks implícitos em npm. Bloquear Git impede dependências externas por URL; auditoria automatizada sinaliza vulnerabilidades conhecidas. A idade mínima permite aplicar período de observação antes de consumir releases recentes.

## PyPI e pip

```bash
pip install --index-url https://pypi.internal.example/simple pacote-interno
pip-compile --generate-hashes requirements.in
pip install --require-hashes -r requirements.txt
```

Use `--index-url` para uma origem definida e nunca `--extra-index-url` em ambientes privados. Hashes exigem que o arquivo baixado corresponda ao valor aprovado.

## Go

```bash
go mod tidy
go mod verify
```

Fixe o proxy e o sumdb no ambiente ou no `go.env` do módulo. `go mod verify` confirma os módulos em cache contra hashes registrados no `go.sum`.

## Cargo

```bash
# Atualize somente após revisão
cargo update --precise <versao>
```

Commit `Cargo.lock` em aplicações e execute builds em ambientes com acesso controlado. Build scripts podem executar durante compilação, então revise novas dependências.

## Maven

Adicione o Maven Enforcer Plugin e regras para exigir versões reais e dependências de release:

```xml
<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-enforcer-plugin</artifactId>
  <configuration>
    <rules>
      <requireReleaseDeps/>
    </rules>
  </configuration>
</plugin>
```

Fixe versões no POM ou BOM e permita apenas repositórios aprovados.

## NuGet

```xml
<PropertyGroup>
  <RestorePackagesWithLockFile>true</RestorePackagesWithLockFile>
</PropertyGroup>
```

Commit `packages.lock.json` e limite feeds de restauração no CI. Revisão de lock impede que uma atualização implícita altere o conjunto enviado ao build.
