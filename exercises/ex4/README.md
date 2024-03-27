# Exercício 4 - Operações de provisionamento de identidade

Neste exercício, você conhecerá as diversas operações disponíveis no serviço Identity Provisioning. Começaremos entendendo o que são transformações.

**Transformações**
Para cada sistema suportado pelo serviço Identity Provisioning, há uma lógica de transformação inicial (padrão) que converte a representação específica do sistema das entidades de/para um JSON comum. Essa transformação padrão fica visível na aba Transformações quando você cria um novo sistema, após salvá-lo.

**Editores de Transformação**
O serviço Identity Provisioning fornece dois editores para trabalhar com o código de transformação: editor gráfico e editor JSON (código). O editor gráfico é exibido por padrão. Você pode alternar entre eles na guia Transformações, como verá no próximo exercício.
Consulte o capítulo [Transformações](https://help.sap.com/docs/identity-provisioning/identity-provisioning/transformations?locale=en-US) para mais explicações e exemplos.

## Exercício 4.1 Conheça o editor gráfico

No exercício anterior, ocorreu um erro no último trabalho executado. Neste caso, o motivo foi que o valor do departamento no sistema de origem não corresponde a um dos valores possíveis no sistema de destino. O objetivo deste exercício é entender como utilizar o editor gráfico, portanto você realizará um mapeamento entre os possíveis valores do atributo `department`.

1. No console de administração do SCI, navegue até a terceira guia **Provisionamento de identidade** e escolha Sistemas de destino. Você deseja executar o mapeamento de valores no sistema de destino porque esses valores são específicos do sistema de destino do Identity Directory.
No sistema de destino **Local Identity Directory** que criamos no Exercício 2, navegue até a segunda guia **Transformações**

<img src="/exercises/ex4/images/41.png">

2. Observe os botões no canto superior direito da aba do editor. A partir daqui você pode alternar entre os dois editores. Pressione o botão **Editar** e siga os próximos passos

<img src="/exercises/ex4/images/42.png">

3. A primeira entidade é o **Usuário**. Role para baixo até o atributo `departamento` e pressione o ícone **Lápis** para editar o mapeamento

<img src="/exercises/ex4/images/43.png">

4. Na parte inferior da janela pop-up, pressione **Adicionar** para adicionar o par nome-valor para a expressão especificada

<img src="/exercises/ex4/images/44.png">

5. Em Nome, escolha **tipo**

<img src="/exercises/ex4/images/45.png">

6. Em Valor, escolha **valueMapping** e depois **Salvar**

<img src="/exercises/ex4/images/46.png">

7. Para **Adicionar um mapeamento de valor** escolha o quinto botão de cima para baixo conforme exibido abaixo
   
<img src="/exercises/ex4/images/47.png">

8. Pressione **Adicionar** para inserir os novos valores no passo 9

<img src="/exercises/ex4/images/48.png">

9. Na coluna da esquerda teremos os valores do sistema de origem SAP SuccessFactors e na coluna da direita os do Identity Directory local. Adicione os valores conforme mostrado abaixo e pressione **Salvar**
 
<img src="/exercises/ex4/images/49.png">

10. Você verá as alterações também no editor JSON. Basta mudar a visualização e procurar as linhas 155 a 175

<img src="/exercises/ex4/images/410.png">

11. Execute o trabalho novamente. Navegue até o sistema de origem e escolha o sistema de origem **SAP SFSF**. Pressione na última aba **Jobs** e escolha **Run Now** para **Read Job**

<img src="/exercises/ex4/images/411.png">

12. Navegue até **Logs de provisionamento** (no menu suspenso Provisionamento de identidade) e observe como o trabalho foi bem-sucedido.
    
<img src="/exercises/ex4/images/412.png">

13. Pressione o resultado do trabalho e inspecione o que mudou agora

<img src="/exercises/ex4/images/413.png">

14. Dê uma olhada no registro do usuário. No console de administração do SCI, navegue até a segunda guia **Gerenciamento de usuários**

<img src="/exercises/ex4/images/414.png">

15. Você pode procurar pelo usuário “HR” pois este era um dos usuários que tinha como valor `departamento` `SMB` no SAP SFSF - e isso causou um erro anteriormente. Escolha este usuário e vamos rolar até o atributo `departamento`

<img src="/exercises/ex4/images/415.png">

16. Como esperado, a mudança na transformação do mapeamento funcionou

<img src="/exercises/ex4/images/416.png">


## Resumo
Depois de concluir essas etapas você aprendeu o que são as transformações e como elas podem ser alteradas. Você editou o mapeamento de valores do atributo `department` e testou os resultados de nossas alterações. Junte-se a nós no próximo exercício para aprender mais recursos interessantes do IPS [Exercício 5 – Operações avançadas de provisionamento de identidade](../ex5/README.md)
