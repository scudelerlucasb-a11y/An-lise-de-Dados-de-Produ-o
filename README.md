# Alpha-SP Indústria — Análise de Dados de Produção

Análise em Python/Pandas dos dados de produção de uma indústria metalúrgica fictícia, cruzando registros diários de produção com cadastro de máquinas e metas mensais para identificar custos, riscos de qualidade e gargalos operacionais.

## 📌 Sobre o Projeto

Fábricas que operam múltiplas máquinas em diferentes setores (usinagem, estamparia, soldagem) geram dados de produção diária, mas raramente esses dados vêm sozinhos — eles precisam ser cruzados com outras fontes, como cadastro de equipamentos, custos operacionais e metas definidas pela gerência, para gerar uma análise realmente útil para a tomada de decisão.

Este projeto simula esse cenário: parte de um CSV com o histórico diário de produção de 3 máquinas ao longo de 6 meses e o combina com uma planilha Excel contendo o cadastro das máquinas (fabricante, ano de aquisição, custo por hora, capacidade máxima) e as metas mensais de produção e qualidade por setor. A partir desse cruzamento, o projeto responde a perguntas de negócio concretas sobre custo, qualidade, cumprimento de metas e utilização de capacidade.

## 🎯 Objetivo

Consolidar múltiplas fontes de dados (CSV + planilha Excel com duas abas) em uma única base analítica e, a partir dela, responder perguntas que apoiem decisões de manutenção, investimento e gestão de metas na fábrica.

## 💼 Aplicação no Mundo Real

Uma empresa do setor industrial poderia utilizar uma análise como essa para embasar reuniões mensais de gestão da produção. Por exemplo:

> O gestor de operações puxa o relatório para a reunião mensal e identifica que o setor de Estamparia descumpre a meta de qualidade com quase o dobro de frequência dos demais setores, e que a máquina mais antiga da fábrica é a que mais gera peças defeituosas — informação que embasa a priorização de manutenção preventiva ou substituição do equipamento.

## 🚀 Funcionalidades

* Leitura e combinação (merge) de um CSV de produção diária com duas abas de uma planilha Excel (cadastro de máquinas e metas mensais)
* Tratamento de inconsistências nos dados de origem (linhas de observação/nota misturadas aos dados reais)
* Cálculo do custo total de operação por máquina, a partir de horas de uso e custo por hora
* Análise da relação entre idade da máquina (ano de aquisição) e taxa média de defeito
* Identificação de dias, meses e setores em que a produção ficou abaixo da meta definida
* Identificação de dias em que a taxa de defeito ultrapassou a meta de qualidade, por mês e setor
* Comparação entre produção média diária e capacidade máxima cadastrada de cada máquina
* Visualização gráfica de um dos indicadores (dias acima da meta de qualidade, por setor)

## 🛠️ Tecnologias Utilizadas

* Python
* Pandas
* Matplotlib
* Jupyter Notebook

## 📂 Estrutura do Projeto

```text
alpha-sp-analise-producao/
│
├── data/
│   ├── alpha_sp_producao_diaria.csv
│   └── dados_complementares_alpha_sp.xlsx
│
├── notebooks/
│   └── Desafio_Extra_Alpha_SP.ipynb
│
├── README.md
└── requirements.txt
```

*Sugestão: caso o repositório também inclua a análise anterior (feita apenas com o CSV, antes do cruzamento com o Excel), ela pode ser adicionada em `notebooks/` como um segundo arquivo, mantendo o histórico de evolução do projeto.*

## ⚙️ Como Executar

```bash
git clone https://github.com/scudelerlucasb-a11y/alpha-sp-analise-producao.git
cd alpha-sp-analise-producao
```

Instale as dependências:

```bash
pip install -r requirements.txt
```

*Sugestão de conteúdo para o `requirements.txt`:*

```text
pandas
matplotlib
openpyxl
jupyter
```

## ▶️ Como Utilizar

1. Abra o notebook `notebooks/Desafio_Extra_Alpha_SP.ipynb` no Jupyter, VS Code ou Google Colab.
2. Garanta que os arquivos `alpha_sp_producao_diaria.csv` e `dados_complementares_alpha_sp.xlsx` estejam acessíveis no caminho esperado pelo notebook (pasta `data/`, ou ajuste o caminho nas células de leitura).
3. Execute as células em ordem, do início ao fim.

## 📊 Exemplo de Uso

**Entrada dos dados:** registros diários de produção por máquina/setor (CSV) + cadastro de máquinas e metas mensais (Excel, duas abas).

**Processamento:** os dados são combinados (merge) usando `maquina` como chave para o cadastro, e `mes` + `setor` como chave composta para as metas.

**Resultado esperado (um dos indicadores gerados):**

```text
maquina
Solda Robô 01    69665.4
Torno CNC 03     51297.5
Prensa 12        42387.2
Name: custo_operacao_dia, dtype: float64
```

**Interpretação:** a Solda Robô 01 foi a máquina mais cara para operar ao longo dos 6 meses analisados, o que, combinado com os demais indicadores do notebook, ajuda a priorizar onde investigar custos ou negociar manutenção.

## 🔮 Melhorias Futuras

* Dashboard interativo (ex.: Streamlit ou Power BI) para consulta dos indicadores sem precisar rodar o notebook — *Sugestão*
* Automatizar a geração mensal do relatório a partir de novos arquivos de entrada — *Sugestão*
* Adicionar testes automatizados para validar a integridade dos merges — *Sugestão*
* Expandir a análise para prever, com base no histórico, meses/setores com maior risco de descumprir metas — *Sugestão*

## 📚 Aprendizados

Este projeto permite demonstrar manipulação e limpeza de dados com Pandas, combinação de múltiplas fontes de dados heterogêneas (CSV e Excel com múltiplas abas), construção de indicadores de negócio a partir de dados brutos, e comunicação de resultados analíticos por meio de gráficos.

## 👨‍💻 Autor

**Lucas Braga Scudeler**

* GitHub: [https://github.com/scudelerlucasb-a11y](https://github.com/scudelerlucasb-a11y)
* LinkedIn: [www.linkedin.com/in/lucas-braga-scudeler](http://www.linkedin.com/in/lucas-braga-scudeler)
