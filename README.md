# Upload de arquivos para o Postgres com orquestração pelo Data Factory


Essa é uma definição de pipeline da plataforma de dados Azure Data Factory, que tem como objetivo mover dados de um arquivo CSV local para uma tabela no banco de dados PostgreSQL.

O pipeline é composto por dois activities (atividades):

A primeira atividade, "csvfile_to_lake", copia o arquivo CSV local para um lake (armazenamento) no formato de texto delimitado. Nessa atividade, é definido o source (origem) como o arquivo CSV local, utilizando a opção "DelimitedTextSource". Também é adicionada uma coluna adicional chamada "insert_data" que contém a data atual formatada em dia-mês-ano, que será usada posteriormente na tabela PostgreSQL. O sink (destino) é definido como um Azure Blob Storage com um arquivo CSV delimitado com todas as colunas citadas no arquivo original.

A segunda atividade, "lake_to_postgres", move os dados do lago para a tabela do PostgreSQL. Nessa atividade, é definido o source (origem) como o arquivo CSV armazenado no lake, utilizando a opção "DelimitedTextSource". O sink (destino) é definido como o banco de dados PostgreSQL, utilizando a opção "AzurePostgreSQLSink". É definido também o tamanho do lote (batch) e o tempo máximo para envio do lote. O tipo de escrita é definido como "CopyCommand".

O pipeline utiliza duas referências de dataset, uma para o arquivo CSV local e outra para a tabela do PostgreSQL.

Em resumo, o pipeline lê o arquivo CSV local, o copia para um lago e, em seguida, move os dados do lago para o banco de dados PostgreSQL. Esse pipeline poderia ser agendado para ser executado regularmente ou desencadeado por um evento específico.





Regenerate response

