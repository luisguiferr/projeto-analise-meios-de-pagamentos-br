# 📊 Análise dos Meios de Pagamento no Brasil (2010–2025)

Este projeto realiza uma análise detalhada da evolução dos principais meios de pagamento no Brasil ao longo de 190 meses, de janeiro de 2010 a outubro de 2025.
O objetivo é compreender como o sistema de pagamentos evoluiu em valores movimentados, quantidade de operações e comportamento dos usuários — especialmente antes e depois do lançamento do Pix, em 2020.

Todo o desenvolvimento foi realizado em Python, utilizando Jupyter Notebook para manipulação, visualização e interpretação dos dados.

## 📁 Estrutura do Projeto

Coleta dos dados diretamente da API Olinda (Banco Central do Brasil).

Tratamento e padronização da série histórica.

Análises anuais e mensais por valor e quantidade de operações.

Visualizações com Matplotlib, Plotly e Seaborn.

Avaliação comparativa dos principais meios de pagamento:

- Pix

- TED

- DOC

- TEC

- Boleto

- Cheque

Conclusões sobre tendências, substituições e comportamento do consumidor.

## 🧰 Bibliotecas Utilizadas

Neste projeto utilizamos um conjunto de bibliotecas essenciais para análise de dados, manipulação de informações e visualização gráfica. A seguir, um resumo das funções de cada uma:

Manipulação e Estruturação de Dados

- pandas (pd):
Manipulação de DataFrames, limpeza, agregação, filtragens e transformação dos dados tabulares.

- NumPy (np):
Suporte a cálculos matemáticos e estruturas de arrays multidimensionais de forma eficiente.

Coleta e Processamento de Dados

- requests:
Realização de requisições HTTP para acessar dados diretamente da API.

- json:
Leitura, escrita e manipulação de dados em formato JSON, muito utilizado em APIs.

Visualização e Exploração

- matplotlib.pyplot (plt):
Base para criação de gráficos estáticos customizados.

- seaborn (sns):
Extensão do Matplotlib para gráficos estatísticos mais elegantes e exploratórios.

- plotly.express (px):
Criação de visualizações interativas e dinâmicas.

- FuncFormatter (matplotlib.ticker):
Formatação personalizada de valores nos eixos dos gráficos.

Essas bibliotecas foram utilizadas ao longo do notebook para realizar desde a coleta e preparação dos dados até a criação de gráficos e visualizações avançadas.

## 🌐 Fonte dos Dados — API Olinda (Banco Central do Brasil)

Os dados foram obtidos a partir da Plataforma Olinda, por meio do serviço:

MPV_DadosAbertos (v1)
URL base (OData):

https://olinda.bcb.gov.br/olinda/servico/MPV_DadosAbertos/versao/v1/odata/

### Protocolo

OData (Open Data Protocol):
Permite consultas REST padronizadas e seleção de campos.

### Formatos Disponíveis

- JSON

- XML

- CSV

- Entre outros

### Endpoint Utilizado

Recurso utilizado para obter os dados mensais:

MeiosdePagamentosMensalDA, que retorna:

- boletos

- transferências (TED, DOC, TEC)

- cheques

- Pix

- valores e quantidades por mês

## 📑 Variáveis Coletadas

Cada chamada retorna os seguintes campos:

 AnoMes – período no formato AAAAMM

- quantidadePix

- valorPix

- quantidadeTED

- valorTED

- quantidadeTEC

- valorTEC

- quantidadeCheque

- valorCheque

- quantidadeBoleto

- valorBoleto

- quantidadeDOC

- valorDOC

## 📌 Exemplo de Chamada ao Endpoint

```python
# Endpoint utilizado
url = "https://olinda.bcb.gov.br/olinda/servico/MPV_DadosAbertos/versao/v1/odata/MeiosdePagamentosMensalDA(AnoMes=@AnoMes)?@AnoMes='201001'&$format=json&$select=AnoMes,quantidadePix,valorPix,quantidadeTED,valorTED,quantidadeTEC,valorTEC,quantidadeCheque,valorCheque,quantidadeBoleto,valorBoleto,quantidadeDOC,valorDOC"

# Dataframe com os dados brutos
dados = pd.read_json(url)
df = pd.json_normalize(dados['value'])

df.head()
```

## 📈 Resultados Obtidos

A análise completa inclui:

- Evolução anual dos valores transacionados.

- Comportamento dos meios antes do Pix.

- Crescimento acelerado do Pix após 2020.

- Queda e desaparecimento de DOC e TEC.

- Comparação em quantidade de operações entre Pix e demais meios.

- Análise da média de valor por operação, com destaque para:

- TED → transações de maior valor

- Pix → uso cotidiano e substituição do dinheiro físico

## 📝 Conclusão Resumida

O período analisado mostra uma transformação profunda no sistema de pagamentos brasileiro, marcada pelo crescimento do Pix, pela consolidação do TED e pela queda dos instrumentos tradicionais como DOC e TEC. O Pix tornou-se dominante em quantidade de operações e assumiu grande parte dos pagamentos antes feitos em dinheiro, enquanto o TED permaneceu como solução para transações de alto valor.

## 🚀 Tecnologias Utilizadas

- Python 3.10+

- Jupyter Notebook

- Bibliotecas: pandas, numpy, requests, json, matplotlib, seaborn, plotly

## Autor

Desenvolvido por Luís Guilherme Ferreira.

📎 LinkedIn: linkedin.com/in/luís-ferreira-218205175
