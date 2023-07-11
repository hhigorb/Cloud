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
