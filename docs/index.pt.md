# Sobre Quor

## O desafio da segurança em containers

O Quor nasceu da **experiência prática em ambientes Kubernetes, especialmente em empresas de operação crítica**, acompanhando de perto como o **alto volume de vulnerabilidades (CVEs)** se tornou um fardo para equipes de desenvolvimento e segurança.

Esse volume drena recursos, atrasa entregas e aumenta a exposição a ataques, especialmente quando as empresas utilizam imagens cuja origem e integridade dos componentes não são conhecidas.

**A visão do Quor é clara**: reduzir a superfície de ataque e evitar CVEs, ao mesmo tempo em que amplia a visibilidade e rastreabilidade da cadeia de software.

## O que é o Quor

O Quor é um **catálogo de imagens de containers seguras, sem CVEs conhecidas e prontas para produção**.

Essas imagens são construídas a partir de bases mínimas, com **assinaturas digitais** e **SBOMs (_Software Bill of Materials_)** que garantem integridade e a rastreabilidade dos componentes contidos em cada imagem; o excesso de software é removido, tornando as imagens mais leves, seguras e performáticas.

Como resultado, as imagens do catálogo Quor são publicadas com **zero ou próximo de zero vulnerabilidades** e acumulam falhas em um ritmo muito menor ao longo do tempo, quando comparadas às imagens oficiais.

## Como o Quor ajuda na prática

Com o Quor, as equipes passam a trabalhar com um **catálogo confiável de imagens de container**, no lugar de depender de imagens de origem incerta ou escolhida por conveniência.

Essa ação traz ganhas imediatos:

- **Menos ruído**: a triagem de vulnerabilidades deixa de ser um gargalo, já que as imagens chegam ao seu pipeline com zero ou próximo de zero CVEs conhecidas.
- **Menos risco na _supply chain_**: a proveniência é clara, com integridade atestada por assinaturas e SBOMs.
- **Menor dependência de terceiros**: as correções não ficam à mercê do cronograma do projeto original; elas são aplicadas continuamente no catálogo.

O resultado é um ambiente de produção muito mais seguro e previsível, sem o fardo de remediar manualmente vulnerabilidades divulgadas no _upstream_ e menor exposição a ataques.

!!! note

    O nome Quor vem da ideia de ser o **_'core'_ da segurança em imagens de container**.
    Seu mascote, o porco-espinho, reflete essa visão: um animal discreto, mas com um sistema de defesa altamente sofisticado.
