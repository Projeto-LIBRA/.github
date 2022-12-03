Projeto LIBRA
=============

***Sistema Interativo de Coleta, Anotação e Detecção Automática de Fake News***

Motivação
---------

A internet trouxe mudanças irreversíveis na forma de se comunicar, de se informar e de interagir com o mundo. Inevitavelmente, várias instâncias do nosso contexto político também se transferiram para o digital. As eleições presidenciais de 2018 e 2022 foram grandes exemplos de como as fake news são usadas como estratégia de campanhas políticas e interferem e processos democráticos. 

No meio acadêmico, a detecção automática de desinformações já se configura como uma área emergente de grande interesse. Porém, ainda não é comum, principalmente no Brasil, encontrar projetos que buscam implementar esse conhecimento, isto é, que propõem soluções para trazer benefícios mais próximos do grande público.

As técnicas modernas de processamento de linguagem natural ainda enfrentam um grande desafio: na mesma medida em que necessitam de muitos dados para treinamento, há pouca diversidade de datasets anotados para seu desenvolvimento, principalmente em domínios mais restritos, como o tratado neste trabalho, e em idiomas diferentes do inglês. No geral, essas bases necessitam de uma etapa de anotação manual humana, que torna o processo pouco escalável e atrasa o desenvolvimento de algoritmos mais robustos em nível nacional.

Objetivo
--------

O objetivo deste trabalho é criar um sistema que auxilie no combate à disseminação de fake news em redes sociais, desenvolvido em conjunto com o grupo interdisciplinar de pesquisa IBRA USP. Esse objetivo se divide em duas frentes complementares:

1. Frente primária: tem como alvo o grande público das redes sociais exposto à disseminação de fake news, na forma de um bot interativo no Twitter.
2. Frente secundária: tem como objetivo agregar valor à comunidade científica que desenvolve modelos de Aprendizado de Máquina no contexto de fake news, na forma de bases de dados anotadas e insights.

Tendo esses dois objetivos em mente, foram utilizadas técnicas de desenvolvimento e implementação (deploy) de algoritmos de Aprendizado de Máquina (mais especificamente processamento de linguagem natural e deep learning) e tecnologias ligadas a coleta, processamento, armazenamento e visualização de dados. Ademais, haverá emprego de técnicas e conceitos de engenharia de software para estruturar a arquitetura necessária para o funcionamento dos diversos módulos do sistema.

Arquitetura
-----------

A arquitetura do sistema é baseada em serviços da AWS, com uso de endpoints da API do Twitter para interação com o usuário e coleta de dados.

![Fluxograma](https://github.com/Projeto-LIBRA/.github/blob/42f7d4ba91b93edcbcdce723a003b4d62145fd11/profile/5.2%20Fluxograma.png)

O processo de execução pode ser descrito da seguinte forma:

1. O fluxo começa quando o o usuário comenta um tweet, marcando o perfil do bot. A marcação age como trigger, isto é, o gatilho para início da execução do fluxo do sistema.
    
1. Um computador virtual (Amazon EC2) que executa continuamente o script que implementa o endpoint Filtered Stream da API do Twitter, recebendo em tempo real objetos que representam eventos de marcação. Esses objetos possuem as chaves identificadoras da postagem original e da marcação. Após recebê-lo, a EC2 envia uma mensagem para uma fila do Amazon SQS, com os parâmetros necessários.
    
1. Uma instância da AWS Lambda, unidade de serviço de computação serverless contendo programa responsável pela coleta de dados, é acionada com o envio da mensagem anterior para a fila. Essa unidade faz o processo completo de extração, processamento e armazenamento dos dados do tweet no Amazon S3.

1. Após o armazenamento ser realizado, é enviada uma mensagem contendo as mesmas duas chaves identificadoras que iniciaram o fluxo para uma segunda fila do Amazon SQS. Essa mensagem aciona uma outra instância de Lambda, responsável por toda a parte final do fluxo, que inclui execução do modelo dEFEND, resposta à marcação no Twitter e armazenamento dos resultados da execução no Amazon S3.

O projeto na prática
--------------------

Os resultados do trabalho podem ser vistos na prática marcando o [perfil do bot no Twitter](https://twitter.com/ProjetoLibra) e acessando o [dataset público](https://github.com/Projeto-LIBRA).

![funcionamento](./funcionamento.png)
