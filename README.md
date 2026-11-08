# hnvitalsigns

FHIR profiler for vitalparametre (vital signs).

## Descrição

Implementation Guide / perfis FHIR R4 para sinais vitais da região Helse Nord (Noruega).
O repositório contém StructureDefinitions, ValueSets, Extensions, archetypes openEHR (.adl)
e templates (.oet) para parâmetros como pressão arterial, frequência cardíaca,
saturação de oxigênio, respiração, temperatura, peso e altura.

## Versões

O histórico do repositório mantém versões sequenciais em pastas `v0.1` a `v0.8`.
A versão mais recente é `v0.8`. As pastas mais antigas são mantidas por referência histórica.

## Tecnologias

- FHIR R4 (4.0.0)
- openEHR archetypes (.adl) e templates (.oet)
- Dependências: simplifier.core.r4, hl7.fhir.no.basis

## Licença

Este repositório é publicado sob a licença [CC0 1.0 Universal](LICENSE) (domínio público).

## Uso

Os arquivos XML em `*.xml` são perfis StructureDefinition FHIR. Os arquivos `.adl`
são archetypes openEHR e os `.oet` são templates openEHR.

Não há build automatizado nem CI configurado neste repositório. Para validar os perfis
FHIR, utilize um validador FHIR (ex.: FHIR Validator) ou SUSHI com as dependências
listadas em `v0.6/package.json` e `v0.6/fhirpkg.lock.json`.

## Contribuição

Abra uma Issue para discutir mudanças antes de enviar um Pull Request.
