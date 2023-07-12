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
