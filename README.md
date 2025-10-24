🧮 Detecção de Discrepâncias de Estoque 📦
📋 Descrição

Este projeto tem como objetivo detectar discrepâncias no estoque de produtos com base em dados de compras, vendas e estoque atual.
O sistema compara esses dados, identifica diferenças e fornece sugestões automáticas de correção para manter a consistência das informações.

⚙️ Ideal para pequenas e médias empresas que precisam auditar seus controles de estoque de forma automatizada e confiável.

🎯 Funcionalidades

Detecção de Discrepâncias:
Compara o estoque atual com o estoque esperado, gerando um relatório detalhado de divergências.

Sugestões Automáticas:
Quando uma discrepância é encontrada, o sistema sugere ações corretivas, como registrar compras ou vendas faltantes.

Flexibilidade de Tolerância:
Permite configurar a margem de diferença aceitável entre o estoque esperado e o atual.

🛠️ Tecnologias Utilizadas
Tecnologia	Função
Python	Linguagem principal do projeto
Pandas	Manipulação e análise de dados
NumPy	Cálculos numéricos e matrizes
Dataclasses	Organização estruturada dos dados de discrepâncias
Logging	Registro de logs e mensagens de erro durante o processamento
🚀 Como Usar
🔧 Instalação
# Clone o repositório
git clone https://github.com/seu_usuario/detecao_discrepancias_estoque.git

# Acesse o diretório
cd detecao_discrepancias_estoque

# Instale as dependências
pip install -r requirements.txt

🧠 Exemplo de Uso
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

# Detecta discrepâncias com tolerância de 2 unidades
report = detect_discrepancies(compras_ex, vendas_ex, estoque_ex, tolerance=2)

# Exibe o relatório
print(report)

📊 Resultados Esperados
produto	data	estoque_anterior	compras	vendas	estoque_atual	estoque_esperado	diferenca	tipo_discrepancia	sugestao
Parafuso	2025-09-01	100	100	0	100.0	200	-100.0	falta_registro_venda	Sugerir adicionar venda de 100 unidades
Parafuso	2025-09-02	100	0	10	NaN	90	NaN	estoque_nao_informado	Registro de estoque ausente
Parafuso	2025-09-03	100	20	5	105.0	115	-10.0	erro_lancamento_estoque	Revisar lançamento de estoque (diferença -10)
Parafuso	2025-09-04	105	0	30	70.0	75	-5.0	erro_lancamento_estoque	Revisar lançamento de estoque (diferença -5)
Porca	2025-09-02	50	50	0	50.0	100	-50.0	falta_registro_venda	Sugerir adicionar venda de 50 unidades
🧩 Funções Principais
_ensure_df(df, cols, date_col='data')

Função de validação e normalização de DataFrames.
Garante que as colunas e os tipos de dados estejam corretos.

Parâmetros:

df: DataFrame a ser validado

cols: Lista de colunas esperadas

date_col: Coluna de data (padrão: 'data')

detect_discrepancies(compras_df, vendas_df, estoque_df, tolerance=0)

Função principal — detecta discrepâncias entre compras, vendas e estoque.

Parâmetros:

compras_df: DataFrame de compras

vendas_df: DataFrame de vendas

estoque_df: DataFrame de estoque

tolerance: Tolerância para diferença entre esperado e atual

Retorno:
Um DataFrame com o relatório de discrepâncias e sugestões de correção.

🤝 Contribuindo

Faça um fork do projeto

Crie uma branch:

git checkout -b minha-branch


Realize suas modificações

Faça commit das alterações:

git commit -am "Adicionando nova funcionalidade"


Envie para o repositório:

git push origin minha-branch


Abra um Pull Request 🚀

📜 Licença

Este projeto está licenciado sob a MIT License — veja o arquivo LICENSE para mais detalhes.