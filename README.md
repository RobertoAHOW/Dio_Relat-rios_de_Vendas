# Características

- A empresa foca apenas em fabricação de consoles, deixando a distribuição e venda para terceiros
- Os produtos são vendidos globalmente

# PROMPTS

# Prompt: Produto mais vendido e Dashboard

---

## Pergunta: Qual o produto mais vendido?

### Código em Python

```python
# Importar a biblioteca pandas para manipulação de dados
import pandas as pd

# Carregar o arquivo Excel enviado pelo usuário
file_path = '/mnt/data/Meganium_Sales_data.xlsx'
sales_data = pd.ExcelFile(file_path)

# Exibir os nomes das abas do arquivo Excel para entender sua estrutura
sales_data.sheet_names

# Carregar os dados da aba "Consolidate" para análise
df = sales_data.parse('Consolidate')

# Exibir as primeiras linhas do DataFrame para visualizar sua estrutura
df.head()

# Determinar o produto mais vendido com base no total de quantidade vendida
most_sold_product = df.groupby('product_sold')['quantity'].sum().idxmax()  # Obter o nome do produto mais vendido
most_sold_product_quantity = df.groupby('product_sold')['quantity'].sum().max()  # Obter a quantidade total do produto mais vendido

most_sold_product, most_sold_product_quantity

## Ordenação de Vendas por País e Produto

Ordene as vendas de produto, do mais vendido para o menos vendido em cada país, exibindo o país, produto e a quantidade vendida.

```python
# Agrupar os dados por país e produto e somar as quantidades vendidas
sales_by_country_product = df.groupby(['delivery_country', 'product_sold'])['quantity'].sum()

# Ordenar os resultados dentro de cada país, do mais vendido para o menos vendido
sales_by_country_product = sales_by_country_product.sort_values(ascending=False).reset_index()

# Renomear as colunas para clareza
sales_by_country_product.columns = ['País', 'Produto', 'Quantidade Vendida']

# Converter os dados para markdown
sales_by_country_product_md = sales_by_country_product.to_markdown(index=False)
sales_by_country_product_md


# PLANEJAMENTO LÓGISTICO:

# 🚛 Como Otimizar o Processo de Transporte e Logística até o Momento da Venda

## 1️⃣ **Planejamento e Roteirização**
- 🗺️ **Roteirização inteligente:** Utilize softwares de roteirização para otimizar trajetos, reduzir custos e evitar atrasos.  
- 📦 **Agrupamento de entregas:** Combine pedidos para destinos próximos em um único envio, diminuindo viagens e custos.

---

## 2️⃣ **Monitoramento em Tempo Real**
- 📡 **Rastreio de frotas:** Use sistemas de GPS para monitorar veículos em tempo real.  
- 🔮 **Análise preditiva:** Antecipe atrasos com base em dados históricos e eventos externos, como condições climáticas.

---

## 3️⃣ **Gestão de Estoques**
- 🏢 **Centros de distribuição descentralizados:** Posicione estoques estrategicamente próximos aos principais mercados consumidores.  
- 🔄 **Cross-docking:** Reduza o armazenamento ao mínimo, transferindo produtos diretamente da chegada ao envio.

---

## 4️⃣ **Integração Tecnológica**
- 💻 **Sistemas de gestão integrados (ERP/TMS):** Centralize informações de transporte, estoque e pedidos para maior controle e automação.  
- ⚙️ **Automação de processos:** Automatize tarefas como geração de pedidos e rastreamento.

---

## 5️⃣ **Colaboração e Parcerias**
- 🤝 **Terceirização:** Trabalhe com transportadoras especializadas para reduzir custos fixos e ampliar a capacidade.  
- 🏗️ **Parcerias logísticas:** Estabeleça contratos com provedores de serviços logísticos para maior eficiência.

---

## 6️⃣ **Sustentabilidade e Eficiência**
- 🚗 **Uso de veículos elétricos ou híbridos:** Reduza custos com combustível e impacto ambiental.  
- 📊 **Consolidação de cargas:** Aumente a ocupação dos veículos para diminuir o número de viagens.

---

## 7️⃣ **Análise de Indicadores de Desempenho (KPIs)**
- 📈 **KPIs essenciais:** Monitore métricas como prazo de entrega, custo por entrega, taxa de ocupação de veículos e índice de devoluções.  
- 🔄 **Otimização contínua:** Utilize os dados coletados para ajustar rotas, processos e estratégias.

---

🎯 **Essas abordagens, combinadas, ajudam a reduzir custos, melhorar a eficiência e aumentar a satisfação do cliente no momento da venda.**
