# SBOM

## Visão geral

No Quor, cada imagem publicada inclui uma SBOM (Software Bill of Materials). Ela registra os componentes presentes na imagem, com versões e licenças, permitindo rastreabilidade e auditoria.

As SBOMs são geradas durante o build e publicadas como artefatos de segurança junto com assinaturas e metadados de proveniência. O formato disponível segue os padrões de mercado, como SPDX e CycloneDX.

## Como acessar

Após abrir uma imagem, por exemplo `https://app.quor.dev/images/102/default/nginx/details`, navegue até a aba **SBOM** em `https://app.quor.dev/images/102/default/nginx/details/sbom`. Nessa aba, você pode ver os componentes presentes na imagem, suas versões e licenças. Se desejar, também pode baixar o arquivo SBOM.

![Detalhes da imagem - Versions](assets/sbom-details-versions.png)

![Detalhes da imagem - SBOM](assets/sbom-details-sbom.png)

1. Abra o catálogo de imagens.
2. Clique na imagem desejada.
3. Na página de detalhes, acesse a aba **SBOM**.
4. Selecione a versão e a arquitetura desejadas.
5. Faça o download do SBOM completo.
