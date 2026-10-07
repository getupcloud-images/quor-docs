---
description: Explore o catálogo de imagens de containers seguras do Quor, com versões, SBOM, assinaturas e changelog de cada imagem.
keywords: catálogo de imagens de containers, imagens Quor, imagens seguras, versões de imagens, SBOM
---

# Catálogo de imagens

## Browse images

A seção Browse images exibe o catálogo de imagens em formato de cards, permitindo a identificação rápida e o acesso à porcentagem de redução de vulnerabilidades em relação a imagem pública.

![Imagens](assets/catalog/explore-images.png)

Para cada imagem, tem-se a seguintes ações disponíveis:

- **Subscrever imagem** → para imagens disponíveis no seu plano;
- **Contate-nos** → para imagens disponíveis apenas no plano Enterprise (pós Trial);
- **Comando docker pull** → para imagens já subscritas e prontas para uso.

!!! note "Importante"

    O path da imagem (necessário para o docker pull) só é exibido após a subscrição.

Além da lista, a tela oferece recursos para localizar imagens específicas.

- **Busca por texto:** Permite pesquisar imagens diretamente pelo nome (ex.: node, nginx, argocd).
- **Mostrar imagens subscritas:** Alterna a visualização para exibir apenas as imagens com inscrição ativa na sua organização.
- **Categorias:** Filtra o catálogo por caso de uso (_Languages & frameworks_, _Integration & delivery_, _Networking_, _Security_, _Message queues_, etc.).
- **Arquteturas:** Filtra as imagens por arquitetura de processador (_x86-64_, _ARM 64_).
- **Distro/Imagem base:** Filtra imagens pela distribuição Linux base (ex.: _Alpine_, _Distroless_).

## Comparação de imagens

Apresentação detalhada da postura de segurança, tamanho e composição entre a imagem do Quor e a imagem pública correspondente.

![Comparação de imagens](assets/catalog/image-details/comparison-1.png)

<p class="image-date"><strong>Data de referência:</strong> 07/10/2026</p>

### **Componentes da comparação**

**Filtros:**

- **Versão:** Define a tag ou versão da imagem a ser analisada (ex.: Latest).
- **Período:** Define a janela temporal do gráfico histórico (ex.: Last month).

**Métricas principais:**

Apresenta o endereço de registro (_registry URL_) de cada imagem e compara os seguintes indicadores:

- CVEs: Quantidade total de vulnerabilidades conhecidas e o percentual de redução obtido (ex.: 8 vs. 177, com redução de `⬇ 95,5%`).
- Packages: Quantidade de pacotes e dependências instaladas em cada imagem.
- Compressed size: Tamanho comprimido da imagem em megabytes, demonstrando a redução no consumo de transferência e armazenamento.

**Vulnerabilidades por severidade**

Detalhamento das vulnerabilidades por nível de severidade (_Critical_, _High_, _Medium_, _Low_, _Unknown_):

- Exibe a comparação direta do número de falhas (Quor vs. Public) e o percentual de mitigação atingido em cada nível (ex.: 0 vs. 12 com ⬇ 100% de redução em falhas críticas).

**Gráficos de evolução temporal**  
Dois gráficos de área comparam o histórico de vulnerabilidades da imagem do Quor em relação à imagem pública ao longo do período selecionado:

- Exibe a variação diária de CVEs identificadas.
- Utiliza cores correspondentes à gravidade para demonstrar a estabilidade da imagem ao longo do tempo.

**Atestações e Conformidade**  
Compara a presença de atestados de segurança e artefatos de conformidade em cada build:

- **Imagem Quor:** Lista as atestações ativas e verificadas, como SLSA provenance, Cyclone DX SBOM, SPDX SBOM e declarações VEX.
- **Imagem Pública:** Sinaliza a ausência de atestações de segurança (_No attestations_).

**Comparativo do Tamanho Comprimido**  
Um gráfico de barras dedicado que ilustra visualmente a diferença de peso entre as duas imagens, exibindo a porcentagem exata de otimização (ex.: ⬇ 78% smaller).

![Comparativo do Tamanho Comprimido](assets/catalog/image-details/comparison-2.png)

<p class="image-date"><strong>Data de referência:</strong> 07/10/2026</p>

**Detalhes de Vulnerabilidades**

- Vulnerabilidades (Vulnerabilities details): Lista cada registro de falha ativa por CVE ID e nível de Severity (ex.: _Low_, _Critical_, _High_). A paginação facilita a navegação e evidencia a drástica diferença no volume de ameaças (ex.: 2 páginas na imagem Quor vs. 36 páginas na imagem pública).

![Vulnerability details](assets/catalog/image-details/comparison-3.png)

<p class="image-date"><strong>Data de referência:</strong> 07/10/2026</p>

!!!note "Acesso às abas SBOM e Provenance"

    Para informações sobre a composição completa de softwares ou proveniência do build, acesse as abas **SBOM** e **Provenance**.

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
