1.a) CI (Integração Contínua):

O principal objetivo da Integração Contínua (Continuous Integration) é integrar frequentemente as alterações de código feitas pelos desenvolvedores em um repositório central. Nessa fase, o código é automaticamente compilado, testado e validado para identificar erros rapidamente e garantir que as novas alterações não comprometam o funcionamento da aplicação.



b) CD (Entrega/Implantação Contínua):

O principal objetivo da Entrega/Implantação Contínua (Continuous Delivery/Continuous Deployment) é automatizar o processo de disponibilização dos artefatos gerados na fase de CI. Os artefatos construídos (como imagens Docker, pacotes ou executáveis) são preparados e enviados para ambientes de teste, homologação ou produção. Na Entrega Contínua, a implantação em produção normalmente depende de uma aprovação manual. Já na Implantação Contínua, a publicação em produção ocorre automaticamente após a aprovação dos testes e validações.



2.Jenkins – ferramenta de código aberto muito utilizada para automação de integração contínua. Permite configurar pipelines para compilar o código, executar testes automatizados e gerar imagens Docker.

GitHub Actions – serviço integrado ao GitHub que possibilita criar fluxos de trabalho automatizados. Pode executar testes, realizar builds e criar imagens Docker sempre que houver alterações no repositório.

AWS CodeBuild – serviço da AWS totalmente gerenciado para CI. Ele compila o código-fonte, executa testes automatizados e constrói artefatos, incluindo imagens Docker, sem a necessidade de gerenciar servidores.



3.a) A principal vantagem de utilizar o Amazon ECR (Elastic Container Registry) é a maior segurança e controle de acesso. Diferentemente de um repositório público do Docker Hub, o ECR permite armazenar imagens Docker de forma privada, controlando quem pode visualizar, enviar ou baixar as imagens por meio das permissões do AWS IAM. Além disso, ele se integra aos demais serviços da AWS, facilitando a autenticação e o gerenciamento centralizado.



b) O Amazon ECR é um serviço regional, ou seja, os repositórios são criados em uma região específica da AWS, como us-east-1 ou sa-east-1.

