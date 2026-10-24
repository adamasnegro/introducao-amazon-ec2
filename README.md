☁️ Laboratório AWS — Introdução ao Amazon EC2

!AWS !EC2 !Status

📌 Sobre o projeto

Este laboratório foi realizado durante a Formação em Nuvem com trilha AWS re/Start, oferecida pela Escola da Nuvem.

O objetivo foi praticar a criação, configuração, monitoração e administração de uma instância do Amazon EC2 (Elastic Compute Cloud), além de configurar um servidor web na AWS.

Durante a atividade, foram explorados recursos de rede, segurança, armazenamento, monitoramento e redimensionamento de uma instância virtual.

🎯 Objetivos
Criar e configurar uma instância EC2.
Selecionar uma imagem de máquina Amazon (AMI).
Configurar rede e grupos de segurança.
Habilitar a proteção contra encerramento.
Instalar um servidor web Apache usando User Data.
Monitorar a instância.
Liberar o acesso HTTP pela porta 80.
Redimensionar a instância e o volume EBS.
Testar a proteção contra encerramento.
🛠️ Tecnologias e serviços utilizados
Serviço ou tecnologia	Finalidade
Amazon EC2	Criação e gerenciamento do servidor virtual
Amazon Linux 2023	Sistema operacional
Amazon EBS	Armazenamento em bloco
Security Groups	Controle do tráfego de rede
Apache HTTP Server	Hospedagem da página web
Amazon CloudWatch	Monitoramento de métricas
AWS Management Console	Gerenciamento dos recursos
🚀 Etapas do laboratório
1. Executar uma instância

Início da configuração de uma nova instância pelo Console de Gerenciamento da AWS.

!01 - Executar uma instância

2. Selecionar uma imagem de máquina da Amazon (AMI)

Seleção da imagem Amazon Linux 2023, utilizada como sistema operacional do servidor.

!02 - Selecionar AMI

3. Selecionar um tipo de instância

Configuração inicial da instância t3.micro, com 2 vCPUs e 1 GiB de memória.

!03 - Tipo de instância

4. Configurar um par de chaves

Foi selecionada a opção de continuar sem um par de chaves, pois o acesso SSH não era necessário para as atividades propostas.

!04 - Configurar par de chaves

5. Definir as configurações de rede

Configuração da VPC do laboratório e criação do grupo de segurança Web Server security group.

Inicialmente, as regras de entrada foram removidas para demonstrar como os grupos de segurança controlam o acesso à instância.

!05 - Configurações de rede

6. Adicionar armazenamento

Utilização do volume raiz padrão do Amazon EBS, com capacidade inicial de 8 GiB.

!06 - Adicionar armazenamento

7. Configurar detalhes avançados

Foi habilitada a proteção contra encerramento e configurado um script de inicialização (User Data) para instalar e iniciar o Apache automaticamente.

bash
#!/bin/bash
yum -y install httpd
systemctl enable httpd
systemctl start httpd
echo '<html><h1>Hello From Your Web Server!</h1></html>' > /var/www/html/index.html


O script realiza a instalação do Apache, habilita sua inicialização automática, inicia o serviço e cria uma página HTML simples.

!07 - Detalhes avançados

7.1. Revisar as configurações

Conferência das configurações de inicialização, segurança e script antes de executar a instância.

!07.1 - Revisão das configurações

8. Instância criada

Após a inicialização, foi verificado o estado Running (Em execução) e o resultado das verificações de status.

!08 - Instância criada

🔍 Monitoramento da instância

Foram exploradas as verificações de status do Amazon EC2 e as métricas de monitoramento disponibilizadas pelo Amazon CloudWatch.

As verificações permitem identificar possíveis problemas na infraestrutura ou na acessibilidade da instância.

Também foi explorada a funcionalidade de captura de tela para auxiliar na análise e solução de problemas.

🌐 Configuração e acesso ao servidor web

Inicialmente, o servidor web não estava acessível porque o grupo de segurança não permitia tráfego HTTP de entrada.

Para liberar o acesso, foi adicionada a seguinte regra:

Configuração	Valor
Tipo	HTTP
Porta	80
Origem	0.0.0.0/0

Após salvar a regra e atualizar o navegador, foi possível visualizar a página com a mensagem:

Hello From Your Web Server!

Essa etapa demonstrou a importância das regras de entrada dos grupos de segurança para permitir o acesso às aplicações.

📈 Redimensionamento da instância

A instância foi interrompida para permitir a alteração do tipo de instância e do volume de armazenamento.

Recurso	Configuração inicial	Configuração final
Tipo de instância	t3.micro	t3.small
Volume raiz EBS	8 GiB	10 GiB

Após as alterações, a instância foi iniciada novamente.

Essa atividade demonstrou como ajustar os recursos computacionais e o armazenamento de acordo com as necessidades de uma aplicação.

🔐 Teste da proteção contra encerramento

Foi realizada uma tentativa de encerramento da instância enquanto a proteção estava habilitada. A operação foi bloqueada.

Em seguida, a proteção foi desabilitada e a instância foi encerrada conforme as instruções do laboratório.

Esse procedimento demonstrou como a proteção contra encerramento ajuda a evitar a exclusão acidental de instâncias.

📚 Principais aprendizados
Provisionamento de instâncias EC2.
Configuração de rede e grupos de segurança.
Automatização de tarefas com User Data.
Instalação e execução de um servidor web Apache.
Monitoramento de instâncias e verificações de status.
Gerenciamento de volumes Amazon EBS.
Redimensionamento de recursos computacionais.
Configuração de acesso HTTP.
Proteção contra encerramento acidental.
✅ Conclusão

O laboratório proporcionou uma experiência prática com o Amazon EC2, desde a criação e configuração da instância até a implantação de um servidor web, o monitoramento, o redimensionamento e o encerramento seguro.

A atividade contribuiu para consolidar conhecimentos fundamentais de computação em nuvem, administração de servidores e segurança na AWS.

🎓 Formação
Instituição: Escola da Nuvem
Formação: Formação em Nuvem com trilha AWS re/Start
Atividade: Laboratório Introdução ao Amazon EC2
Plataforma: Ambiente de laboratório AWS
Status: Concluído

Projeto desenvolvido para fins educacionais como parte da jornada de aprendizado em computação em nuvem.