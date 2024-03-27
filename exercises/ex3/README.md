# Exercício 3 – Tipos de trabalho de provisionamento de identidade

Neste exercício, você aprenderá sobre as diversas operações disponíveis no serviço de provisionamento de identidade e examinaremos detalhadamente os vários tipos de trabalho de provisionamento disponíveis.


## Exercício 3.1 Tipos de trabalho
Você pode iniciar e interromper um trabalho de provisionamento na interface do usuário (IU) do Provisionamento de Identidade ou em um cliente de API usando a API de administração de locatário do Provisionamento de Identidade.

O serviço Provisionamento de Identidade fornece os seguintes tipos de trabalhos de provisionamento:

**Leia o trabalho**
Lê todas as entidades do sistema de origem e provisiona apenas entidades novas ou atualizadas no sistema de destino. Se o trabalho for executado no modo de leitura delta, ele lê e provisiona/exclui apenas entidades novas ou atualizadas no sistema de origem.

**Trabalho de ressincronização**
Lê todas as entidades do sistema de origem e provisiona todas as entidades para o sistema de destino.

**Simular trabalho**
Estima o número de entidades que serão criadas, atualizadas, excluídas ou ignoradas no sistema de destino. Fornece os resultados esperados de uma tarefa de ressincronização sem modificar o sistema de destino.

**Validar trabalho**
Verifica como as entidades (usuários e grupos) seriam mapeadas dos sistemas de origem para os sistemas de destino sem modificá-los.

Se você quiser saber mais sobre isso, dê uma olhada em nossa página de produto em [Iniciar e parar trabalhos de provisionamento](https://help.sap.com/docs/identity-provisioning/identity-provisioning/start-and-stop -provisioning-jobs?locale=en-US&version=Cloud).


## Exercício 3.2 O trabalho Validar

Conforme mencionado anteriormente, para entender como o IPS realiza o mapeamento entre o sistema de origem e de destino, você pode aproveitar o trabalho **Validate**.
Assim como a tarefa de simulação, a tarefa de validação prevê resultados no sistema de destino sem modificá-lo. Porém, diferentemente do trabalho de simulação (que estima o número de entidades que serão criadas, atualizadas, excluídas ou ignoradas), o trabalho de validação verifica o conteúdo das entidades.

Para executar um trabalho de validação, você precisa importar um ou dois arquivos CSV - um para usuários e/ou outro para grupos. Cada arquivo deve conter no máximo 10 usuários ou grupos com atributos definidos no sistema de origem. Os nomes dos atributos devem usar a notação de ponto JSONPath. Por exemplo: atributo `emails[0].value` indicando o valor do primeiro e-mail dentro de uma matriz `emails`, ou `name.familyName` - um atributo de nome complexo contendo um subatributo `familyName`. Se o arquivo tiver mais de 10 usuários ou grupos, o trabalho validará os 10 primeiros e ignorará o restante.

Você pode criar um arquivo CSV usando um editor de texto, por exemplo o Bloco de Notas. Certifique-se de que o número de campos corresponda ao número de cabeçalhos no arquivo. Caso contrário, você receberá um erro ao importar o arquivo e não poderá prosseguir até corrigi-lo.

Para este exercício, você usará apenas um arquivo CSV de usuários criado para você. 

1. [Baixe](/exercises/ex3/Users_SAPSFSF.csv) o arquivo CSV preparado para usuários anexado a este exercício. O arquivo é chamado **Users_SAPSFSF.csv**

2. Navegue até o console administrativo do SCI que corresponde ao seu assento. No terceiro menu **Provisionamento de identidade** escolha **Sistemas de origem**

<img src="/exercises/ex3/images/32.png">

3. Escolha o sistema de origem criado no Exercício 1 **SAP SFSF**

4. Uma vez no sistema correto, navegue até a quinta guia chamada **Trabalhos**

<img src="/exercises/ex3/images/34.png">

5. Escolha o último Job chamado **Validate** e pressione **Run Now**. Escolher Executar agora, entretanto, não aciona o trabalho literalmente. Apenas abre uma caixa de diálogo onde você deve importar arquivos CSV (valores separados por vírgula)

<img src="/exercises/ex3/images/35.png">

6. Na caixa de diálogo Importar usuários, procure e selecione o arquivo CSV que você baixou anteriormente para testar usuários

7. Pressione **Validar**

<img src="/exercises/ex3/images/37.png">

9. Seu navegador exibiu um pop-up informando que os resultados do trabalho de validação foram baixados. Navegue até esta pasta localmente no seu computador e verifique os resultados

<img src="/exercises/ex3/images/39.png">

## Exercício 3.3 O trabalho de leitura

1. Na seção Jobs do sistema de origem, escolha **Read Job** e pressione **Run Now**
   
<img src="/exercises/ex3/images/331.png">

2. Navegue até o menu **Logs de provisionamento** na guia **Provisionamento de identidade**

<img src="/exercises/ex3/images/332.png">
   
3. O trabalho foi concluído com erro. Pressione o resultado para ver os detalhes

<img src="/exercises/ex3/images/333.png">

4. Como você percebeu, apenas um subconjunto de usuários e grupos do SAP SFSF foi provisionado. Ao expandir o log de erros, você entende o porquê: `Valor desconhecido 'SMB' para o atributo 'urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department`
O atributo `departamento` é um atributo de referência que pode ter valores fixos no IdDS.

<img src="/exercises/ex3/images/334.png" >

5. Para exibir todos os logs de erros, você pode pressionar **Baixar todos os logs de erros deste trabalho**

<img src="/exercises/ex3/images/335.png" >

Depois de fazer o download, você pode procurar o usuário com o Displayname _HR Coordinator_ e perceber que o problema também era o valor `departamento`. Os próximos exercícios explicarão como corrigir tais erros.

## Resumo
Após concluir essas etapas você conheceu os diversos tipos de trabalhos disponíveis no IPS e já testou dois deles. Vamos tentar alterar a transformação padrão e corrigir o erro dos logs no próximo exercício.
Continue para - [Exercício 4 - Operações de provisionamento de identidade](../ex4/README.md)
