# Desafio – Alerta de Produtos Vencidos
Desafio: Criação de uma lógica para a identificação de produtos vencidos nas lojas

Identificação de Danones vencidos em lojas a partir de um DataSet com o seguinte formato:

Imagem 1

Como não temos a validade dos produtos no nosso banco de dados, considera-se que a validade é de 11 dias desde a chegada do produto na loja.
Como regra, há duas diretrizes:
  1.	Os Danones vendidos serão sempre do lote mais antigo
  2.	Ajustes da quantidade de Danones na loja mesmo que não haja vendas, serão descontados do lote mais recente

# Resolução:
Foram adicionadas 2 colunas: “estoque_inicial” e “quantidade_adicionada”. A coluna “quantidade_estoque” foi renomeada para “estoque_final”.
Dessa forma temos: <br>
•	__Estoque inicial__: Quantidade de Danones em estoque no início do dia <br>
•	__Estoque final__: Quantidade de Danones em estoque no final do dia <br>
•	__Quantidade adicionada__: Quantidade de Danones chegando à loja (novo lote). Números negativos nesta coluna representam ajustes no DataSet sobre a quantidade do produto. <br>

Imagem 2

Neste exemplo, observa-se que no dia 12/07/2021, 200 Danones foram adicionados ao estoque. No dia 09/07/2021 houve um ajuste de -2. <br>
No primeiro dia do DataSet, não sabemos o dia de chegada dos produtos. A análise será mais confiável a partir do primeiro lote registrado.

Na tabela abaixo, observa-se os dias onde houve chegada de novos produtos nas lojas:

Imagem 3

Foi criada uma função que identifica os lotes, a quantidade de Danones restantes de cada lote em cada loja. A função também cria um DataFrame com o histórico de alertas de produtos vencidos ou próximos da validade.<br>
Na tabela abaixo visualiza-se a quantidade de produtos de cada estoque para a loja 1:

Imagem 4

Observa-se que no último dia do DataSet, ainda há 46 Danones disponíveis. 40 do lote 13, que chegou no dia 01/11 e 6 do lote anterior, que chegou no dia 28/10.

A função criada gera um aviso de produtos vencidos ou próximos da data de validade (a partir do sétimo dia desde a chegada).<br>
Abaixo está um exemplo do histórico de alertas da loja 2:

Imagem 5

A partir da lógica criada, é possível criar uma aplicação capaz de emitir alertas e consultar o histórico de alertas emitidos.

