[ISI] Trabalho Prático I: Integração e Análise de Dados de Saúde (Reservas e Dadores)
🎯 Objetivo do Projeto
Este repositório contém o trabalho prático desenvolvido no âmbito da Unidade Curricular de Integração de Sistemas de Informação (ISI). O foco é aplicar e experimentar processos de ETL (Extract, Transform and Load) para integrar dados de saúde dispersos em formato JSON, transformá-los e prepará-los para análise.

O objetivo principal é consolidar datasets de Reservas de Componentes Sanguíneos e Dadores (1ª Vez e Regulares) por Região e Entidade, culminando na produção de um dataset limpo e estruturado.

🛠️ Tecnologias Utilizadas
Categoria	Ferramenta	Função no Projeto	
Critério de Mais-Valia 

ETL	KNIME Analytics Platform	
Desenvolvimento e execução do Job de ETL.

Sim (Ferramenta de suporte a ETL)
Fonte de Dados	JSON	
Formato de dados de entrada brutos (ex: reservas.json).

Sim (Serialização de JSON)
Destino de Dados	Parquet	Formato de ficheiro otimizado para a carga e análise posterior (DadosDadiva.parquet).	Sim (Diversidade de formatos)
Visualização	Microsoft Power BI / Similar	
Criação de dashboards para análise dos resultados.

Sim (Visualização dos resultados)

Exportar para Sheets
⚙️ Processo ETL (KNIME Workflow)
O fluxo de trabalho foi construído no KNIME e está dividido em três fases principais, conforme os princípios de ETL:

1. Extract & Initial Transformation

Leitura JSON: Leitura das diferentes fontes JSON (Reservas e Dadores).

JSON Path: Extração de campos aninhados como Entidade, Região, Reservas, Periodo, Latitude e Longitude.

Ungroup: Desagrupamento das colunas de lista para formar linhas atómicas.

Filtragem: Aplicação de filtros por valores nominais na coluna Região.

2. Transform & Integrate
Manipulação de Data: O campo Periodo (formato YYYY-MM) é manipulado usando String Manipulation (join($Periodo$, "-01")) e convertido para o tipo Date&Time.

Joins: Integração das pipelines de Reservas e Dadores através de um nó Joiner com a correspondência dupla Entidade AND Região.

Tratamento de Missing Values: Substituição de valores nulos em colunas numéricas (Float e Integer) por zero (0).

3. Load
Parquet Writer: Carregamento dos dados limpos e integrados para o ficheiro DadosDadiva.parquet.

📊 Resultados da Análise (Visualizações)
O dataset final processado foi utilizado para gerar visualizações que permitem auditar a distribuição de reservas e dadores:

Visualização	Destaque	Imagem de Referência
Soma de Reservas por Região	Demonstra o volume total de reservas, onde a Entidade Central (IPST, IP) é a dominante.	[image_5793a5.png]
Soma de Dadores por Região	Compara a distribuição de dadores 1a Vez e Regulares, confirmando a prevalência da Entidade Central.	[image_5793e4.png]

🚀 Trabalhos Futuros

Orquestração: Explorar ferramentas como Node-RED ou Apache Airflow para agendamento e monitorização do Job de ETL (Job Control).

Expressões Regulares (ER): Introduzir o uso de ER para normalização e limpeza mais robusta dos campos Região e Entidade.

Desenvolvido por:Hélder Costa
Integração de API: Explorar o acesso a APIs remotas para enriquecer os dados extraídos.

Desenvolvido por: [Nome do Aluno]
