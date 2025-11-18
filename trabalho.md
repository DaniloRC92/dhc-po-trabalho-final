# **Trabalho Final de Pesquisa Operacional**

## **1. Descrição do Problema Real**

O problema estudado neste trabalho é baseado no clássico **Problema da Mochila (Knapsack Problem)**, no qual deve-se selecionar um conjunto de itens para maximizar o valor total transportado, respeitando a **capacidade máxima de peso** de uma mochila.

O contexto escolhido representa uma situação real enfrentada por empresas de transporte leve, como mensageiros, entregadores de alto valor agregado ou até equipes de campo que precisam decidir quais itens carregar em um espaço limitado.

Cada item possui:

* Um **valor**, representando lucro, importância ou benefício associado ao transporte.
* Um **peso**, representando sua ocupação na mochila.
* Uma decisão binária: **levar ou não levar** o item.

O objetivo é **maximizar o valor total** dos itens selecionados sem ultrapassar o limite de capacidade.

Os dados utilizados foram definidos pelo grupo de forma a representar um cenário realista, contendo **10 itens**, cada um com peso e valor distintos. A capacidade da mochila será analisada em mais de um cenário conforme exigido no trabalho.

## **2. Tipo de Modelo**

O modelo utilizado é uma **Programação Linear Inteira Binária (PLI)**.

**Justificativa:**

* As variáveis de decisão assumem apenas valores **0 ou 1**, conforme o item seja incluído ou não na mochila.
* O objetivo é uma função linear.
* A restrição de peso também é linear.
* Não existe necessidade de variáveis contínuas ou mistas, o que torna a PLI o modelo mais adequado.

## **3. Formulação Matemática**

### **3.1 Variáveis de Decisão**

Para cada item ( i ), definimos:

[
x_i =
\begin{cases}
1, & \text{se o item ( i ) for selecionado} \
0, & \text{caso contrário}
\end{cases}
]

### **3.2 Parâmetros**

* ( v_i ): valor do item ( i )
* ( p_i ): peso do item ( i )
* ( C ): capacidade máxima da mochila

### **3.3 Função Objetivo**

Maximizar o valor total:

[
\text{Maximizar } Z = \sum_{i=1}^{10} v_i x_i
]

### **3.4 Restrições**

Restrição de capacidade:

[
\sum_{i=1}^{10} p_i x_i \leq C
]

Restrições de domínio:

[
x_i \in {0,1}, \quad \forall i
]

## **4. Dados do Problema**

A tabela abaixo contém os **10 itens**, com seus pesos e valores definidos para o modelo.

| Item | Peso ((p_i)) | Valor ((v_i)) |
| ---- | ------------ | ------------- |
| 1    | 3            | 24            |
| 2    | 2            | 13            |
| 3    | 4            | 28            |
| 4    | 1            | 6             |
| 5    | 5            | 33            |
| 6    | 2            | 14            |
| 7    | 6            | 40            |
| 8    | 3            | 19            |
| 9    | 7            | 45            |
| 10   | 4            | 26            |

Capacidades analisadas nos cenários:

* **Cenário A:** ( C = 15 )
* **Cenário B:** ( C = 18 )

Esses dois cenários serão usados para comparação conforme solicitado no trabalho.

## **5. Implementação Computacional**

A implementação se encontra no arquivo `trabalho.xlsx`. Foi utilizado o **Excel Solver**.

## **6. Análises Planejadas**

As análises previstas incluem:

### **6.1 Comparação entre Cenário Base e Alternativo**

Os resultados para:

* Capacidade 15
* Capacidade 18

serão comparados para avaliar:

* Quais itens passam a ser selecionados com aumento de capacidade.
* Como varia o valor máximo obtido.

### **6.2 Análise de Sensibilidade**

Serão feitas análises em pelo menos dois parâmetros:

1. **Variação do valor dos itens**

   * Testar impacto de aumentar ou reduzir o valor de itens específicos.

2. **Variação do peso dos itens ou da capacidade**

   * Avaliar quantos itens adicionais seriam escolhidos com mais capacidade.
   * Verificar itens mais sensíveis à mudança de peso.

### **6.3 Interpretação Gerencial**

Resultados esperados:

* Identificação dos itens mais eficientes (maior valor relativo ao peso).
* Compreensão de trade-offs entre capacidade limitada e valor obtido.
* Avaliação da relevância de mudanças marginais na capacidade.
* Recomendações sobre:

  * Prioridade de transporte.
  * Possíveis ajustes de capacidade.
  * Estratégias de maximização de retorno.

## **7. Conclusão**
