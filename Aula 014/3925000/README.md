1-a) Os três pilares da observabilidade são métricas, logs e traces.

Métricas: acompanham desempenho e saúde do sistema.

Logs: registram eventos e erros.

Traces: rastreiam o caminho das requisições.



b) No Amazon Elastic Kubernetes Service (EKS):

Métricas → Amazon CloudWatch

Logs → Amazon CloudWatch Logs

Traces → AWS X-Ray



c) Monitoramento detecta problemas e mostra o que está acontecendo.

Observabilidade ajuda a entender a causa do problema.

Por isso, só monitorar não basta, pois nem sempre mostra a origem da falha.





2-a) O Fluent Bit é uma ferramenta de coleta e envio de logs. No EKS, ele é implantado como DaemonSet para garantir que exista um pod em cada node do cluster, coletando logs de todos os containers.



b) No Amazon CloudWatch Logs:

Log Group: é o agrupamento de logs de uma aplicação ou serviço.

Log Stream: é o fluxo individual de logs dentro do grupo, geralmente separado por pod ou instância.



c) Configurar retenção é importante para controlar armazenamento e custos. Sem isso, os logs ficam guardados por tempo indeterminado, ocupando espaço e aumentando gastos.





3-a) As métricas padrão do Amazon Elastic Kubernetes Service (EKS) mostram dados básicos do cluster, como nodes e status. Já o Amazon CloudWatch Container Insights fornece métricas mais detalhadas, como uso de CPU, memória, rede e disco de pods e containers.



b) O namespace ContainerInsights no Amazon CloudWatch é onde ficam armazenadas as métricas coletadas do cluster. Ele guarda dados de desempenho de nodes, pods, containers e serviços.



c) O comando kubectl top pods mostra o consumo atual de CPU e memória de cada pod. Ele é útil para monitoramento em tempo real porque ajuda a identificar rapidamente pods com alto uso de recursos.





4-a) No Amazon CloudWatch, Threshold é o limite que dispara o alerta (ex: CPU > 80%). Evaluation Periods é a quantidade de vezes que a métrica é analisada antes de acionar o alarme. Usar mais de 1 período evita falsos positivos causados por picos momentâneos.



b) Os 4 Golden Signals do Google Site Reliability Engineering são:

Latência: tempo de resposta da aplicação (ex: API demorando 2s).

Tráfego: quantidade de requisições recebidas (ex: 500 acessos/minuto).

Erros: taxa de falhas (ex: erros 500).

Saturação: uso de recursos (ex: CPU em 90%).



c)Alerta acionável: informa um problema claro e o que deve ser corrigido. Ex: “CPU acima de 90% por 5 min”.

Alerta genérico: avisa algo sem contexto suficiente. Ex: “Sistema com problema”.





1\. Cluster EKS criado



Print mostrando o cluster ativo e os nodes em estado Ready.



2\. Deploy da aplicação



Print do comando kubectl get pods -A mostrando os pods em execução.



3\. Serviço LoadBalancer



Print do comando kubectl get svc -A mostrando o LoadBalancer criado.



4\. Monitoramento no CloudWatch



Print das métricas da aplicação no Amazon CloudWatch.



5\. Alarmes configurados



Print dos alarmes criados para CPU, memória ou erros da aplicação.

