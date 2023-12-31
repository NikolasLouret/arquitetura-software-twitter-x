# Twitter Architecture Analysis

Este repositório contém informações e análises detalhadas sobre a arquitetura do Twitter. O objetivo deste trabalho é fornecer uma visão geral abrangente da infraestrutura, tecnologias e desafios enfrentados pelo Twitter em sua busca para fornecer uma plataforma de mídia social escalável e confiável para bilhões de usuários em todo o mundo.

> [!NOTE]
> Este trabalho é apenas para fins educacionais

## Integrantes

-   [Frederico dos Santos](https://www.ofrederico.com)
-   [Gabriel de Souza](https://www.gabrieldesouza.com)
-   [Gabriel Lima de Souza](https://www.gabriellimadesouza.com)
-   [Nikolas Louret](https://www.nikolaslouret.com)

## Sumário

-   [Twitter Architecture Analysis](#twitter-architecture-analysis)
    -   [Integrantes](#integrantes)
    -   [Sumário](#sumário)
    -   [Introdução](#introdução)
    -   [Características do Sistema](#características-do-sistema)
        -   [Nicho de Mercado](#nicho-de-mercado)
        -   [Número de Clientes](#número-de-clientes)
        -   [Segmentação Geográfica](#segmentação-geográfica)
        -   [Dados Demográficos do Público](#dados-demográficos-do-público)
        -   [Requisitos de Segurança](#requisitos-de-segurança)
    -   [Desafios Técnicos](#desafios-técnicos)
    -   [Arquitetura em Alto Nível](#arquitetura-em-alto-nível)
    -   [Tecnologias e Componentes Principais](#tecnologias-e-componentes-principais)
    -   [Requisitos importantes](#requisitos-importantes)
        -   [1. Escalabilidade:](#1-escalabilidade)
        -   [2. Segurança e privacidade:](#2-segurança-e-privacidade)
        -   [3. Processamento em tempo real](#3-processamento-em-tempo-real)
            -   [Arquitetura antiga](#arquitetura-antiga)
            -   [Nova arquitetura](#nova-arquitetura)
            -   [Evolução da performance do sistema](#evolução-da-performance-do-sistema)
    -   [Conclusão](#conclusão)
    -   [Referências](#referências)

## Introdução

O Twitter é uma das redes sociais mais populares do mundo, com centenas de milhões de usuários ativos diariamente. Para manter sua posição como uma plataforma confiável e escalável, o Twitter desenvolveu uma arquitetura de sistema robusta e altamente distribuída.

Este trabalho explora essa arquitetura em detalhes, destacando seus principais componentes, os desafios técnicos enfrentados pela empresa e como ela lida com questões de escalabilidade e segurança.

## Características do Sistema

Esta seção destaca aspectos que exercem influência significativa na construção e arquitetura do Twitter, tais como o nicho de mercado, volume de clientes e acessos, bem como os requisitos de segurança da aplicação.

### Nicho de Mercado

O Twitter é uma plataforma única e amplamente reconhecida por sua natureza de microblogging, que permite aos usuários compartilhar pensamentos, notícias, opiniões e informações em mensagens curtas, chamadas de "tweets".

Uma das principais características do nicho do Twitter é a instantaneidade. A plataforma é conhecida por ser um dos canais mais rápidos para se manter atualizado sobre eventos e notícias em tempo real. Isso faz com que o Twitter seja uma escolha popular para jornalistas, celebridades, políticos e pessoas comuns que desejam compartilhar e acessar informações instantaneamente.

A ênfase na instantaneidade e disseminação de informações em tempo real no Twitter requer uma arquitetura distribuída altamente escalável e algoritmos sofisticados de classificação de conteúdo para garantir a entrega rápida e relevância dos tweets.

### Número de Clientes

Segundo o "Similarweb" o Twitter ocupa a terceira posição no ranking das redes sociais mais acessadas no mundo, registrando um total de 5,8 bilhões de visitas no último mês. Essa classificação é superada apenas pelo Instagram, em segundo lugar, com 6,4 bilhões de acessos, e pelo Facebook, na liderança, com 16,3 bilhões de acessos. A duração média de cada visita por usuário na plataforma Twitter é de 10 minutos e 37 segundos.

### Segmentação Geográfica

Olhando para a segmentação geográfica da plataforma, o "Similarweb" aponta que o Estados Unidos domina o topo da lista com 23,69% do trafégo de dados realizado, em segundo lugar vem o Japão com 16,43%, seguido por Reino Unido com 5,67%, Brasil com 3,94% e Espanha com 3,23% do total.

### Dados Demográficos do Público

Ao examinarmos a composição do público do Twitter, observamos:

-   66,55% do público é do genêro masculino e 33,45% do gênero feminino
-   58,27% dos usuários tem de 18 a 34 anos de idade
-   A parcela de idosos (65 anos ou mais) que utilizam a plataforma é bem pequena sendo apenas 4,81% do público total

### Requisitos de Segurança

O Twitter como uma rede social, possui dados e informações pessoais de seus usuários sobre sua responsabilidade, por isso, sua arquitetura deve garantir:

-   Criptografia dos dados, para senhas e mensagens diretas dos usuários
-   Monitoramento de conteúdo, para detectar conteúdo malicioso, informações falsas e discurso de ódio
-   Backup e recuperação de dados, para garantir a disponibilidade contínua e redundância dos dados
-   Autenticação forte, para exigir senhas fortes, com o objetivo de impedir senhas comuns
-   Gerenciamento de identidade, para garantir que os usuários alterem e recuperem sua conta
-   Resposta a incidentes, para reagir rapidamente a violações de segurança

## Desafios Técnicos

O Twitter enfrenta diversos desafios técnicos, incluindo:

-   **Escala**: Gerenciar uma plataforma com bilhões de tweets e usuários requer sistemas altamente escaláveis.
-   **Latência**: Fornecer atualizações em tempo real para milhões de usuários simultâneos sem atrasos é crucial.
-   **Consistência**: Manter a consistência dos dados em um ambiente distribuído é um desafio complexo.
-   **Segurança**: Proteger os dados dos usuários contra ameaças é uma prioridade crítica.
-   **Conformidade**: Cumprir regulamentos de privacidade de dados em várias regiões geográficas.

## Arquitetura em Alto Nível

A arquitetura do Twitter é composta por vários componentes interconectados que trabalham juntos para fornecer serviços de mídia social aos usuários. Em um alto nível, a arquitetura pode ser dividida em várias camadas:

1. **Camada de Aplicação**: Esta camada inclui a interface do usuário do Twitter, que os usuários finais acessam por meio de aplicativos da web e móveis.
2. **Camada de Lógica de Negócios**: Aqui, a lógica de negócios do Twitter é implementada, incluindo recursos como publicação de tweets, pesquisa, tendências, e muito mais.
3. **Camada de Armazenamento**: O Twitter lida com uma enorme quantidade de dados, incluindo tweets, seguidores, curtidas e muito mais. Esta camada inclui diversos sistemas de armazenamento, como bancos de dados distribuídos, caches e sistemas de armazenamento de objetos.
4. **Camada de Infraestrutura**: A infraestrutura do Twitter engloba data centers em várias regiões geográficas, balanceadores de carga, sistemas de monitoramento e escalonamento automático.

## Tecnologias e Componentes Principais

1. Alguns dos componentes mais importantes da arquitetura do Twitter incluem:

-   **Manhattan**: O back-end para tweets, mensagens diretas, contas do Twitter e muito mais.
-   **Cache**: Clusters Redis e Memcache: armazenando em cache os usuários, cronogramas, tweets e muito mais.
-   **Kafka**: Um sistema de mensagens distribuído usado para ingestão e processamento de dados em tempo real.
-   **FlockDB**: Banco de dados utilizados para fazer o armazenas os grafos de relacionamentos de seguidores.
-   **Blobstore**: Armazenamento de imagens, vídeos e arquivos grandes onde são guardados centenas de bilhões de objetos.
-   **SQL**: Inclui MySQL, PostgreSQL e Vertica. MySQL/PosgreSQL são usados ​​onde é necessário forte consistência, gerenciando campanhas publicitárias, troca de anúncios, bem como ferramentas internas. Vertica é um armazenamento de colunas frequentemente usado como back-end para o Tableau(usados para gerenciamento dos dados).
-   **Hadoop**: Um framework de computação em nuvem usado para processar grandes conjuntos de dados.

2. Mais sobre o Hadoop:

   2.1 Características
   
- Uma biblioteca de software que permite o processamento distribuído de grandes conjuntos de dados em clusters de computadores usando modelos de programação simples.
- Projetado para escalar desde servidores únicos até milhares de máquinas, cada uma oferecendo computação e armazenamento locais.
- Projetado para detectar e tratar falhas na camada de aplicação

  2.2 Como é utilizado

Segundo a postagem "The Infrastructure Behind Twitter: Scale", retirado do blog de engenharia do Twitter, Hadoop é o back-end do pipeline de log baseado em Scribe, a fim de resolver problemas como a falta de limitação de taxa de clientes seletivos para agregadores, falta de garantia de entrega para categorias e para resolver problemas de corrupção de memória. O Hadoop lida com mais de um trilhão de mensagens por dia e todas elas são processadas em mais de 500 categorias, consolidadas e copiadas seletivamente em todos os clusters.
  
## Requisitos importantes

O desenvolvimento do Twitter, assim como qualquer plataforma de mídia social, implica uma complexidade de requisitos técnicos, experiência do usuário e aspectos comerciais. Nesta seção, serão descritos alguns dos requisitos importantes do Twitter.

### 1. Escalabilidade:

Com base na postagem "The Infrastructure Behind Twitter: Scale", presente no blog de engenharia do Twitter, o data center inaugural do Twitter foi planejado com base em modelagens dos perfis de capacidade e tráfego do sistema conhecido na época. Ao longo de alguns anos, testemunhou-se uma notável expansão, com os data centers alcançando dimensões 400% maiores que o projeto original. Essa expansão destacou uma mudança substancial nas suposições iniciais que guiaram os primeiros projetos de rede, evidenciando a necessidade de ajustes contínuos diante da evolução dinâmica das demandas tecnológicas.

O rápido crescimento do tráfego de dados ressalta a importância de uma arquitetura altamente escalável. Em vez de depender de migrações volumosas e complexas, é crucial construir uma estrutura que permita a adição incremental de capacidade. Isso assegura uma resposta ágil às demandas crescentes, evitando reconfigurações massivas de data centers.

O Twitter enfrentou desafios significativos de capacidade e tráfego de dados devido à alta demanda. Inicialmente, a abordagem envolveu dispositivos de rede com buffers de pacotes profundos para lidar com padrões diversos de tráfego. No entanto, essa abordagem inicial resultou em custos elevados e maior complexidade de hardware. Projetos subsequentes adotaram uma abordagem mais equilibrada, utilizando tamanhos de buffer padrão, recursos de comutação _cut-through_[^1], e otimizações na pilha TCP do lado do servidor para enfrentar _microbursts_[^2], grandes quantidades de dados transmitida em um período muito pequeno, de maneira eficiente. Ao longo desse processo, destacaram-se aprendizados valiosos sobre a importância de adaptabilidade e ajustes contínuos diante das mudanças no ambiente tecnológico:

-   **Arquitetar Além das Especificações:** É crucial projetar além das especificações originais e realizar ajustes rápidos e corajosos, especialmente quando o tráfego se aproxima dos limites previstos.

-   **Depender de Dados e Métricas:** Tomar decisões de projeto com base em dados e métricas é essencial. Além disso, é fundamental garantir que essas métricas sejam compreensíveis para os operadores de rede, especialmente em ambientes hospedados e em nuvem.

-   **Evitar Soluções Temporárias:** Soluções temporárias frequentemente resultam em dívidas tecnológicas. Em vez disso, buscar abordagens sustentáveis e de longo prazo é crucial para lidar eficazmente com desafios de tráfego e capacidade.

### 2. Segurança e privacidade:

Segundo o blog Stronger security for your Twitter account, para garantir a segurança dos usuários no Twitter, a plataforma implementou mecanismos rigorosos de autenticação, com destaque para a utilização de autenticação de dois fatores (2FA) em conjunto com chaves de segurança. As chaves de segurança representam a camada mais robusta de proteção para as contas do Twitter, incorporando salvaguardas integradas que impedem o acesso mesmo em caso de uso em sites de _phishing_[^3]. Ao adotar os padrões de segurança _FIDO_[^4] e _WebAuthn_[^5], a carga de proteção contra tentativas de _phishing_ é transferida do usuário para um dispositivo de hardware. Essas chaves têm a capacidade de distinguir sites legítimos de maliciosos, bloqueando tentativas de _phishing_ que métodos tradicionais, como SMS ou códigos de verificação, não seriam capazes de conter.

Em 2018, a opção de utilizar chaves de segurança foi introduzida como parte das opções de 2FA, inicialmente limitada ao [Twitter.com](https://twitter.com) e não disponível no aplicativo móvel. Além disso, exigia que as contas tivessem outra forma de 2FA habilitada.

Em 2019, houve uma atualização no suporte de chave de segurança, incorporando o padrão _WebAuthn_ mais recente, proporcionando um método de autenticação seguro e reconhecido em toda a WEB.

No ano seguinte, em 2020, foram implementadas melhorias adicionais, incluindo o suporte para chaves de segurança em dispositivos móveis. Em 2021, foi adicionada a capacidade de registrar várias chaves de segurança em uma única conta, permitindo chaves de segurança de backup e facilitando a habilitação de 2FA com múltiplas chaves para contas gerenciadas por várias pessoas.

Recentemente, a plataforma introduziu a opção de usar chaves de segurança como o único método 2FA, permitindo que os usuários inscrevam uma ou mais chaves como a única forma de 2FA em sua conta do Twitter, sem a necessidade de um método de backup, reconhecendo que nem todos têm ou desejam compartilhar um número de telefone para esse fim.

### 3. Processamento em tempo real

Segundo o blog Processing billions of events in real time at Twitter, o Twitter processa aproximadamente 400 bilhões de eventos em tempo real diariamente, gerando petabytes (PB) de dados. Esses eventos provêm de diversas fontes, distribuídas em diferentes plataformas e sistemas de armazenamento.

Para lidar com essa enorme quantidade de dados, a equipe da Twitter Data Platform desenvolveu várias ferramentas internas dedicadas ao processamento em lote, streaming, descoberta e consumo de dados. No entanto, o rápido crescimento dos dados continua a desafiar a infraestrutura de dados, mesmo com as ferramentas existentes.

No que diz respeito ao pipeline de interação e engajamento, a equipe coleta e processa dados em tempo real de vários fluxos, combinando informações de tweets, interações do usuário e logs de servidores e clientes. Esses dados agregados são fundamentais para os serviços de receita de anúncios e produtos de dados do Twitter, fornecendo informações cruciais sobre métricas de impressão e engajamento. A busca eficiente e rápida desses dados de interação, com baixa latência e alta precisão em diferentes data centers, é crucial.

Para atender a essas necessidades, o sistema foi dividido em componentes distintos, incluindo pré-processamento, agregação de eventos e entrega de dados. Essa abordagem permite uma análise robusta e eficaz, garantindo que consultas aos dados de interação sejam realizadas de maneira rápida e precisa em toda a infraestrutura do Twitter.

#### Arquitetura antiga

<div align="center">
    <picture>
        <img alt="Arquitetura lambda antiga" src="./imgs/old-architecture.png" />
    </picture>
    <p>Arquitetura lambda antiga</p>
</div>

A arquitetura anterior é baseada em um modelo lambda, que misturava processamento em lote e em tempo real para analisar dados. Dados de logs do Hadoop[^6] eram processados em lote e armazenados, enquanto dados em tempo real, como tweets recentes, eram armazenados de forma temporária. Isso permitia que o Twitter oferecesse um atendimento ao cliente mais rápido, analisando eventos em tempo real, como interações de clientes e tweets.

No entanto, essa estratégia encontra desafios ao lidar com grandes quantidades de dados em tempo real, o que pode levar à perda de informações e imprecisões nos resultados. Esses problemas se agravam, principalmente, quando há uma grande quantidade de eventos que precisam ser processados em curtos períodos, sobrecarregando os sistemas.

Quando o sistema fica sobrecarregado, algumas partes dele podem ficar mais lentas, causando atrasos e, eventualmente, levando à perda de dados. Para resolver esse problema, a plataforma propos uma nova abordagem, em que os dados são processados continuamente em tempo real, eliminando a necessidade de processamento em lote. Isso tornaria o sistema mais eficiente, reduzindo a latência (tempo de resposta) e evitando perdas de dados.

Essa mudança na arquitetura busca melhorar a precisão das informações fornecidas aos usuários e simplificar o sistema, tornando-o mais ágil e eficaz.

#### Nova arquitetura

<div align="center">
    <picture>
        <img alt="Nova arquitetura em Kafka e Dataflow" src="./imgs/new-architecture.png" />
    </picture>
    <p>Nova arquitetura em Kafka e Dataflow</p>
</div>

A nova arquitetura é baseada nos serviços do Twitter Data Center e no Google Cloud Platform. Os eventos como tweets são processados localmente nos servidores do Twitter e também na nuvem usando os serviços do Google.

No processo local, foi criado sistemas para transformar e encaminhar eventos, garantindo que a informação seja consistente. Esses eventos são então enviados para o Google Cloud, onde passam por um processo de remoção de duplicatas e agregação em tempo real. Os dados resultantes são armazenados no BigTable[^7].

Essa nova abordagem economiza custos e melhora a precisão do processamento em tempo real, eliminando a necessidade de manter diferentes formas de organização de dados em locais diferentes. Em termos mais leigos, o Twitter agora consegue lidar melhor com a enorme quantidade de informações que recebe a cada segundo, garantindo que o que você vê seja preciso, rápido e eficiente.

#### Evolução da performance do sistema

<div align="center">
    <picture>
        <img alt="Comparação de desempenho do sistema para arquiteturas antiga e nova" src="./imgs/evaluation-architectures.png" />
    </picture>
    <p>Comparação de desempenho do sistema para arquiteturas antiga e nova</p>
</div>

A nova arquitetura apresenta vantagens significativas em relação à antiga. Notavelmente, oferece menor latência em comparação com a arquitetura anterior e proporciona maior rendimento. Além disso, destaca-se por lidar de maneira eficiente com a contagem de eventos atrasados, garantindo que nenhum evento seja perdido durante a agregação em tempo real. Uma característica notável é a ausência de componentes em lote na nova arquitetura, simplificando o design e reduzindo os custos computacionais que eram presentes na arquitetura anterior.

## Conclusão

Este trabalho oferece uma visão abrangente da arquitetura do Twitter, destacando seus componentes principais, desafios técnicos e abordagens para escalabilidade e segurança. A arquitetura distribuída do Twitter é um exemplo notável de como uma plataforma de mídia social pode crescer e evoluir para atender às necessidades de milhões de usuários em todo o mundo.

## Apresentação 

-   [Link dos Slides](https://docs.google.com/presentation/d/1TCivC5mpvibkfd0muLWqrfCi3WwaYCozslcB5lW7ivM/edit#slide=id.g531f0fbb07_0_1610)

## Referências

-   [Twitter Engineering Blog](https://blog.twitter.com/engineering/en_us)
    -   [The Infrastructure Behind Twitter: Scale](https://blog.twitter.com/engineering/en_us/topics/infrastructure/2017/the-infrastructure-behind-twitter-scale)
    -   [Manhattan Database for Twitter Scale](https://blog.twitter.com/engineering/en_us/a/2014/manhattan-our-real-time-multi-tenant-distributed-database-for-twitter-scale)
    -   [Stronger security for your Twitter account](https://blog.twitter.com/en_us/topics/product/2020/stronger-security-for-your-twitter-account)
    -   [Processing billions of events in real time at Twitter](https://blog.twitter.com/engineering/en_us/topics/infrastructure/2021/processing-billions-of-events-in-real-time-at-twitter-)
-   [Similar Web](https://www.similarweb.com/pt/website/twitter.com/#geography)

[^1]: Técnica de comutação em redes de computadores utilizada em dispositivos como switches de rede para encaminhar pacotes de dados com a menor latência possível.
[^2]: Eventos de curta duração e alta intensidade em uma rede de computadores, nos quais uma grande quantidade de dados é transmitida em um período muito pequeno.
[^3]: Tipo de ataque cibernético que visa enganar as pessoas para que revelem informações confidenciais, como senhas, informações de cartão de crédito ou detalhes de login.
[^4]: _"Fast Identity Online"_, é uma aliança global de tecnologia que desenvolve padrões abertos para autenticação online mais segura e fácil de usar, buscando criar uma alternativa mais robusta e segura aos métodos tradicionais de autenticação baseados em senhas, como o nome de usuário e senha.
[^5]: Padrão da Web que permite a autenticação forte sem senha para aplicativos e serviços online.
[^6]: Framework de software de _open-source_ projetado para processamento distribuído de grandes conjuntos de dados em _clusters_ de computadores.
[^7]: Banco de dados NoSQL desenvolvido pela Google altamente escalável e projetado para lidar com grandes volumes de dados e operações de leitura e gravação em tempo real.
