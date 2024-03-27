# Exercício 2 – Adicionando um sistema de destino

Neste exercício, você criará um sistema de destino para o sistema de origem criado no exercício anterior.

## Exercício 2.1 Definindo o Diretório de Identidades como um sistema de destino

Como aprendemos no capítulo [Introdução](../ex0/README.md), cada locatário do SAP SCI inclui um diretório de identidade (IdDS) que armazena usuários, grupos e atribuições de grupo. Neste exercício você configurará o IdDS como alvo de provisionamento.

1. Navegue até o console administrativo do SCI que corresponde ao seu assento. Na terceira guia **Provisionamento de identidade** escolha **Sistemas de destino**

<img src="/exercises/ex2/images/21.png" largura=50% altura=50%>

2. Para adicionar um novo sistema de destino, pressione **+Adicionar**

<img src="/exercises/ex2/images/22.png" largura=50% altura=50%>
   
3. Procure o conector **Diretório de Identidade Local** **Tipo**

<img src="/exercises/ex2/images/23.png" largura=50% altura=50%>

4. Escolha um nome e uma descrição significativos, como **Diretório de identidade local** e **meu diretório de identidade local** para seu sistema. Informamos que o nome do sistema não pode ser alterado depois que o sistema for salvo
   
5. Em **Sistemas Fonte** você precisa escolher o sistema fonte que foi criado no exercício anterior

<img src="/exercises/ex2/images/25.png" largura=50% altura=50%>

6. **Salve** seu sistema. Agora seu sistema de destino foi criado e deve ficar assim:

<img src="/exercises/ex2/images/24.png" largura=50% altura=50%>

Como os usuários e grupos serão provisionados no diretório de identidade do seu locatário atual do SAP Cloud Identity Services, você não precisa configurar propriedades de conectividade e autenticação para o sistema de destino.


## Resumo

Agora você definiu os IdDs do seu locatário SCI como um sistema de provisionamento de destino para o seu cenário.

Continue para - [Exercício 3 - Tipos de trabalho de provisionamento de identidade](../ex3/README.md)
