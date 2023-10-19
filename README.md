# Twitter Architecture Analysis

Este repositório contém informações e análises detalhadas sobre a arquitetura do Twitter. O objetivo deste trabalho é fornecer uma visão geral abrangente da infraestrutura, tecnologias e desafios enfrentados pelo Twitter em sua busca para fornecer uma plataforma de mídia social escalável e confiável para bilhões de usuários em todo o mundo.

## Integrantes
- [Frederico dos Santos](https://www.ofrederico.com)
- [Gabriel de Souza](https://www.gabrieldesouza.com)
- [Gabriel Lima de Souza](https://www.gabriellimadesouza.com)
- [Nikolas Louret](https://www.nikolaslouret.com)

## Sumário

-   [Twitter Architecture Analysis](#twitter-architecture-analysis)
    -   [Sumário](#sumário)
    -   [Introdução](#introdução)
    -   [Características do Sistema](#características-do-sistema)
    -   [Arquitetura em Alto Nível](#arquitetura-em-alto-nível)
    -   [Componentes Principais](#componentes-principais)
    -   [Desafios Técnicos](#desafios-técnicos)
    -   [Escalabilidade](#escalabilidade)
    -   [Disponibilidade](#disponibilidade)
    -   [Segurança](#segurança)
    -   [Conclusão](#conclusão)
    -   [Referências](#referências)

## Introdução

O Twitter é uma das redes sociais mais populares do mundo, com centenas de milhões de usuários ativos diariamente. Para manter sua posição como uma plataforma confiável e escalável, o Twitter desenvolveu uma arquitetura de sistema robusta e altamente distribuída.

Este trabalho explora essa arquitetura em detalhes, destacando seus principais componentes, os desafios técnicos enfrentados pela empresa e como ela lida com questões de escalabilidade e segurança.

## Características do Sistema

Esta seção destaca características do Twitter que impactam em sua construção e arquitetura

1. **Nicho de Mercado**
   
O Twitter é uma plataforma única e amplamente reconhecida por sua natureza de microblogging, que permite aos usuários compartilhar pensamentos, notícias, opiniões e informações em mensagens curtas, chamadas de "tweets". 

Uma das principais características do nicho do Twitter é a instantaneidade. A plataforma é conhecida por ser um dos canais mais rápidos para se manter atualizado sobre eventos e notícias em tempo real. Isso faz com que o Twitter seja uma escolha popular para jornalistas, celebridades, políticos e pessoas comuns que desejam compartilhar e acessar informações instantaneamente.

A ênfase na instantaneidade e disseminação de informações em tempo real no Twitter requer uma arquitetura distribuída altamente escalável e algoritmos sofisticados de classificação de conteúdo para garantir a entrega rápida e relevância dos tweets.

2. **Número de Clientes**

O Twitter ocupa a terceira posição no ranking das redes sociais mais acessadas no mundo, registrando um total de 5,8 bilhões de visitas no último mês. Essa classificação é superada apenas pelo Instagram, em segundo lugar, com 6,4 bilhões de acessos, e pelo Facebook, na liderança, com 16,3 bilhões de acessos. A duração média de cada visita por usuário na plataforma Twitter é de 10 minutos e 37 segundos.

3. **Segmentação Geográfica**

Olhando para a segmentação geográfica da plataforma, o Estados Unidos domina o topo da lista com 23,69% do trafégo de dados realizado, em segundo lugar vem o Japão com 16,43%, seguido por Reino Unido com 5,67%, Brasil com 3,94% e Espanha com 3,23% do total. 

4. **Dados Demográficos do Público**

Ao examinarmos a composição do público do Twitter, observamos:

    - 66,55% do público é do genêro masculino e 33,45% do gênero feminino
    - 58,27% dos usuários tem de 18 a 34 anos de idade
    - A parcela de idosos (65 anos ou mais) que utilizam a plataforma é bem pequena sendo apenas 4,81% do público total

5. **Requisitos de Segurança**

O Twitter como uma rede social, possui dados e informações pessoais de seus usuários sobre sua responsabilidade, por isso, sua arquitetura deve garantir:

- Criptografia dos dados, para senhas e mensagens diretas dos usuários
- Monitoramento de conteúdo, para detectar conteúdo malicioso, informações falsas e discurso de ódio
- Backup e recuperação de dados, para garantir a disponibilidade contínua e redundância dos dados
- Autenticação forte, para exigir senhas fortes, com o objetivo de impedir senhas comuns
- Gerenciamento de identidade, para garantir que os usuários alterem e recuperem sua conta
- Resposta a incidentes, para reagir rapidamente a violações de segurança

## Arquitetura em Alto Nível

A arquitetura do Twitter é composta por vários componentes interconectados que trabalham juntos para fornecer serviços de mídia social aos usuários. Em um alto nível, a arquitetura pode ser dividida em várias camadas:

1. **Camada de Aplicação**: Esta camada inclui a interface do usuário do Twitter, que os usuários finais acessam por meio de aplicativos da web e móveis.
2. **Camada de Lógica de Negócios**: Aqui, a lógica de negócios do Twitter é implementada, incluindo recursos como publicação de tweets, pesquisa, tendências, e muito mais.
3. **Camada de Armazenamento**: O Twitter lida com uma enorme quantidade de dados, incluindo tweets, seguidores, curtidas e muito mais. Esta camada inclui diversos sistemas de armazenamento, como bancos de dados distribuídos, caches e sistemas de armazenamento de objetos.
4. **Camada de Infraestrutura**: A infraestrutura do Twitter engloba data centers em várias regiões geográficas, balanceadores de carga, sistemas de monitoramento e escalonamento automático.

## Componentes Principais

Alguns dos componentes mais importantes da arquitetura do Twitter incluem:

-   **Twitter Timeline Service**: Responsável por construir a linha do tempo dos usuários com os tweets relevantes.
-   **FlockDB**: Um banco de dados de gráficos usado para armazenar relacionamentos de seguidores.
-   **Twitter Cache**: Utilizado para armazenar em cache tweets e dados de perfil de usuário.
-   **Twitter Kafka**: Um sistema de mensagens distribuído usado para ingestão e processamento de dados em tempo real.
-   **Twitter Manhattan**: Um sistema de armazenamento de dados distribuído que lida com dados de alto volume e alta taxa de gravação.

## Desafios Técnicos

O Twitter enfrenta diversos desafios técnicos, incluindo:

-   **Escala**: Gerenciar uma plataforma com bilhões de tweets e usuários requer sistemas altamente escaláveis.
-   **Latência**: Fornecer atualizações em tempo real para milhões de usuários simultâneos sem atrasos é crucial.
-   **Consistência**: Manter a consistência dos dados em um ambiente distribuído é um desafio complexo.
-   **Segurança**: Proteger os dados dos usuários contra ameaças é uma prioridade crítica.
-   **Conformidade**: Cumprir regulamentos de privacidade de dados em várias regiões geográficas.

## Escalabilidade

Para atender à demanda crescente, o Twitter adota abordagens de escalabilidade, como a distribuição de dados em vários data centers, uso de balanceadores de carga e implementação de técnicas de particionamento de dados.

## Disponibilidade

A disponibilidade é fundamental para o Twitter. A empresa utiliza replicação de dados, failover automático e sistemas de monitoramento avançados para garantir que seus serviços estejam sempre disponíveis.

## Segurança

A segurança dos dados do usuário é de extrema importância para o Twitter. Isso envolve a criptografia de dados, autenticação de usuários, monitoramento de ameaças e práticas rigorosas de segurança da informação.

## Conclusão

Este trabalho oferece uma visão abrangente da arquitetura do Twitter, destacando seus componentes principais, desafios técnicos e abordagens para escalabilidade e segurança. A arquitetura distribuída do Twitter é um exemplo notável de como uma plataforma de mídia social pode crescer e evoluir para atender às necessidades de bilhões de usuários em todo o mundo.

## Referências

-   [Twitter Engineering Blog](https://blog.twitter.com/engineering/en_us)
-   [Similar Web](https://www.similarweb.com/pt/website/twitter.com/#geography)

_Nota: Este trabalho é apenas para fins educacionais_
