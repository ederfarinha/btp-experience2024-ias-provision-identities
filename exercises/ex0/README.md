# Getting started

Antes de iniciar os exercícios, vamos relembrar um pouco o que são os serviços SAP Cloud Identity.

   
<img align="right" width="650" src="/exercises/ex0/images/SCI.png" />

O SAP Cloud Identity Services (SCI) é a ferramenta padrão para autenticar e provisionar usuários em soluções em nuvem da SAP:
* Autenticação de identidade (IAS)
* Provisionamento de identidade (IPS)
* Gerenciamento de autorização (AMS)
* Integrado através do diretório de identidade comum (IdDS)

O número de **soluções SAP pré-integradas** que exigem **SAP Cloud Identity Services** aumentará.
Não há necessidade de licenciar separadamente o uso de nossos serviços, quando usados com soluções em nuvem SAP.
**Por padrão**, oferecemos **dois locatários SCI**:
* Teste
* Produção

**O que é autenticação de identidade?**
O serviço de autenticação de identidade fornece acesso controlado baseado em nuvem a processos de negócios, aplicativos e dados. Ele simplifica a experiência do usuário por meio de mecanismos de autenticação, logon único, integração local e opções convenientes de autoatendimento.

**O que é provisionamento de identidade?**
O serviço Identity Provisioning automatiza os processos do ciclo de vida da identidade. Ele ajuda você a provisionar identidades e suas autorizações para vários aplicativos de negócios locais e na nuvem.

**O que é gerenciamento de autorização?**
O gerenciamento de autorizações fornece um gerenciamento centralizado de autorizações de usuários finais para aplicativos de negócios baseados na plataforma tecnológica SAP BTP. O AMS é baseado no Identity Directory existente do SAP Cloud Identity Services e permite que os clientes gerenciem atribuições de políticas a usuários com base na API SCIM do Identity Directory.

**O que é o Diretório de Identidade?**
O Identity Directory é o componente central para usuários e grupos persistentes dentro dos SAP Cloud Identity Services.
O uso do Identity Directory simplifica a forma como os clientes se conectam aos nossos aplicativos SAP SaaS, usando-o como um ponto central de verdade para o ambiente de nuvem SAP.
Além da IU do console administrativo do SAP Cloud Identity Services, uma API SCIM 2.0 permite acessar programaticamente as identidades dentro do diretório.

Para obter mais informações sobre esses serviços, explore nossa documentação [SAP Cloud Identity Services](https://help.sap.com/docs/cloud-identity), bem como nossa [coleção de API](https://api.sap.com/package/SCPIdentityServices/rest) publicado no hub SAP API Business Accelerator . Todos os serviços podem interagir visualmente a partir do console de administração do SAP Cloud Identity Services.

## Cenário prático
Para entender melhor a funcionalidade de provisionamento disponível no SAP Cloud Identity Service, passaremos juntos pelos próximos exercícios. O cenário é escolhido de forma a assemelhar-se, ainda que em pequena escala, ao ciclo de vida da identidade numa paisagem. Começaremos conectando uma origem de usuário ao Provisionamento de Identidade. Para isso, utilizaremos um sistema SAP SuccessFactors. Posteriormente, configuraremos um sistema alvo - o Diretório de Identidades. Analisaremos os diferentes tipos de trabalho e aprenderemos como alterar as transformações IPS padrão e como validar seu comportamento.

## Acessando o locatário do SAP Cloud Identity Services

Agora que sabemos o que são os SAP Cloud Services e entendemos qual é o escopo desta sessão prática, vamos verificar o acesso ao sistema. Para esta sessão, você precisará de acesso a um locatário do SAP Cloud Identity Service (SCI) e a uma instância do SAP SuccessFactors.

1. Procure o navegador da Internet em seu computador e navegue até o console administrativo do SCI.  

URL: https://aruagcnbn.accounts.ondemand.com/admin    


<i>Usuário e senha serão fornecidos na sala do evento!</i>

2. Digite o nome de usuário e a senha e pressione **Log On**

   <img src="/exercises/ex0/images/02.png" width=50% height=50%>

3. Você tem acesso ao console administrativo do SAP Cloud Identity Services.
   
   <img src="/exercises/ex0/images/01.png" width=50% height=50%>
   

   



## Summary

Agora que você efetuou login em seu console SCI, continue para - [Exercise 1 - Exercise 1 Description](../ex1/README.md)
