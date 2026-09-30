---
description: Explore o catálogo de imagens de containers seguras do Quor, com versões, SBOM, assinaturas e changelog de cada imagem.
keywords: catálogo de imagens de containers, imagens Quor, imagens seguras, versões de imagens, SBOM
---

# Catálogo de imagens

## Browse images

A seção Browse images exibe o catálogo de imagens em formato de cards, permitindo a identificação rápida e o acesso à porcentagem de redução de vulnerabilidades em relação a imagem pública de cada container.

![Imagens](assets/catalog/explore-images.png)

Para cada imagem, tem-se a seguintes ações disponíveis:

- **Subscribe to image** → para imagens disponíveis no seu plano;
- **Contact us** → para imagens disponíveis apenas no plano Enterprise (pós Trial);
- **Comando docker pull** → para imagens já subscritas e prontas para uso.

!!! note "Importante"

    O path da imagem (necessário para o docker pull) só é exibido após a subscrição.

Além da lista, a tela oferece recursos para localizar imagens específicas.

- **Busca por texto:** Permite pesquisar imagens diretamente pelo nome (ex.: node, nginx, argocd).
- **Only subscribed images:** Alterna a visualização para exibir apenas as imagens com inscrição ativa na sua organização.
- **Categories:** Filtra o catálogo por caso de uso (_Languages & frameworks_, _Integration & delivery_, _Networking_, _Security_, _Message queues_, etc.).
- **Architectures:** Filtra as imagens por arquitetura de processador (_x86-64_, _ARM 64_).
- **Distro/Base image:** Filtra imagens pela distribuição Linux base (ex.: _Alpine_, _Distroless_).

## Detalhes da imagem

Ao clicar em uma imagem, você acessa a página de detalhes com informações completas organizadas em abas:

![Detalhes da imagem - Versions](assets/image-details-versions.png)

### Versions

Lista todas as versões disponíveis da imagem, com data de atualização e comando `docker pull` para cada uma. Ao clicar em uma versão específica, é possível visualizar seus pacotes e vulnerabilidades, além de instruções de scan.

### Quick Start

Guia rápido com instruções de uso da imagem, incluindo exemplos de deploy em Kubernetes, Helm e Dockerfile.

### Specifications

Especificações técnicas da imagem, como arquitetura, tamanho e configurações.

### SBOM

O **SBOM (Software Bill of Materials)** lista todos os pacotes contidos na imagem, com suas respectivas licenças. Você pode selecionar a versão e arquitetura desejadas e fazer download do SBOM completo.

![Detalhes da imagem - SBOM](assets/image-details-sbom.png)

### Provenance

Informações de proveniência da imagem, atestando sua origem e integridade.
Para todas as imagens e versões, esse conjunto inclui SBOM, assinatura, atestados de proveniência e declarações VEX para adicionar contexto de explorabilidade na análise de vulnerabilidades.

### Changelog

O **Changelog** exibe o histórico de vulnerabilidades da imagem ao longo do tempo. Inclui um gráfico de evolução e uma lista detalhada das vulnerabilidades detectadas, com CVE ID, severidade, pacote afetado, versão e status de correção.

![Detalhes da imagem - Changelog](assets/image-details-changelog.png)

## Solicitar novas imagens

O catálogo do Quor é expandido continuamente, com novas imagens adicionadas em ciclos regulares. Além disso, usuários podem solicitar a inclusão de imagens específicas.

### Critérios para solicitação

As solicitações são avaliadas de acordo com os seguintes requisitos:

- O projeto deve ser open source;
- A licença precisa ser compatível com redistribuição;
- A versão solicitada deve estar em suporte ativo de segurança (não EOL).

!!! note

    A verificação de suporte é feita com base em [endoflife.date](https://endoflife.date).
