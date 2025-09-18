Detecção de Discrepâncias de Estoque

Este projeto tem como objetivo detectar discrepâncias no estoque de produtos com base em dados de compras, vendas e o estoque atual. Através de um conjunto de funções, o sistema compara os dados de estoque, compras e vendas, identificando diferenças e fornecendo sugestões de ajustes.

Funcionalidades

Detecção de Discrepâncias: O sistema compara o estoque atual com o esperado, gerando um relatório de discrepâncias.

Sugestões Automáticas: Quando uma discrepância é encontrada, o sistema sugere ações corretivas, como registrar compras ou vendas faltantes.

Flexibilidade: O tolerância de diferença entre o estoque esperado e o atual pode ser configurada para permitir ajustes mais flexíveis.

Tecnologias Usadas

Python: A linguagem principal do projeto.

Pandas: Para manipulação e análise de dados.

Numpy: Utilizado para cálculos numéricos.

Dataclasses: Para organizar e estruturar os dados de discrepâncias.

Logging: Para registrar informações e mensagens de erro durante o processamento dos dados.

Como Usar
Instalação

Clone este repositório:

git clone https://github.com/seu_usuario/detecao_discrepancias_estoque.git


Navegue para o diretório do projeto:

cd detecao_discrepancias_estoque


Instale as dependências:

pip install -r requirements.txt

Exemplo de Uso

Você pode usar a função detect_discrepancies passando os DataFrames de compras, vendas e estoque como entrada. A função retorna um relatório com as discrepâncias detectadas.

Exemplo de Código:
import pandas as pd
from seu_script import detect_discrepancies

# Dados de compras
compras_ex = pd.DataFrame([
    {'data':'2025-09-01','produto':'Parafuso','quantidade_comprada':100},
    {'data':'2025-09-03','produto':'Parafuso','quantidade_comprada':20},
    {'data':'2025-09-02','produto':'Porca','quantidade_comprada':50},
])

# Dados de vendas
vendas_ex = pd.DataFrame([
    {'data':'2025-09-02','produto':'Parafuso','quantidade_vendida':10},
    {'data':'2025-09-03','produto':'Parafuso','quantidade_vendida':5},
    {'data':'2025-09-04','produto':'Parafuso','quantidade_vendida':30},
    {'data':'2025-09-03','produto':'Porca','quantidade_vendida':5},
])

# Dados de estoque
estoque_ex = pd.DataFrame([
    {'data':'2025-09-01','produto':'Parafuso','quantidade_em_estoque':100},
    {'data':'2025-09-03','produto':'Parafuso','quantidade_em_estoque':105},
    {'data':'2025-09-04','produto':'Parafuso','quantidade_em_estoque':70},
    {'data':'2025-09-02','produto':'Porca','quantidade_em_estoque':50},
    {'data':'2025-09-03','produto':'Porca','quantidade_em_estoque':45},
])

# Detecta as discrepâncias
report = detect_discrepancies(compras_ex, vendas_ex, estoque_ex, tolerance=2)

# Exibe o relatório
print(report)

Resultados Esperados

O sistema irá gerar um DataFrame com as seguintes colunas:

produto: Nome do produto.

data: Data do movimento.

estoque_anterior: Estoque antes do movimento.

compras: Quantidade comprada.

vendas: Quantidade vendida.

estoque_atual: Estoque após o movimento.

estoque_esperado: Estoque calculado com base nas compras e vendas.

diferenca: Diferença entre o estoque atual e o estoque esperado.

tipo_discrepancia: Tipo de discrepância encontrada (ex: falta de registro de venda, erro de lançamento de estoque).

sugestao: Sugestões para corrigir a discrepância (ex: adicionar venda ou compra).

Funções
_ensure_df(df, cols, date_col='data')

Esta função valida e normaliza um DataFrame, garantindo que as colunas e os tipos de dados sejam corretos.

Parâmetros:

df: O DataFrame a ser validado.

cols: As colunas esperadas.

date_col: O nome da coluna de data (por padrão, 'data').

detect_discrepancies(compras_df, vendas_df, estoque_df, tolerance=0)

Esta é a função principal que detecta as discrepâncias entre os dados de compras, vendas e estoque.

Parâmetros:

compras_df: DataFrame com dados de compras.

vendas_df: DataFrame com dados de vendas.

estoque_df: DataFrame com dados de estoque.

tolerance: Valor de tolerância para a diferença entre o estoque esperado e o atual (padrão é 0).

Retorno: Um DataFrame com o relatório de discrepâncias detectadas.

Exemplo de Relatório

Um exemplo de saída pode ser o seguinte:

produto	data	estoque_anterior	compras	vendas	estoque_atual	estoque_esperado	diferenca	tipo_discrepancia	sugestao
Parafuso	2025-09-01	100	100	0	100.0	200	-100.0	falta_registro_venda	Sugerir adicionar venda de 100 unidades.
Parafuso	2025-09-02	100	0	10	NaN	90	NaN	estoque_nao_informado	Registro de estoque ausente.
Parafuso	2025-09-03	100	20	5	105.0	115	-10.0	erro_lancamento_estoque	Revisar lançamento de estoque (diferenca -10)
Parafuso	2025-09-04	105	0	30	70.0	75	-5.0	erro_lancamento_estoque	Revisar lançamento de estoque (diferenca -5)
Porca	2025-09-02	50	50	0	50.0	100	-50.0	falta_registro_venda	Sugerir adicionar venda de 50 unidades.
Contribuindo

Se você gostaria de contribuir para este projeto, siga as etapas:

Faça um fork do repositório.

Crie uma nova branch (git checkout -b minha-branch).

Realize as alterações desejadas.

Faça commit das suas alterações (git commit -am 'Adicionando nova funcionalidade').

Faça push para a branch (git push origin minha-branch).

Abra um pull request.

Licença

Este projeto está licenciado sob a MIT License - veja o arquivo LICENSE
 para mais detalhes.