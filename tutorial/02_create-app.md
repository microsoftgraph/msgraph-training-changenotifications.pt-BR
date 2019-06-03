<!-- markdownlint-disable MD002 MD041 -->

Neste exercício, você criará um novo registro de aplicativo Web do Azure AD usando o centro de administração do Azure Active Directory e concederá consentimento do administrador aos escopos de permissão necessários.

1. Abra um navegador e navegue até o [centro de administração do Azure Active Directory](https://portal.azure.com). Faça logon usando uma **conta corporativa ou de estudante**.

1. Selecione **Azure Active Directory** na navegação à esquerda e, em seguida, selecione **Registros do aplicativo (Visualizar)** sob **Gerenciar**.

    ![Uma captura de tela dos registros de aplicativo ](./images/01.png)

1. Selecione **Novo registro**. Na página **Registrar um aplicativo**, defina os valores da seguinte forma.

    - Defina **Nome** para `GraphNotificationTutorial`.
    - Defina **Tipos de conta com suporte** para **Contas em qualquer diretório organizacional e contas pessoais da Microsoft**.
    - Em **URI de Redirecionamento**, defina o primeiro menu suspenso para `Web` e defina o valor como `http://localhost`.

    ![Uma captura de tela da página registrar um aplicativo](./images/02.png)

1. Selecione **registrar**. Na página **GraphNotificationTutorial** , copie o valor da ID do **aplicativo (cliente)** e da **ID de diretório (locatário)** salve-o, você precisará deles na próxima etapa.

    ![Uma captura de tela da ID do aplicativo do novo registro de aplicativo](./images/03.png)

1. Selecione **Certificados e segredos** sob **Gerenciar**. Selecione **novo segredo do cliente**. Insira um valor em **Descrição** e selecione uma das opções para **expirar** e selecione **Adicionar**.

    ![Uma captura de tela da caixa de diálogo Adicionar um segredo do cliente](./images/04.png)

1. Copie o valor secreto do cliente antes de sair desta página. Você precisará dele na próxima etapa.

    > [!IMPORTANT]
    > Este segredo do cliente nunca é mostrado novamente, portanto, copie-o agora.

    ![Uma captura de tela do novo segredo do cliente recentemente adicionado](./images/05.png)

1. Selecione **permissões de API** em **gerenciar**. **Adicione uma permissão** e selecione **Microsoft Graph**. Selecione **permissão de aplicativo** e expanda **usuário** e selecione o escopo **User. ReadWrite. All** . Selecione **adicionar permissões** para salvar suas alterações.

    ![Uma captura de tela do novo segredo do cliente recentemente adicionado](./images/06.png)

O aplicativo solicita uma permissão de aplicativo com o escopo **User. ReadWrite. All** . Essa permissão exige o consentimento administrativo.

Selecione **conceder consentimento do administrador para contoso** e, em seguida, selecione **Sim** para concordar com este aplicativo e conceder o acesso do aplicativo ao locatário usando os escopos especificados.

![Captura de tela de entrada](./images/07.png)
