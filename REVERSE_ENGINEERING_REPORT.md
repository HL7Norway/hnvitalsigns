# REVERSE ENGINEERING REPORT — HL7Norway/hnvitalsigns

## Repositório original
- Nome: hnvitalsigns
- URL: https://github.com/HL7Norway/hnvitalsigns
- Tipo: Implementation Guide / perfis FHIR R4 para sinais vitais (vitalparametre), região Helse Nord (Noruega)
- Branch: master
- Base: 7f3496b Har oppdatert profilene etter møte DIPS HN 28/1

## Data da auditoria
2026-11-07

## Ferramentas utilizadas
- Git v2.49.0
- PowerShell 5.1
- gh (GitHub CLI), autenticado como admeduardovieira
- Kilo Code (análise estática de arquivos XML/JSON/.adl/.oet)

## Arquitetura identificada
Repositório de definições FHIR R4 para sinais vitais da Helse Nord (Noruega).
Contém StructureDefinitions, ValueSets, Extensions, archetypes openEHR (.adl) e
templates (.oet). Organizado por versões sequenciais (v0.1 a v0.8) + pasta Messaging
+ pasta openehr. Não há código executável; são definições de dados/clínicas.

## Tecnologias e dependências
FHIR R4 (4.0.0), openEHR archetypes/templates, simplifier.core.r4, hl7.fhir.no.basis
(dependências listadas em v0.6/package.json e v0.6/fhirpkg.lock.json).

## Estado de manutenção
- Último commit: 7f3496b (setembro/outubro 2023, mensagens em norueguês)
- 4 Issues (2 abertas: #3 busca em Composition, #4 Uttrekk Q/QR; 2 fechadas)
- 0 PRs no histórico
- Nenhum teste automatizado, CI, lint ou validação FHIR/SUSHI
- Versões múltiplas (v0.1–v0.8) mantidas no mesmo branch sem tagging

## Limitações da investigação
- Não é projeto de código executável; não há ambiente para validar build FHIR
- Não se aplica SUSHI/releaselabel (não há sushi-config.yaml na raiz)
- Segundo repositório da rodada (innrapportering-helseregister) não pôde ser clonado
  (falha de rede/diretório fantasma em todos os caminhos testados); existe na API do GitHub

---

## Problemas encontrados (hnvitalsigns)

| ID | Sev | Status | Local | Problema | Correção aplicada |
|---|---|---|---|---|---|
| REA-001 | P3 | CONFIRMADO | Raiz do repositório | Ausência de arquivo LICENSE; direitos de uso/redistribuição indeterminados | Adicionado LICENSE (CC0 1.0 Universal) |
| REA-002 | P3 | CONFIRMADO | README.md | README mínimo (1 linha); sem instruções de uso, build, contribuição ou versão | README expandido com propósito, tecnologias, versões, licença, uso |
| REA-003 | P2 | CONFIRMADO | .vs\** | Arquivos de configuração do Visual Studio (.vs\slnx.sqlite, .vs\*.suo, .vs\*.json) versionados | .vs/ adicionado ao .gitignore e removido do rastreamento |
| REA-004 | P2 | CONFIRMADO | v0.3 – Kopi\ | Pasta duplicada ("Kopi" = cópia) de v0.3\ com conteúdo idêntico | Pasta v0.3 – Kopi\ removida do rastreamento e do disco |
| REA-005 | P2 | CONFIRMADO | v0.1\ a v0.8\ | Oito versões no mesmo branch sem tagging/release clara | Não corrigido (requer decisão do mantenedor sobre estratégia de versionamento) |
| REA-006 | P3 | CONFIRMADO | Raiz do repositório | Arquivos binários .zip versionados (openehr.zip, v0.1.zip, v0.6.zip) | .zip adicionados ao .gitignore e removidos do rastreamento e do disco |
| REA-007 | P3 | CONFIRMADO | Repositório | Nenhum teste automatizado, CI ou validação FHIR/SUSHI | Não corrigido (requer decisão de CI; sem impacto nos perfis FHIR) |
| REA-008 | P3 | PROVÁVEL | v0.3\fhirpkg.lock.json, v0.6\fhirpkg.lock.json | Lock files presentes apenas em algumas versões, não consistente | Não corrigido |
| REA-009 | P3 | HIPÓTESE | Vários XML FHIR | Muitos perfis com <status value="draft" />; sem indicação de quais estão prontos | Não corrigido (requer revisão clínica de domínio) |
| REA-010 | P3 | CONFIRMADO | .gitignore | .gitignore cobre apenas macOS/AFP; não ignora .vs/, *.zip, node_modules/ | .gitignore expandido (.vs/, *.zip, node_modules/, package-lock.json) |

## Problemas recorrentes
- Issues #3 (busca em Composition, 2020-10-30) e #4 (Uttrekk Q/QR, 2020-12-11) ainda abertas; não resolvidas.
- 0 PRs no histórico — sem registro de correções comunitárias.

## Erros não documentados (novos da auditoria)
REA-001 a REA-010 não têm registro público visível.

## Mudanças implementadas (Fase 2)
1. LICENSE (novo): CC0 1.0 Universal.
2. README.md (expandido): propósito, tecnologias, versões, licença, uso, contribuição.
3. .gitignore (expandido): ignora .vs/, *.zip, node_modules/, package-lock.json, Thumbs.db.
4. Remoção do rastreamento: pasta .vs/ (arquivos do Visual Studio).
5. Remoção do rastreamento e do disco: pasta duplicada v0.3 – Kopi\.
6. Remoção do rastreamento e do disco: openehr.zip, v0.1.zip, v0.6.zip.

## Mudanças NÃO implementadas (requerem decisão do mantenedor ou revisão clínica)
- REA-005: tags de versão (git tag) em vez de pastas v0.x no mesmo branch.
- REA-007: CI/validação FHIR automatizada.
- REA-008: lock files consistentes entre versões.
- REA-009: revisão de status draft dos perfis FHIR (domínio clínico).

## Validação executada
- Verificação estática: git status mostra remoções e adições corretas.
- Não executado: build FHIR/SUSHI (não aplicável; não há ambiente).

## Riscos remanescentes
- Estratégia de versionamento (pastas v0.x vs tags) não resolvida.
- Perfis com status draft podem não estar prontos para produção.

## Recomendações para auditorias futuras
- Definir política de versionamento (tags semânticas).
- Adicionar CI básico para validação de bem-formação dos XML FHIR.
- Revisar quais perfis podem sair do status draft.
