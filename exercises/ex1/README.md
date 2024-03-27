# Exercício 1 – Tipos de sistema no serviço Identity Provisioning

Neste exercício, aprenderemos sobre os diferentes tipos de sistemas no Identity Provisioning e configuraremos um sistema de origem.

O serviço Identity Provisioning garante a sincronização das entidades entre um sistema de origem e um ou vários sistemas de destino.

**Sistemas Fonte**

Um sistema de origem é o conector usado para leitura de entidades (usuários, grupos, funções). Os sistemas de origem podem ser locais ou baseados em nuvem, SAP ou não SAP, e geralmente representam o armazenamento de usuários corporativos onde as identidades são mantidas atualmente. O Provisionamento de Identidade lê as entidades do sistema de origem e as cria ou atualiza nas entidades de destino relevantes. O provisionamento é acionado na guia Jobs de um sistema de origem.

Você pode conectar um sistema de origem a um ou vários sistemas de destino.

<img src="/exercises/ex1/images/sourcesys.png" width=50% height=50% >

*Sistemas Alvos**

Um sistema de destino é o conector usado para escrever (provisionar) entidades. Os sistemas de destino geralmente são baseados em nuvem, onde o Identity Provisioning cria ou atualiza as entidades retiradas do sistema de origem.

Um sistema de destino pode ser conectado a um único ou a vários sistemas de origem.

**Sistemas Proxy**

Um sistema proxy é um conector especial usado para cenários “híbridos”. Ele expõe qualquer sistema back-end compatível com Provisionamento de Identidade como um provedor de serviços SCIM 2.0, que pode ser consumido por qualquer aplicativo cliente compatível com SCIM 2.0, sem fazer uma conexão direta entre eles.

<img src="/exercises/ex1/images/proxy.png" width=50% height=50% >

Você pode encontrar mais informações sobre isso em nossa página de produto em [Tipos de sistema](https://help.sap.com/docs/identity-provisioning/identity-provisioning/system-types?locale=en-US).

O serviço Identity Provisioning oferece suporte ao provisionamento de usuários e grupos entre vários sistemas na nuvem e locais, tanto SAP quanto não SAP. A lista completa pode ser encontrada em [Sistemas Suportados](https://help.sap.com/docs/identity-provisioning/identity-provisioning/supported-systems?locale=en-US)


## Exercício 1.1 Criando um sistema fonte em IPS

1. Navegue até o menu Provisionamento de Identidade no console administrativo:

<img src="/exercises/ex1/images/12.png">

2. Escolha **Sistemas Fonte** na lista suspensa

<img src="/exercises/ex1/images/11.png">
 
3. Para adicionar um novo Sistema Fonte, pressione **+Adicionar**

<img src="/exercises/ex1/images/13.png">
   
4. Procure o conector **SAP SuccessFactors** **Tipo**

<img src="/exercises/ex1/images/14.png">
   
5. Escolha um nome e uma descrição significativos, como **SAP SFSF** e **meu sistema de origem** para seu sistema. **Não salve ainda o sistema.**

<img src="/exercises/ex1/images/15.png">
   
6. Navegue até a terceira aba chamada **Propriedades**, pressione o botão **Adicionar** e escolha **Padrão**

<img src="/exercises/ex1/images/16.png">

7. Para **Nome** escolha _sf.api.version_ e para **Valor** escreva _2_

<img src="/exercises/ex1/images/17.png">
     
8. Quando terminar, pressione **Salvar**

  <img src="/exercises/ex1/images/18.png">

9. Seu sistema salvo deve ficar assim:
    
<img src="/exercises/ex1/images/19.png">

10. Depois de criar o sistema de origem, continue adicionando o restante das propriedades necessárias:
As propriedades a seguir são do tipo **Padrão**

| Name         |Value | 
|--------------|:-----:|
| Authentication|BasicAuthentication|        
| ProxyType|Internet|     
| Type|HTTP|   
|URL |https://apisalesdemo2.successfactors.eu/|   
|User | **Ask your supervisor**|  

The following property is of type **Credential**
| Name         |Value | 
|--------------|:-----:|
|Password | **Ask your supervisor**|   

11. Modifique a seguinte propriedade

| Name         |Value | 
|--------------|:-----:|
|ips.trace.failed.entity.content |true|  

Se um trabalho de provisionamento falhar repetidamente e você precisar de investigação do problema, poderá ativar o registro em log e o rastreamento dos dados pessoais e confidenciais de suas entidades provisionadas.
Para fazer isso, defina esta propriedade como verdadeira. Se a propriedade não estiver definida, nos logs você verá: conteúdo = conteúdo oculto.

12. Verifique se suas propriedades são semelhantes à captura de tela abaixo e pressione **Salvar**.

<img src="/exercises/ex1/images/111.png">


## Resumo

Agora você criou um sistema de origem para sua instância do SAP SuccessFactors.

Continue para o [Exercício 2 - Adicionando um sistema de destino](../ex2/README.md) para criar um sistema de destino.
