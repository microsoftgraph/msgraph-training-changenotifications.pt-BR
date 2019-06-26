<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="e2d15-101">Neste exercício, você criará um novo registro de aplicativo Web do Azure AD usando o centro de administração do Azure Active Directory e concederá consentimento do administrador aos escopos de permissão necessários.</span><span class="sxs-lookup"><span data-stu-id="e2d15-101">In this exercise, you will create a new Azure AD web application registration using the Azure Active Directory admin center and grant administrator consent to the required permission scopes.</span></span>

1. <span data-ttu-id="e2d15-102">Abra um navegador e navegue até o [centro de administração do Azure Activehttps://aad.portal.azure.com)Directory (](https://aad.portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="e2d15-102">Open a browser and navigate to the [Azure Active Directory admin center (https://aad.portal.azure.com)](https://aad.portal.azure.com).</span></span> <span data-ttu-id="e2d15-103">Faça logon usando uma **conta corporativa ou de estudante**.</span><span class="sxs-lookup"><span data-stu-id="e2d15-103">Login using a **Work or School Account**.</span></span>

1. <span data-ttu-id="e2d15-104">Selecione **Azure Active Directory** na navegação à esquerda e, em seguida, selecione **registros de aplicativo** em **gerenciar**.</span><span class="sxs-lookup"><span data-stu-id="e2d15-104">Select **Azure Active Directory** in the left-hand navigation, then select **App registrations** under **Manage**.</span></span>

    ![Captura de tela dos registros de aplicativo](./images/aad-portal-home.png)

1. <span data-ttu-id="e2d15-106">Selecione **Novo registro**.</span><span class="sxs-lookup"><span data-stu-id="e2d15-106">Select **New registration**.</span></span> <span data-ttu-id="e2d15-107">Na página **registrar um aplicativo**</span><span class="sxs-lookup"><span data-stu-id="e2d15-107">On the **Register an application** page</span></span>

    ![Captura de tela da página de registro de aplicativos](./images/aad-portal-newapp.png)

    <span data-ttu-id="e2d15-109">Defina os valores da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e2d15-109">Set the values as follows:</span></span>

    - <span data-ttu-id="e2d15-110">**Nome**: GraphNotificationTutorial</span><span class="sxs-lookup"><span data-stu-id="e2d15-110">**Name**: GraphNotificationTutorial</span></span>
    - <span data-ttu-id="e2d15-111">**Tipos de conta com suporte**: contas em qualquer diretório organizacional e contas pessoais da Microsoft</span><span class="sxs-lookup"><span data-stu-id="e2d15-111">**Supported account types**: Accounts in any organizational directory and personal Microsoft accounts</span></span>
    - <span data-ttu-id="e2d15-112">**URI**de redirecionamento: Web >http://localhost</span><span class="sxs-lookup"><span data-stu-id="e2d15-112">**Redirect URI**: Web > http://localhost</span></span>

    ![Captura de tela da página registrar um aplicativo](./images/aad-portal-newapp-01.png)

    <span data-ttu-id="e2d15-114">Selecione **registrar**.</span><span class="sxs-lookup"><span data-stu-id="e2d15-114">Select **Register**.</span></span>

1. <span data-ttu-id="e2d15-115">Na página **GraphNotificationTutorial** , copie o valor da ID do **aplicativo (cliente)** e da **ID de diretório (locatário)** salve-o, você precisará deles na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="e2d15-115">On the **GraphNotificationTutorial** page, copy the value of the **Application (client) ID** and **Directory (tenant) ID** save it, you will need them in the next step.</span></span>

    ![Captura de tela da ID do aplicativo do novo registro de aplicativo](./images/aad-portal-newapp-details.png)

1. <span data-ttu-id="e2d15-117">Selecione **gerenciar > certificados & segredos**.</span><span class="sxs-lookup"><span data-stu-id="e2d15-117">Select **Manage > Certificates & secrets**.</span></span> 

    <span data-ttu-id="e2d15-118">Selecione **novo segredo do cliente**.</span><span class="sxs-lookup"><span data-stu-id="e2d15-118">Select **New client secret**.</span></span>

    <span data-ttu-id="e2d15-119">Insira um valor em **Descrição** e selecione uma das opções para **expirar** e selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="e2d15-119">Enter a value in **Description** and select one of the options for **Expires** and select **Add**.</span></span>

    ![Captura de tela da caixa de diálogo Adicionar um segredo do cliente](./images/aad-portal-newapp-secret.png)

    ![Captura de tela da caixa de diálogo Adicionar um segredo do cliente](./images/aad-portal-newapp-secret-02.png)

1. <span data-ttu-id="e2d15-122">Copie o valor secreto do cliente antes de sair desta página.</span><span class="sxs-lookup"><span data-stu-id="e2d15-122">Copy the client secret value before you leave this page.</span></span> <span data-ttu-id="e2d15-123">Você precisará dele na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="e2d15-123">You will need it in the next step.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="e2d15-124">Este segredo do cliente nunca é mostrado novamente, portanto, copie-o agora.</span><span class="sxs-lookup"><span data-stu-id="e2d15-124">This client secret is never shown again, so make sure you copy it now.</span></span>

    ![Captura de tela do novo segredo do cliente recém-adicionado](./images/aad-portal-newapp-secret-03.png)

1. <span data-ttu-id="e2d15-126">Selecione **gerenciar permissões de API de >**.</span><span class="sxs-lookup"><span data-stu-id="e2d15-126">Select **Manage > API Permissions**.</span></span>

    <span data-ttu-id="e2d15-127">Selecione **Adicionar uma permissão** e selecione **Microsoft Graph**.</span><span class="sxs-lookup"><span data-stu-id="e2d15-127">Select **Add a permission** and select **Microsoft Graph**.</span></span>

    ![Captura de tela selecionando o serviço do Microsoft Graph](./images/aad-portal-newapp-graphscope.png)

    <span data-ttu-id="e2d15-129">Selecione **permissão de aplicativo**, expanda o grupo de **usuários** e selecione o escopo **User. ReadWrite. All** .</span><span class="sxs-lookup"><span data-stu-id="e2d15-129">Select **Application Permission**, expand the **User** group and select **User.ReadWrite.All** scope.</span></span>

    <span data-ttu-id="e2d15-130">Selecione **adicionar permissões** para salvar suas alterações.</span><span class="sxs-lookup"><span data-stu-id="e2d15-130">Select **Add permissions** to save your changes.</span></span>

    ![Captura de tela selecionando o escopo do Microsoft Graph](./images/aad-portal-newapp-graphscope-02.png)

    ![Captura de tela do novo segredo do cliente recém-adicionado](./images/aad-portal-newapp-graphscope-03.png)

<span data-ttu-id="e2d15-133">O aplicativo solicita uma permissão de aplicativo com o escopo **User. ReadWrite. All** .</span><span class="sxs-lookup"><span data-stu-id="e2d15-133">The application requests an application permission with the **User.ReadWrite.All** scope.</span></span> <span data-ttu-id="e2d15-134">Essa permissão exige o consentimento administrativo.</span><span class="sxs-lookup"><span data-stu-id="e2d15-134">This permission requires administrative consent.</span></span>

<span data-ttu-id="e2d15-135">Selecione **conceder consentimento do administrador para contoso**e, em seguida, selecione **Sim** para concordar com este aplicativo e conceder o acesso do aplicativo ao locatário usando os escopos especificados.</span><span class="sxs-lookup"><span data-stu-id="e2d15-135">Select **Grant admin consent for Contoso**, then select **Yes** to consent this application and grant the application access to your tenant using the scopes you specified.</span></span>

![Captura de tela aprovado pelo consentimento do administrador](./images/aad-portal-newapp-graphscope-04.png)
