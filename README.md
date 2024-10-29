# Airflow-DAG
Neste projeto foi implementada uma DAG de orquestração de tarefas utilizando o Apache-Airflow. 

Simulando um ambiente real de empresa, foram gerados dados por uma arquivo JSON de uma turbina eólica a cada intervalo de tempo definido.

Como engenheiro de dados, utilizei um FileSensor para monitorar um diretório e disparar o workflow a cada vez que o arquivo JSON fosse gerado pela turbina eólica, iniciando o processo.

Depois, utilizei o Python Operator para ler o arquivo JSON, separar as variáveis existentes no documento e inserir cada variável em objetos Xcom para compartilharcom as demais tarefas do pipeline, e apagar o arquvio JSON gerado esperando o novo documeno a ser gerado no intervalo de tmepo definido.

Posteriormente as tarefas se dividiram em dois grupos.

Um grupo (Group_check_temp) responsável por checar a temperatura da turbina, utilizando o BranchPythonOperator, orquestrou duas possibilidades de tarefa: envio de Email de alerta se a tempuratura estivesse acima de 24ºC, e o envio de Email nomra de rotina se a tempuratura estivesse abaixo de 24ºC.

Paralelamente, outro grupo (Group_database) ficará responsável por agendar a tarefa de criar uma tabela e inserir os dados nessa tabela utilizando o banco de dados Postgre.




