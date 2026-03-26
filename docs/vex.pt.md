# VEX

## Introdução

VEX (Vulnerability Exploitability eXchange) adiciona contexto de explorabilidade aos achados de CVE.
Ele complementa o resultado de scanners ao indicar se a vulnerabilidade é relevante para uma versão específica da imagem.

## VEX e SBOM

- **SBOM** responde o que compõe a imagem.
- **VEX** responde se as CVEs reportadas são exploráveis naquele contexto.

## Modelo de status

O Quor segue os status padrão de VEX:

- `not_affected`
- `affected`
- `fixed`
- `under_investigation`

## VEX no Quor

Para todas as imagens e versões do Quor, o VEX é publicado junto com o conjunto de evidências da imagem:

- SBOM
- Assinatura
- Atestados de proveniência

## Impacto prático no CI/CD

O uso de VEX reduz ruído na triagem de vulnerabilidades e ajuda a priorizar risco real nos pipelines.
