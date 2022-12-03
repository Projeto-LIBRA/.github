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

![Fluxograma](/5.2 Fluxograma.png)
