<!-- markdownlint-disable MD002 MD041 -->

Neste exercício, você criará um novo registro de aplicativo Web do Azure AD usando o centro de administração do Azure Active Directory e concederá consentimento do administrador aos escopos de permissão necessários.

1. Abra um navegador e navegue até o [centro de administração do Azure Activehttps://aad.portal.azure.com)Directory (](https://aad.portal.azure.com). Faça logon usando uma **conta corporativa ou de estudante**.

1. Selecione **Azure Active Directory** na navegação à esquerda e, em seguida, selecione **registros de aplicativo** em **gerenciar**.

    ![Captura de tela dos registros de aplicativo](./images/aad-portal-home.png)

1. Selecione **Novo registro**. Na página **registrar um aplicativo**

    ![Captura de tela da página de registro de aplicativos](./images/aad-portal-newapp.png)

    Defina os valores da seguinte maneira:

    - **Nome**: GraphNotificationTutorial
    - **Tipos de conta com suporte**: contas em qualquer diretório organizacional e contas pessoais da Microsoft
    - **URI**de redirecionamento: Web >http://localhost

    ![Captura de tela da página registrar um aplicativo](./images/aad-portal-newapp-01.png)

    Selecione **registrar**.

1. Na página **GraphNotificationTutorial** , copie o valor da ID do **aplicativo (cliente)** e da **ID de diretório (locatário)** salve-o, você precisará deles na próxima etapa.

    ![Captura de tela da ID do aplicativo do novo registro de aplicativo](./images/aad-portal-newapp-details.png)

1. Selecione **gerenciar > certificados & segredos**. 

    Selecione **novo segredo do cliente**.

    Insira um valor em **Descrição** e selecione uma das opções para **expirar** e selecione **Adicionar**.

    ![Captura de tela da caixa de diálogo Adicionar um segredo do cliente](./images/aad-portal-newapp-secret.png)

    ![Captura de tela da caixa de diálogo Adicionar um segredo do cliente](./images/aad-portal-newapp-secret-02.png)

1. Copie o valor secreto do cliente antes de sair desta página. Você precisará dele na próxima etapa.

    > [!IMPORTANT]
    > Este segredo do cliente nunca é mostrado novamente, portanto, copie-o agora.

    ![Captura de tela do novo segredo do cliente recém-adicionado](./images/aad-portal-newapp-secret-03.png)

1. Selecione **gerenciar permissões de API de >**.

    Selecione **Adicionar uma permissão** e selecione **Microsoft Graph**.

    ![Captura de tela selecionando o serviço do Microsoft Graph](./images/aad-portal-newapp-graphscope.png)

    Selecione **permissão de aplicativo**, expanda o grupo de **usuários** e selecione o escopo **User. ReadWrite. All** .

    Selecione **adicionar permissões** para salvar suas alterações.

    ![Captura de tela selecionando o escopo do Microsoft Graph](./images/aad-portal-newapp-graphscope-02.png)

    ![Captura de tela do novo segredo do cliente recém-adicionado](./images/aad-portal-newapp-graphscope-03.png)

O aplicativo solicita uma permissão de aplicativo com o escopo **User. ReadWrite. All** . Essa permissão exige o consentimento administrativo.

Selecione **conceder consentimento do administrador para contoso**e, em seguida, selecione **Sim** para concordar com este aplicativo e conceder o acesso do aplicativo ao locatário usando os escopos especificados.

![Captura de tela aprovado pelo consentimento do administrador](./images/aad-portal-newapp-graphscope-04.png)
