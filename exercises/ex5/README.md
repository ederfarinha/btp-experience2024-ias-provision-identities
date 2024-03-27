# Exercício 5 - Operações avançadas de provisionamento de identidade

## Exercício 5.1 Condições de edição

1. Vamos continuar alterando a transformação padrão editando uma condição no sistema de origem. No console de administração do SCI, navegue até a terceira guia **Provisionamento de identidade** e escolha **Sistemas de origem**.
   
2. Escolha o sistema de origem **SAP SFSF** e navegue até a segunda aba **Transformações**.
   
3. Pressione o botão **Editar** no lado direito do menu.

4. Escolha Editar entidade -> usuário -> Adicionar condição.
   
<img src="/exercises/ex5/images/511.png">

6. No pop-up copie as condições abaixo e pressione **Salvar**.

```
isValidEmail($.emails[0].value) && $.emails[0].value =~ /.*@successfactors.de/
```
<img src="/exercises/ex5/images/521.png">

Esta condição garante que apenas usuários com um endereço de e-mail válido sejam lidos no sistema de origem. Além disso, o trabalho irá filtrar apenas usuários com endereços de e-mail pertencentes a domínios específicos, neste caso queremos filtrar apenas usuários que pertencem a um domínio _SuccessFactors_.

## Exercício 5.2 Conheça o trabalho Simular

1. Navegue agora até **Jobs**, a última aba deste sistema de origem
   
2. Escolha **Simular trabalho** e pressione **Executar agora**

<img src="/exercises/ex5/images/522.png">
   
3. Navegue até **Logs de provisionamento** (no menu suspenso Provisionamento de identidade) e observe o resultado do trabalho
   
4. Nesta fase muitos usuários seriam excluídos
<img src="/exercises/ex5/images/523.png">

6. Você pode verificar mais informações sobre a execução deste trabalho. Como esses usuários são ignorados porque não atendem aos critérios de filtragem, pressione **Baixar todos os logs de entidades ignorados para este trabalho** no canto superior direito:

<img src="/exercises/ex5/images/526.png">

7. No arquivo baixado você verá a seguinte mensagem:
   
<img src="/exercises/ex5/images/524.png">

No próximo exercício você aprenderá como usar propriedades.

## Exercício 5.3 Trabalhando com Propriedades

Você já usou propriedades para configurar a conexão entre os sistemas de origem e de destino no primeiro exercício. No entanto, este não é o único benefício que se obtém deles. As propriedades ajudam você a personalizar a maneira como suas identidades são lidas em um sistema de origem ou provisionadas no sistema de destino. Eles também podem filtrar as entidades e atributos que devem ser lidos ou ignorados durante o trabalho de provisionamento.

1. Continuemos com a configuração do exercício anterior. Navegue até o sistema de origem **SAP SFSF** e acesse a aba **Propriedades**. Adicione as duas propriedades **Padrão** a seguir:

| Name         |Value | 
|--------------|:-----:|
|ips.trace.skipped.entity |true|  
|ips.trace.skipped.entity.content |true|  

O resultado deve ficar assim:

<img src="/exercises/ex5/images/531.png">

Pressione **Salvar**.

2. Navegue até o sistema de destino **Diretório de identidade local** e vá para a guia **Propriedades**

3. Modifique a seguinte propriedade

| Name         |Value | 
|--------------|:-----:|
|ips.trace.failed.entity.content |true|  


Se um trabalho de provisionamento falhar repetidamente e você precisar de investigação do problema, poderá ativar o registro em log e o rastreamento dos dados pessoais e confidenciais de suas entidades provisionadas. Para fazer isso, defina esta propriedade como verdadeira.

Se a propriedade não estiver definida, nos logs você verá: conteúdo = conteúdo oculto


4. Vamos executar o trabalho Simulate mais uma vez para ver o resultado de nossas alterações. Para isso navegaremos de volta aos nossos sistemas de origem e iremos para a última aba **Jobs**. Escolha **Simular trabalho** e pressione **Executar agora**
   
5. Navegue até **Logs de provisionamento** (no menu suspenso Provisionamento de identidade), observe o resultado do trabalho e baixe o arquivo de entidades ignoradas.
   
<img src="/exercises/ex5/images/534.png">

Agora você pode perceber que o domínio utilizado na condição estava errado e portanto todos os usuários terão sido deletados, inclusive os pertencentes a _*@successfactors.com_. Isso será corrigido no próximo exercício.

6. Retorne ao sistema de origem **SAP SFSF** e navegue até a segunda aba **Transformações**. Pressione o botão **Editar** no lado direito do menu. Escolha Editar entidade -> usuário -> Editar condição. Corrija a condição existente conforme ilustrado abaixo: 
   
```
isValidEmail($.emails[0].value) && $.emails[0].value =~ /.*@successfactors.com/ 
```
O resultado deve ficar assim:

<img src="/exercises/ex5/images/536.png">

7. Pressione **Salvar**.
   
8. Agora que você corrigiu o domínio, simule o trabalho uma última vez. Navegue até a última guia **Trabalhos**. Escolha **Simular trabalho** e pressione **Executar agora**
   
9. Como esperado, nem todas as entidades lidas serão excluídas. Após verificar os logs, você notará que não há mais usuários com o domínio _*@successfactors.com_ ignorado. Os usuários que seriam excluídos são aqueles pertencentes a outros domínios.

<img src="/exercises/ex5/images/539.png">
    
10. Navegue até o sistema de origem **SAP SFSF*, escolha a última aba **Jobs** e desta vez escolha **Read Job** e pressione **Run Now**
    
11. Navegue até **Logs de provisionamento** (no menu suspenso Provisionamento de identidade) e observe o resultado do trabalho.

<img src="/exercises/ex5/images/5311.png">

A quantidade esperada de usuários foi excluída.

Estas são apenas algumas das muitas propriedades que você pode usar no IPS. Todas as propriedades disponíveis do serviço Identity Provisioning podem ser encontradas em nossa página de produto em [Lista de propriedades](https://help.sap.com/docs/identity-provisioning/identity-provisioning/list-of-properties?locale =en-US&version=Cloud).

Por exemplo, caso se queira limitar o número de usuários excluídos no sistema alvo, a propriedade `ips.delete.threshold.users` pode ser usada. Se mais usuários do que o valor da propriedade forem excluídos, a execução do trabalho apresentará erros, impedindo a exclusão real.

## Resumo
Nesta sessão prática você aprendeu o que são os serviços SAP Cloud Identity e como configurar e solucionar problemas de sistemas no serviço Identity Provisioning. 
