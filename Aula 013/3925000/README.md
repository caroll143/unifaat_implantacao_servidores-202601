1-a)Control Plane: é a parte responsável por gerenciar o cluster Kubernetes. Ele executa componentes como o servidor da API, o agendador (scheduler) e o controlador (controller manager), tomando decisões sobre onde os pods serão executados e mantendo o estado desejado do cluster. No Amazon EKS, o Control Plane é gerenciado pela AWS.

Worker Nodes: são as máquinas (instâncias EC2 ou nós gerenciados) que executam as aplicações em contêineres. Neles ficam os pods e o agente do Kubernetes responsável pela comunicação com o Control Plane. Os Worker Nodes são gerenciados pelo cliente, embora a AWS possa auxiliar na administração quando são utilizados Managed Node Groups.



b)Quando um pod falha, é encerrado inesperadamente ou deixa de responder, o Kubernetes detecta o problema por meio dos seus controladores. Se o pod fazia parte de um Deployment, ReplicaSet ou outro controlador, o sistema cria automaticamente um novo pod para substituir o que falhou, garantindo que a quantidade de réplicas configurada continue sendo executada e que a aplicação permaneça disponível.





2-a)O Deployment é o recurso responsável por criar, atualizar e gerenciar os Pods da aplicação, garantindo que a quantidade desejada de réplicas esteja sempre em execução. Já o Service é responsável por fornecer um ponto de acesso estável aos Pods, permitindo que outras aplicações ou usuários se comuniquem com eles, mesmo que os Pods sejam recriados e tenham seus endereços IP alterados.



b)Labels são etiquetas compostas por pares de chave e valor utilizadas para identificar e organizar objetos no Kubernetes, como os Pods. Selectors são regras usadas para selecionar objetos que possuem determinadas labels. Um Service utiliza Selectors para localizar os Pods corretos e direcionar o tráfego para eles. Por exemplo, se um Service possui um selector com o valor app=web, ele enviará as requisições apenas para os Pods que tiverem a label app=web.



c)As sondas são mecanismos utilizados para verificar a saúde e a disponibilidade dos contêineres. A livenessProbe verifica se o contêiner continua funcionando corretamente; caso a aplicação trave ou deixe de responder, o Kubernetes reinicia o contêiner automaticamente. Já a readinessProbe verifica se a aplicação está pronta para receber requisições. Enquanto ela indicar que o Pod não está pronto, o Kubernetes impede que o Service envie tráfego para ele. Um exemplo de uso da livenessProbe é detectar uma aplicação que entrou em deadlock. Um exemplo de uso da readinessProbe é aguardar que a aplicação termine sua inicialização e estabeleça conexão com o banco de dados antes de começar a atender os usuários.





3-a) O cluster EKS precisa de um papel IAM próprio, chamado EKSClusterRole, para que o serviço Amazon EKS tenha permissão para interagir com outros serviços da AWS e gerenciar os recursos necessários ao funcionamento do cluster. Essa função permite ações como criar e gerenciar interfaces de rede, monitorar recursos e coordenar operações relacionadas ao ambiente Kubernetes. Sem esse papel IAM, o EKS não conseguiria administrar corretamente o Control Plane do cluster.



b) Os Worker Nodes precisam da política AmazonEC2ContainerRegistryReadOnly para obter permissão de leitura no Amazon ECR (Elastic Container Registry). Essa política permite que os nós autentiquem-se no ECR e façam o download das imagens dos contêineres que serão executados nos Pods. Se essa política não estiver anexada, os Worker Nodes não conseguirão baixar as imagens armazenadas no ECR, fazendo com que os Pods falhem na inicialização e apresentem erros como ImagePullBackOff ou ErrImagePull.





4-a) O ClusterIP é o tipo padrão de Service no Kubernetes e expõe a aplicação apenas dentro do próprio cluster, permitindo a comunicação interna entre os componentes. O NodePort expõe a aplicação através de uma porta fixa em cada Worker Node, possibilitando o acesso externo utilizando o endereço IP do nó e a porta configurada. Já o LoadBalancer expõe a aplicação para acesso externo por meio de um balanceador de carga criado pelo provedor de nuvem, fornecendo um endereço IP ou DNS público para os usuários acessarem o serviço.



b) Quando um Service do tipo LoadBalancer é criado no Amazon EKS, a AWS provisiona automaticamente um Elastic Load Balancer (ELB) para distribuir o tráfego externo para os Worker Nodes e, consequentemente, para os Pods da aplicação. Esse recurso recebe as requisições dos usuários e as encaminha para os destinos corretos no cluster.



c) É importante excluir o Service do tipo LoadBalancer antes de excluir o cluster EKS porque o balanceador de carga criado pela AWS pode permanecer ativo caso não seja removido corretamente. Isso pode gerar recursos órfãos na conta da AWS e custos desnecessários, já que o Load Balancer continua sendo cobrado mesmo após a exclusão do cluster. Além disso, remover o Service primeiro ajuda a garantir uma limpeza adequada de todos os recursos associados ao ambiente.

