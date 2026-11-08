# CORRECTIONS.md — hnvitalsigns

Base: HL7Norway/hnvitalsigns@7f3496b (master). Usuário autorizou implementação de todas as propostas viáveis.

## Implementado

1. **`LICENSE`** (novo) — CC0 1.0 Universal, consistente com outros IGs HL7 Poland já auditados.
2. **`README.md`** (expandido) — propósito, tecnologias, versões, licença, uso, contribuição.
3. **`.gitignore`** (expandido) — ignora `.vs/`, `*.zip`, `node_modules/`, `package-lock.json`, `Thumbs.db`.
4. **Remoção do rastreamento: `.vs/`** — arquivos de configuração do Visual Studio (`.vs\slnx.sqlite`, `.vs\*.suo`, `.vs\*.json`).
5. **Remoção do rastreamento e do disco: `v0.3 – Kopi\`** — pasta duplicada de `v0.3\`.
6. **Remoção do rastreamento e do disco: `openehr.zip`, `v0.1.zip`, `v0.6.zip`** — binários versionados desnecessários.

## Não implementado (decisão do mantenedor / revisão clínica)
- REA-005: tags de versão (git tag) em vez de pastas v0.x no mesmo branch.
- REA-007: CI/validação FHIR automatizada.
- REA-008: lock files consistentes entre versões.
- REA-009: revisão de status draft dos perfis FHIR (domínio clínico).

## Validação
- `git status` confirma remoções e adições corretas.
- Não executado: build FHIR/SUSHI (não aplicável).
