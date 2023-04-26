# **PROJETO DE ANÁLISES DE DADOS E-COMMERCE- OLIST
![](https://blog.caju.com.br/wp-content/uploads/2022/08/case-olist.webp)
## INTRODUÇÃO


Vamos analisar o conjunto de comércio eletrônico brasileiro de pedidos feitos na loja Olist.

Olist é uma plataforma de comércio eletrônico brasileira que conecta pequenas empresas a canais de vendas online, permitindo que vendam seus produtos em vários marketplaces do Brasil. A empresa também oferece serviços de logística e gerenciamento de pedidos para seus clientes.

O conjunto de dados possui informações de 100 mil pedidos de 2016 a 2018 realizados em vários marketplaces no Brasil. Suas características permitem visualizar um pedido em múltiplas dimensões: desde o status do pedido, preço, desempenho de pagamento e frete até a localização do cliente, atributos do produto e, finalmente, avaliações escritas pelos clientes. Também lançamos um conjunto de dados de geolocalização que relaciona os códigos postais brasileiros às coordenadas (latitude/longitude).

Estes são dados comerciais reais, foram anonimizados e as referências às empresas e parceiros no texto da revisão foram substituídas pelos nomes das grandes casas de Game of Thrones.

<p>A <strong>análise exploratória de dados</strong> é uma das principais técnicas utilizadas em <strong>Data Science</strong>, pois nos permite compreender melhor os dados e encontrar <em>insights</em> valiosos que podem ser usados em decisões de negócios. Neste notebook, vamos explorar a base de dados da Olist e responder algumas perguntas importantes sobre o comportamento dos consumidores no mercado de e-commerce.</p>

<p>Para isso, usaremos a linguagem <strong>Python</strong> e as bibliotecas <strong>Pandas</strong>, <strong>Numpy</strong> e <strong>Matplotlib</strong> para manipulação e visualização de dados. Além disso, utilizaremos a biblioteca <strong>Plotly</strong> para criar gráficos interativos e mais complexos, permitindo uma análise mais detalhada dos dados.</p>

<h2 style="color: #6c5b7b"> Perguntas a serem respondidas</h2>

- Quais valores médio  e máximo dos fretes?
- Como se comportam as notas de avaliações dos consumidores?
- Quais cliente geram maiores receitas e que mais gastam?
- Quais os top 10 Estados com maiores números de pedidos?
- Quais as cidades com maiores receitas?
- Como os pedidos variam com otempo?
- Quais maiores números de pedidos por semana?
- Quais produtos com melhores e piores avaliações?
- Será que o método de pagamentos afetam os status do  pedido?
- Existem relação entre o tempo de entrega e as avaliações?
- Quais pedidos mais rápidos e mais demorados em prazo de entrega?
- Quais as cidaddes dos vendedores com maiores e menores tempo de entrega?
- Quais vendedores com melhores e piores prazo de entrega?

# STORYTELLING COM OS DADOS

Pedro  gerencia o setor de e-commerce do grupo Olist, e acionou seus analistas e cientistas de dados para que fizessem um projeto que o ajudasse a tomar as melhores decisões estratégicas de negócios. Se sentindo perdido deixou nas mãos do seu time dados a confiança em buscar informações valiosas que podessem te nortear para uma decisão de negócio mais acertiva.Seus analistas dentro do contexto do negócio, resolveram responder algumas perguntas com base nos dados da empresa.

Sendo assim, os analistas descobriram algumas informações relevantes como:

- A média dos **fretes é de 20,05 reais, sendo que existem frete grátis e valor máximo de 409,00**.Essa informação faz concluir até que ponto o consumidor está disposto a pagar em frete.

- Os analistas queriam saber como se comportava as avaliações dos consumidores, e **descobriram que mais 75% deram uma pontuação igual ou maior que 4**, sendo considerado bem avaliados, levando em consideração que a nota máxima é 5.

- Com base na regra de pareto 20% dos clientes representam 80% dos resultados, sendo assim, os analistas foram atrás dos 20% dos clientes que geram maiores receitas e descobriram que **o cliente que mais paga representa 54% com total de vendas acima de 100mil**. Dentre os **top 10 clientes estão cima de 20 mil**, isso pode sugerir futuramente com a área de negócio uma segmentação de clientes por faixa de gastos.

- Ao aprofundar suas análises  descobriram que  **São Paulo é estado com maior número de pedidos com 48 mil, seguido por Rio de janeiro e Minas Gerais com aproximadamente 13 mil pedidos**. Tão logo, se validou que as cidades com maiores número de pedidos são São Paulo, Rio de janeiro e Belo Horizonte

- Os analistas queriam saber em qual momento do dia se concentram os , e chegaram à conclusão que **os pedidos começam a aumentar por volta das 6hs da manhã e atingem o pico às 16hs da tarde**.
O período da tarde é bastante significativo em número de pedidos.

- Tão logo queriam saber os picos de pedidos durante os dias da semana, **os pedidos atingem o pico no início da semana (segunda e terça-feira) e começam a declinar um pouco depois**, verifica-se o final de semana tem uma leve queda nos pedidos mas com pouca discrepância.

- Os analistas queriam saber o tipo de produtos bem avaliados e perceberam que os produtos bem avaliados estão com notas acima de 4, sendo considerados a nota máxima 5, produtos como: alimentos, livros técnico, construção e etc, produtos diversos se enquadram como bem avaliados, isso leva a concluir que **não é o tipo de produto que faz ser bem avaliado, e sim, alguma a operação no serviço prestado**. Perceberam também que produtos com menores avaliações estão acima da nota 3, o que não pode ser considerados maus avaliados.

- Analisando o tempo média de entrega, **O tempo médio de entrega é de  (12 dias)**, sendo que metade das entregas são feitas acima de  (10 dias).porém observamos um **valor extremo atípico de 208 dias**.

- Os analistas descobriram que o  tempo de entrega é uma variável que tem relação direta com as pontuações, a hipótese confirma que **à medida que o tempo de entrega diminui, as avaliações aumentam**.

- Os analistas não conformados, queriam saber qual o vendedor mais rápido e o que mais demorou nas entregas, logo percebe-se que o vendedor mais rápido em tempo de entrega têm **média 5 dias para entregar porém ele têm poucos pedidos**, O vendedor mais lento têm tempo de entrega média de **22 dias e com poucos pedidos, isso leva a concluir que o gargalos se encontra na logística e não quantidades de pedidos**.

- Para validar a importância do tempo de entrega, os analistas avaliou os top 10 Estado com maiores e piores scores, e descobriram que os estados com maior tempo de entrega é RR, AP e AM, **SALIENTANDO QUE OS 10 MAIORES TEMPO DE ENTREGA POR ESTADOS ESTÃO ACIMA DE 20 DIAS DE ENTREGA**, enquanto que, *SP TÊM O MENOR TEMPO DE ENTREGA 9 DIAS APENAS, ENQUANTO OS OUTROS ATÉ 16 DIAS dentre os top 10 menores tempo de entrega!*.

- Os analistas analisou o panorama do tempo de entrega  entre 2016 e 2018, e descobriu que, A empresa melhorou sua logística e reduziu considerávelmente o tempo de entrega ao longo dos anos, **em 2016 era acima de 16 dias, em 2017 reduziu para 12 dias , e em 2018  cerca de 9 dias**. Consequentemente, em 2017 e 2018 as avaliações melhoraram com relação à 2016.

- E por fim, os analistas queriam saber quais os produtos mais vendidos entre os top 10,e descobriram que:**Cama_mesa_banho, beleza_saùde, acessórios_informática , são os 3 que mais se destacam**.


## CONSIDERAÇÕES FINAIS
Pedro e sua equipe de negócio agora pode tomar decisões estratégicas com base em informações analíticas geram valor ao negócio.
ele pode definir;

- Politíca de frete;
- Prazo de entrega e logística;
- Politica de vendas;
- Politica de segmentação de clientes;
- Politica com base na geolocalização dos clientes;
- Politica de gerenciamento de gargalos logísticos de prazo de entrega;
- Politica para gerenciamento de clientes com melhores e de baixo scores por Estados;
- Politica de segmentação por tipo de produto;

## PROJETOS FUTUROS
Com base nas informação obtidas pelas análises, alguns projetos futuros completaria a gama de informação, sendo assim têm como sugestão de trabalho:

- Projeto de modelagem preditiva usando modelos de agrupamento para segmentar clientes;
- Projeto de modelagem preditiva para prever o nível de satisfação dos cliente;
- Projeto de modelagem preditiva para prever o churn de clientes;
- Projeto de modelagem preditiva para prever a receita futuros dos principais clientes;
- Projeto de modelagem preditiva para prever o tempo de entrega dos produtos;

