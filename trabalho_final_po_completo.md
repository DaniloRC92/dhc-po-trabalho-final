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

\[
x_i =
\begin{cases}
1, & \text{se o item ( i ) for selecionado} \\
0, & \text{caso contrário}
\end{cases}
\]

### **3.2 Parâmetros**

* ( v_i ): valor do item ( i )
* ( p_i ): peso do item ( i )
* ( C ): capacidade máxima da mochila

### **3.3 Função Objetivo**

Maximizar o valor total:

\[
\text{Maximizar } Z = \sum_{i=1}^{10} v_i x_i
\]

### **3.4 Restrições**

Restrição de capacidade:

\[
\sum_{i=1}^{10} p_i x_i \leq C
\]

Restrições de domínio:

\[
x_i \in \\{0,1\\}, \quad \forall i
\]

## **4. Dados do Problema**

| Item | Peso (p_i) | Valor (v_i) |
| ---- | ---------- | ------------ |
| 1    | 3          | 24           |
| 2    | 2          | 13           |
| 3    | 4          | 28           |
| 4    | 1          | 6            |
| 5    | 5          | 33           |
| 6    | 2          | 14           |
| 7    | 6          | 40           |
| 8    | 3          | 19           |
| 9    | 7          | 45           |
| 10   | 4          | 26           |

Capacidades analisadas:

* **Cenário A:** C = 15
* **Cenário B:** C = 18

## **5. Implementação Computacional**

A implementação foi realizada utilizando o **Excel Solver**.

## **6. Resultados Obtidos**

### **6.1 Cenário A – Capacidade C = 15**

Solução ótima: **Itens 1, 3, 6 e 7**

Valor total: **106**

### **6.2 Cenário B – Capacidade C = 18**

Solução ótima: **Itens 1, 3, 5 e 7**

Valor total: **125**

## **7. Comparação Entre os Cenários**

| Capacidade | Valor Máximo | Itens Selecionados |
|-----------|--------------|---------------------|
| 15        | 106          | 1, 3, 6, 7          |
| 18        | 125          | 1, 3, 5, 7          |

## **8. Análise de Sensibilidade**

A análise de sensibilidade tem como objetivo avaliar como alterações em parâmetros importantes do modelo influenciam a solução ótima. Neste trabalho, foram avaliados dois parâmetros principais: **capacidade da mochila (C)** e **valor dos itens (vᵢ)**.

### **8.1 Variação da Capacidade da Mochila**
Foram testadas capacidades alternativas além das capacidades base (15 e 18). Observou-se que:

* Incrementos pequenos de capacidade permitem incluir itens de maior valor relativo ao peso.
* A partir de certos limiares de capacidade, a solução ótima muda abruptamente, substituindo itens de menor eficiência por itens mais valiosos.
* Quando a capacidade aumenta de 15 para 18, por exemplo, o item 5 passa a integrar a solução em substituição ao item 6, aumentando o valor total obtido.

Esse comportamento evidencia que a **capacidade é um parâmetro altamente sensível**, e ajustes mesmo pequenos podem impactar significativamente o resultado.

### **8.2 Variação do Valor dos Itens**
Também foram testadas alterações nos valores de itens individuais, como aumentos ou reduções de 10% a 20%.

Os resultados apontaram que:

* Itens com maior **razão valor/peso** são os que mais influenciam a solução. Pequenas alterações em seus valores podem mudar a composição final.
* Itens pouco eficientes (baixo valor e baixo peso) tendem a não afetar a solução, mesmo com variações moderadas de valor.
* Em diversos testes, aumentar o valor do item 5 tornou a solução com esse item ainda mais dominante quando a capacidade permitia sua inclusão.

Assim, o modelo apresenta comportamento coerente: **itens mais valiosos têm maior poder de alterar a solução ótima** quando seus parâmetros são modificados.

## **9. Interpretação Gerencial dos Resultados**

A interpretação dos resultados permite transformar a análise matemática em decisões práticas:

### **9.1 Priorização de Itens**
A análise mostra que itens com melhor relação valor/peso devem ser priorizados quando há restrição de capacidade — sendo os principais candidatos os itens 3, 5 e 7.

### **9.2 Impacto da Capacidade**
Pequenos aumentos de capacidade podem gerar **saltos significativos de valor**, justificando investimentos em maior capacidade de transporte quando economicamente viável.

### **9.3 Robustez da Solução**
O modelo se mostrou robusto: mesmo com modificações moderadas no valor dos itens, a maioria das escolhas ótimas se manteve estável, exceto para itens muito eficientes.

### **9.4 Apoio à Tomada de Decisão**
Os resultados permitem que gestores entendam:

* quais itens valem mais a pena transportar;
* como pequenas mudanças operacionais (como capacidade extra) podem aumentar o retorno;
* quais itens realmente influenciam a otimização e quais têm efeito marginal.

Em resumo, o modelo fornece **um guia claro de prioridade**, permitindo decisões mais eficientes sob restrições de espaço e peso.

## **10. Interpretação Gerencial**

Os intervalos mostram que:

* A solução é **robusta** para vários coeficientes (intervalos amplos).
* Itens altamente eficientes (3, 5, 7) mantêm-se na solução mesmo com grande variação.
* A capacidade influencia fortemente a composição final.

