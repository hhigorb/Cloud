# AWS

## Básico sobre a AWS

A AWS é a plataforma de nuvem mais adotada e abrangente do mundo. Possuem mais de 175 serviços disponibilizados em datacentes espalhados por todo o mundo.

![O que é a AWS](images/image1.png 'O que é a AWS')

Isso significa que tudo que um Data Center faz, a AWS também faz. Em vários aspectos, é até mais fácil implementar uma solução pela AWS, pois há vários serviços
simples de se utilizar e a configuração e custo seriam mais complexos utilizando um Data Center.

Também é projetada para ser segura e flexível, além de possuir uma infraestrutura global, como no mapa abaixo:

![O que é a AWS](images/image2.png 'O que é a AWS')

A AWS utiliza o formato **Pay As You Go** - Pagamento conforme o uso. O que torna a plataforma completamente acessível. É cobrado pelo uso de recursos, ou seja,
parou de utilizar, parou de pagar.

É importante consultar o preço de cada serviço a ser utilizado. Cada serviço tem seu método de cobrança baseado no uso.

---

## Regiões, Zonas de Disponibilidades e Zonas Locais

![Regiões e Zonas de Disponibilidade](images/image3.png 'Regiões e Zonas de Disponibilidade')

---

![Regiões e Zonas de Disponibilidade](images/image4.png 'Regiões e Zonas de Disponibilidade')

Cada região da AWS está situada numa área geográfica separada das outras, e é projetada para funcionar independentemente das outras regiões. Inclusive, existe diferença
do valor cobrado para o mesmo serviço entre as regiões. A região Norte da Virgina (us-east-1) é onde normalmente os serviços chegam primeiro, além de ser a mais barata.

No Console da AWS, você vê somente os recursos que estão vinculados à região especificada. Os recursos não são replicados entre regiões da AWS automaticamente, ou seja,
ao subir uma máquina na região de São Paulo, só verei ela quando eu estiver na região de São Paulo. A instância não replica para todas as regiões.

![Regiões e Zonas de Disponibilidade](images/image5.png 'Regiões e Zonas de Disponibilidade')

---

Uma Zona de Disponibilidade é um conjunto de Data Centers, projetado para trabalhar de forma isolada das demais ZDs, sendo redundante e seguro. Cada região possui peo menos 2 ZD.
Por exemplo: Na região de São Paulo, podemos ter 3 Zonas de Disponibilidade (poderiam ser 3 prédios da Amazon com vários Data Centers), e o conjunto dessas 3 ZDs seriam uma região.

As ZDs ficam geograficamente distantes umas das outras para que, caso ocorra algum evento significativo, todas não sejam afetadas. Elas são construídas a uma distância que possibilite
uma interconexão de rede de baixa latência.

![Regiões e Zonas de Disponibilidade](images/image6.png 'Regiões e Zonas de Disponibilidade')

Existem pelo menos 2 ZDs em cada Região.

---

As Zonas locais da AWS permitem que você utilize serviços seletos, como os de computação e de armazenamento, mais perto dos usuários. Dessa forma, eles têm acesso de baixíssima latência
aos aplicativos executados no local.

Zonas locais da AWS também são conectadas à região principal por meio de uma rede privada de banda larga muito alta e redundante da Amazon. Com isso, os aplicativos que são executados nas 
Zonas locais têm acesso rápido, seguro e fácil aos demais serviços da AWS.

Um resumo dos conceitos de Regiões e Zonas:

![Regiões e Zonas de Disponibilidade](images/image7.png 'Regiões e Zonas de Disponibilidade')

---

## Arquitetura Serveless

Serveless (sem servidor) é uma arquitetura nativa da nuvem orientada a **eventos** e que permite transferir mais das suas responsabilidades operacionais à AWS. Ela permite criar e executar
aplicativos e serviços sem se preocupar com a infraestrutura em que esses aplicativos estão rodando e elimina as tarefas de gerenciamento de servidores.

Deixa de ser necessário tarefas como o provisionamento de servidores ou de clusters, patches, manutenção do sistema operacional e provisionamento de capacidade. Podemos criar servidores para
praticamente qualquer tipo de aplicativo ou serviço e a AWS cuida de tudo o que for necessário para executar e escalar aplicativos com alta disponibilidade. Isso permite focar amis no desenvolvimento
da aplicação e menos em configuração ou gerenciamento de servidores. Outros benefícios são a redução de custo e alta escalabilidade e disponibilidade da aplicação

Para entender as diferenças entre uma arquitetura padrão com servidores e a Serveless, podemos usar de exemplo uma aplicação web que recebe requisições de usuários. No caso de uma arquitetura padrão,
sempre há pelo menos 1 servidor ativo para caso algum usuário faça uma requisição, o serviço esteja no ar. Já na arquitetura Serveless, não existe um servidor online "ouvindo" as requisições.
Quando chega uma requisição, a AWS sobe uma máquina para processá-la e depois a encerra. Com isso, só é pago pelo momento em que a máquina da AWS sobe e processa o evento. 

## AWS Lambda

O AWS Lambda é um serviço da Amazon que permite que você execute código sem provisionar ou gerenciar servidores. Você paga apenas pelo tempo de computação consumido. Basta carregar o código e o Lambda se 
encarrega de todos os itens necessários para executar e permitir que o código seja escalável e com alta disponibilidade.

Uma boa prática da utilização do Lambda é sempre escrever códigos enxutos, otimizados e específicos para o contexto utilizado. Pagamos por uso, então quanto mais rápido a execução do Lambda, melhor.

![AWS Lambda](images/image8.png 'AWS Lambda')

---

![AWS Lambda](images/image9.png 'AWS Lambda')

---

![AWS Lambda](images/image10.png 'AWS Lambda')

---

![AWS Lambda](images/image11.png 'AWS Lambda')

---

## Como o Lambda funciona?

![AWS Lambda](images/image12.png 'AWS Lambda')

---

![AWS Lambda](images/image13.png 'AWS Lambda')

## Alguns cases reais de Arquitetura de uso do Lambda

![AWS Lambda](images/image14.png 'AWS Lambda')

---

![AWS Lambda](images/image15.png 'AWS Lambda')

## Preços do Lambda

Você é cobrado pelo número de solicitações de suas funções e pela duração, o tempo que leva para que seu código seja executado. O Lambda conta uma solicitação cada vez que começa a executar em resposta
a uma notificação de evento ou chamada de invocação, incluindo invocações de teste do console.

A duração é calculada a partir do momento em que seu código começa a ser executado até ele retornar ou encerrar, arredondando para os 100 ms mais próximos. O preço depende da quantidade de memória
que você alocar para sua função.

O único componente configurável no Lambda é a quantidade de memória que você quer para sua função. Capacidade de CPU e outros recursos são alocados de forma proporcional. Um aumento no tamanho da memória 
aciona um aumento equivalente na CPU disponível para sua função.

**Exemplos de custo da AWS Lambda:**

![AWS Lambda](images/image16.png 'AWS Lambda')

## AWS API Gateway

O AWS API Gateway é um serviço gerenciado que permite que desenvolvedores criem, publiquem, mantenham, monitorem e protejam APIS em qualquer escala com facilidade. Usando o API Gateway, você pode criar APIs
RESTful e APIs WebSocket que habilitam aplicativos de comunicação bidirecionais em tempo real.

O API Gateway dá suporte a cargas de trabalho conteinerizadas e sem servidor, além de aplicativos da web. Ele administra todas as tarefas envolvidas no recebimento e processamento de até centenas de milhares
de chamadas de API simultâneas. Inclusive provém suporte a gerenciamento de tráfego, suporte de CORS, controle de autorização e acesso, com fluxo controlado, monitoramento e gerenciamento de versões de API.

Não tem taxas mínimas ou custos antecipados. Você paga apenas pelas chamadas de API recebidas e pela quantidade transferida de dados de saída.

## Como o API Gateway funciona?

![AWS API Gateway](images/image17.png 'AWS API Gateway')

Além disso, com o modelo de definição de preço em camadas do API Gateway, você pode reduzir os custos à medida que seu uso da API é escalado.

Existem 2 tipos de APIs:

![AWS API Gateway](images/image18.png 'AWS API Gateway')

---

![AWS API Gateway](images/image19.png 'AWS API Gateway')

---

![AWS API Gateway](images/image20.png 'AWS API Gateway')

## Preços do API Gateway

![AWS API Gateway](images/image21.png 'AWS API Gateway')

---

![AWS API Gateway](images/image22.png 'AWS API Gateway')

**Exemplos de custo do AWS API Gateway:**

![AWS API Gateway](images/image23.png 'AWS API Gateway')

---

![AWS API Gateway](images/image24.png 'AWS API Gateway')

---

![AWS API Gateway](images/image25.png 'AWS API Gateway')

---

![AWS API Gateway](images/image26.png 'AWS API Gateway')

## AWS SAM

O AWS SAM ou Serveless Application Model é um framework open-source para construir aplicações Serverless na AWS. Ele fornece sintaxe abreviada
para expressar funções, APIs, bancos de dados e mapeamentos de origens de eventos.

Basicamente, atráves de templates e linha de comando, conseguimos criar nossas aplicações serveless, testar localmente simulando o ambiente da AWS e fazer deploy de forma simplificada.

Ele é integrado com ferramentas de desenvolvimento, a fim de facilitar ainda mais a vida do desenvolvedor. O AWS SAM executa o ambiente em containers do Docker, baixando as imagens direto da AWS. Nosso único trabalho é instalá-lo.

Documentação do SAM para caso de dúvidas: [AWS SAM](https://aws.amazon.com/serverless/sam/)

## AWS IAM

O AWS Identity and Access Management (IAM) permite que você gerencie com segurança o acesso aos serviços e recursos da AWS. Usando o IAM, você pode criar e gerenciar usuários e grupos da AWS e usar permissões para conceder e negar acesso a recursos da AWS.

O IAM Permite que os usuários controlem o acesso às APIs de serviço e a recursos específicos da AWS. O IAM também permite que você adicione condições específicas, como a hora certa para controlar como um usuário pode usar a AWS, seu endereço IP de origem, se estão usando SSL ou se fizeram a autentição com um dispositivo de autentição multifator.

![AWS IAM](images/image27.png 'AWS IAM')

---

![AWS IAM](images/image28.png 'AWS IAM')

---

![AWS IAM](images/image29.png 'AWS IAM')

---

![AWS IAM](images/image30.png 'AWS IAM')

---

![AWS IAM](images/image31.png 'AWS IAM')

---

![AWS IAM](images/image32.png 'AWS IAM')

---

![AWS IAM](images/image33.png 'AWS IAM')

---

![AWS IAM](images/image34.png 'AWS IAM')

---

![AWS IAM](images/image35.png 'AWS IAM')

---

![AWS IAM](images/image36.png 'AWS IAM')

---

**ATENÇÃO AO USO DE CREDENCIAIS EM PROJETOS**

Temo que tomar muito cuidado ao subir qualquer tipo de código envolvendo AWS em repositórios.

Uma prática muito comum (porem incorreta) é utilizar as credenciais da AWS no proprio projeto para permissionamento da aplicação.

Se por um descuido, você publicar essas credenciais no GitHub (ou qualquer repositorio publico), você poderá perder muito dinheiro.

Existem ferramentas maliciosas que ficam escaneando o GitHub para encontrar essas credenciais da AWS. Uma vez que eles encontrem, caso essas credenciais possuam acesso, irão criar diversos recursos para beneficio proprio (como instancias EC2, bancos de dados, e tudo que quiserem utilizar), resultando em um grande custo pra você.

Portanto temos sempre que tomar muito cuidado e nunca enviarmos credenciais para repositorios.

Mesmo que o repositorio seja privado, ainda é uma falha de segurança, pois caso voce esteja trabalhando em uma empresa que tenha as chaves no repositorio, alguem pode sair da empresa, guardar as chaves com ele, e também realizar ações maliciosas, como criar recursos, ou apagar os já existentes.

SEMPRE prefira utilizar permissionamento de aplicações sem ser pelas credenciais, dando permissões direta aos recursos.

## AWS DynamoDB 

O Amazon DynamoDB é um banco de dados NoSQL (não relacional) que oferece alto desempenho para aplicações em qualquer escala.

É um banco de dados durável, totalmente gerenciado com segurança, backup e restauração integrados, além de armazenamento em cache.

O DynamoDB pode processar mais de 10 trilhões de solicitações por dia e comportar picos de mais de 20 milhões de solicitações por segundo!

Empresas como Lyft, Airbnb, Samsung, Toyota, Netflix e muitas outras utilizam o AWS DynamoDB em seu dia-a-dia.

![AWS DynamoDB](images/image37.png 'AWS DynamoDB')

---

![AWS DynamoDB](images/image38.png 'AWS DynamoDB')

---

![AWS DynamoDB](images/image39.png 'AWS DynamoDB')

---

![AWS DynamoDB](images/image40.png 'AWS DynamoDB')

O DynamoDB criptografa todos os dados por padrão e oferece controle refinado de acesso e identidade em todas as suas tabelas. Você pode criar backups completos de centenas de terabytes de dados instantaneamente, sem impacto no desempenho de suas tabelas, e recuperar qualquer momento dos 35 dias anteriores sem tempo de inatividade.

![AWS DynamoDB](images/image41.png 'AWS DynamoDB')

## Como o DynamoDB funciona?

![AWS DynamoDB](images/image42.png 'AWS DynamoDB')

---

![AWS DynamoDB](images/image43.png 'AWS DynamoDB')

---

![AWS DynamoDB](images/image44.png 'AWS DynamoDB')

---

![AWS DynamoDB](images/image45.png 'AWS DynamoDB')

---

![AWS DynamoDB](images/image46.png 'AWS DynamoDB')

---

![AWS DynamoDB](images/image47.png 'AWS DynamoDB')

---

![AWS DynamoDB](images/image48.png 'AWS DynamoDB')

---

![AWS DynamoDB](images/image49.png 'AWS DynamoDB')

---

![AWS DynamoDB](images/image50.png 'AWS DynamoDB')

---

![AWS DynamoDB](images/image51.png 'AWS DynamoDB')

---

![AWS DynamoDB](images/image52.png 'AWS DynamoDB')

## AWS SQS

O Amazon Simple Queue Service (SQS) é um serviço de filas de mensagens gerenciado que permite o desacoplamento e a escalabilidade de microsserviços, sistemas distribuídos e aplicativos sem servidor.

O SQS elimina a complexidade e a sobrecarga associadas ao gerenciamento e à operação de middleware orientado a mensagens.

Use o SQS para enviar, armazenar e receber mensagens entre componentes de software em qualquer volume, sem perder mensagens ou precisar que outros serviços estejam disponíveis.

O SQS oferece dois tipos de filas de mensagens:

![AWS SQS](images/image53.png 'AWS SQS')

---

![AWS SQS](images/image54.png 'AWS SQS')

---

![AWS SQS](images/image55.png 'AWS SQS')

---

![AWS SQS](images/image56.png 'AWS SQS')

---

![AWS SQS](images/image57.png 'AWS SQS')

---

![AWS SQS](images/image58.png 'AWS SQS')

---

![AWS SQS](images/image59.png 'AWS SQS')

---

![AWS SQS](images/image60.png 'AWS SQS')

---

![AWS SQS](images/image61.png 'AWS SQS')

## AWS SNS

O Amazon Simple Notification Service (SNS) é um serviço de mensagens totalmente gerenciado para comunicação de sistema para sistema e de aplicativo para pessoa (A2P).

Ele permite que você se comunique entre sistemas por meio de padrões de publicação/assinatura (pub/sub).

Ele permite mensagens entre aplicativos de microsserviços dissociados ou para se comunicar diretamente com os usuários via SMS, push móvel e e-mail.

A funcionalidade de pub/sub de sistema para sistema fornece tópicos para mensagens de alto rendimento, baseadas em push e de muitos-para-muitos.

Usando tópicos do Amazon SNS, seus sistemas editores podem espalhar mensagens para um grande número de sistemas de assinantes ou endpoints de clientes.

Incluindo filas do Amazon SQS, funções do AWS Lambda e HTTP/S, para processamento paralelo.

![AWS SNS](images/image62.png 'AWS SNS')

## Amazon S3

O Amazon Simple Storage Service (Amazon S3) é um serviço de armazenamento de objetos que oferece escalabilidade líder do setor, disponibilidade de dados, segurança e performance.

Isso significa que clientes de todos os tamanhos e setores podem usá-lo para armazenar qualquer volume de dados em uma grande variedade de casos de uso, como sites, aplicações para dispositivos móveis, backup e restauração, arquivamento, aplicações empresariais, dispositivos IoT e análises de Big Data.

O Amazon S3 foi projetado para 99,99% de durabilidade e armazena dados para milhões de aplicativos para empresas de todo o mundo.

![AWS S3](images/image63.png 'AWS S3')

---

![AWS S3](images/image64.png 'AWS S3')

---

![AWS S3](images/image65.png 'AWS S3')

O S3 Standard oferece um armazenamento de objetos com altos níveis de resiliência, disponibilidade e performance para dados acessados com frequência. Como fornece baixa latência e alto throughput, o S3 Standard é adequado para uma grande variedade de casos de uso, como aplicativos na nuvem, sites dinâmicos, distribuição de contéudo, aplicativos móveis, jogos e dados analíticos de Big Data.

Já o S3 Standard-Infrequent Access (S3 Standard-IA) é indicado para dados acessados com menos frequência, mas que exigem acesso rápdio quando necessários. Ela oferece os altos níveis de resiliência e throughput e a baixa latência do S3 Standard. A combinação de baixo custo e a alta performance a tornam ideal para armazenamento de longa duração, backups e datastores para arquivos de recuperação de desastres.

O S3 One Zone-Infrequent Access (S3 One Zone-IA) ao contrário de outras classes de armazenamento do S3, que armazenam dados em no mínimo três Zonas de Disponibilidade (AZs), armazena dados em uma única AC. ELa é uma opção de menor custo para dados acessados com pouca frequência, mas não precisam da disponibilidade e da resiliência S3 Standard ou S3 Standard-IA.

O S3 Intelligent-Tiering foi projetado para otimizar os custos movendo automaticamente os dados para o nível de acesso mais econômico, sem impacto na performance ou sobrecarga operacional. Ela funciona a partir do armazenamento de objetos em dois níveis de acesso: um nível é otimizado para acesso frequente e outro nível de custo mais baixo, que é otimizado para acesso infrequente.

O S3 Glacier é uma classe de armazenamento segura, durável e de baixo custo para arquivamento de dados. Você pode armazenar com confiabilidade qualquer volume de dados a um custo competitivo ou inferior ao custo de soluções no local. Para manter os custos baixos, mas com condições de suprir necessidades variáveis, o S3 Glacier disponibiliza três opções de recuperação, que podem levar de alguns minutos a várias horas.

Já o S3 Glacier Deep Archive é a classe de armazenamento mais barata do Amazon S3 e oferece suporte à retenção e preservação digitais de longo prazo para dados que podem ser acessados uma ou duas vezes por ano. Essa classe é projetaa para clientes que mantêm conjuntos de dados por 7 a 10 anos ou mais para cumprir requisitos de conformidade normativa, e podem ser restaurados em até 12 horas.

## AWS Cloud Watch

O Cloud Watch é um serviço de monitoramento para recursos em nuvem AWS. Você pode usá-lo para coletar e rastrear métricas, coletar e monitorar arquivos de log e definir alarmes.

Você pode usá-lo para obter visibilidade sobre a utilização de recursos, a performance de aplicativos e o status operacional em todo o sistema.

É possível usar essas percepções para reagir e manter seu aplicativo em execução tranquilamente. 

Ele pode monitorar recursos da AWS como instâncias do Amazon EC2, tabelas do Amazon DynamoDB, funções Lambda, dentre outros.

É possível usar o Cloud Watch para detectar comportamento anormal em seus ambientes, definir alarmes, visualizar logs, métricas lado a lado, executar ações automatizadas, resolver problemas e descobrir insights para manter seus aplicativos em perfeita execução.

É simples monitorar seus recursos e aplicativos da AWS com o Cloud Watch. Ele se integra nativamente com mais de 70 serviços da AWS, como EC2, DynamoDB, S3, ECS, EKS e AWS Lambda, além de publicar automaticamente métricas detalhadas de um minuto e métricas personalizadas com até um segundo de granularidade.

![AWS Cloud Watch](images/image66.png 'AWS Cloud Watch')

## AWS Step Functions

O AWS Step Functions é um orquestrador de funções sem servidor que facilita o sequenciamento de funções do AWS Lambda e vários serviços da AWS.

Por meio da interface visual, você cria e executa uma série de fluxos de trabalho com ponto de verificação e orientados a evento que mantém o estado da aplicação.

A saída de uma etapa serve de entrada para a próxima. Cada etapa da aplicação é executada em sequência e conforme esperado pela lógica de negócios definida.

O Step Functions gerencia automaticamente o tratamento de erros, a lógica de novas tentativas e o estado.

Ele ajuda a garantir que **trabalhos de ETL** múltiplos e prolongados sejam executados em ordem e concluídos com sucesso, em vez de organizar manualmente esses trabalhos ou manter um aplicativo separado.

Também é possível usar o Step Functions para padronizar um fluxo de trabalho de treinamento de Machine Learning para aumentar a precisão dos modelos de Machine Learning.

O Step Functions tem dois tipos de fluxos de trabalho: Standard Workflows e Express Workflows.

![AWS Step Functions](images/image67.png 'AWS Step Functions')

---

![AWS Step Functions](images/image68.png 'AWS Step Functions')

## AWS Cloud Formation

O AWS Cloud Formation oferece uma linguagem comum para modelar e provisionar recursos de infraestrutura da AWS e terceirizados em um ambiente de nuvem.

Ele permite usar linguagens de programação ou um arquivo de texto simples para modelar e provisionar de forma automática e segura todos os recursos necessários.

Ele provisiona recursos de forma segura e replicável, permitindo criar e recriar a sua infraestrutura e aplicativos, sem precisar executar ações manuais ou gravar scripts personalizados.

Isso cria uma única fonte confiável para concentrar os seus recursos de infraestrutura.

![AWS Cloud Formation](images/image69.png 'AWS Cloud Formation')

Dessa forma, podemos replicar nosso ambiente com facilidade, sem nos preocuparmos se tudo foi recriado da forma como estava.

## Outros serviços também úteis

## AWS Code Commit

O AWS CodeCommit é um serviço de hospedagem de repositório de controle de versão totalmente gerenciado pela Amazon Web Services (AWS). Ele fornece um ambiente seguro e escalável para armazenar e gerenciar o código-fonte de aplicativos e projetos de software.

O CodeCommit permite que equipes de desenvolvimento colaborem de forma eficiente no desenvolvimento de software. Ele suporta repositórios Git, um sistema de controle de versão distribuído amplamente utilizado, que permite rastrear e gerenciar alterações no código ao longo do tempo.

Algumas das principais características do AWS CodeCommit são:

**Controle de versão:** O CodeCommit permite rastrear todas as alterações no código, facilitando a colaboração e a reversão de alterações indesejadas.

**Segurança:** Os repositórios do CodeCommit são protegidos usando autenticação baseada em IAM (Identity and Access Management), permitindo o controle granular de permissões de acesso. Além disso, os dados são criptografados em repouso e em trânsito.

**Integração com outros serviços AWS:** O CodeCommit se integra perfeitamente com outros serviços da AWS, como AWS CodePipeline, AWS CodeBuild e AWS CodeDeploy, para criar pipelines de integração e entrega contínuas (CI/CD).

**Escalabilidade e disponibilidade:** O serviço é altamente escalável e gerenciado pela AWS, o que significa que não é necessário se preocupar com capacidade ou disponibilidade do servidor.

**Integração com ferramentas Git:** Como o CodeCommit é compatível com o Git, é possível usar várias ferramentas e clientes Git existentes para interagir com os repositórios, como a linha de comando Git, IDEs e ferramentas de desenvolvimento.

**Notificações e integração com eventos:** É possível configurar notificações baseadas em eventos para alertar sobre alterações no repositório, como confirmações de código, pull requests ou atualizações de branches.