<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="53ab2-101">Neste exercício, você criará um novo registro de aplicativo Web do Azure AD usando o centro de administração do Azure Active Directory e concederá consentimento do administrador aos escopos de permissão necessários.</span><span class="sxs-lookup"><span data-stu-id="53ab2-101">In this exercise, you will create a new Azure AD web application registration using the Azure Active Directory admin center and grant administrator consent to the required permission scopes.</span></span>

1. <span data-ttu-id="53ab2-102">Abra um navegador e navegue até o [centro de administração do Azure Active Directory](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="53ab2-102">Open a browser and navigate to the [Azure Active Directory admin center](https://portal.azure.com).</span></span> <span data-ttu-id="53ab2-103">Faça logon usando uma **conta corporativa ou de estudante**.</span><span class="sxs-lookup"><span data-stu-id="53ab2-103">Login using a **Work or School Account**.</span></span>

1. <span data-ttu-id="53ab2-104">Selecione **Azure Active Directory** na navegação à esquerda e, em seguida, selecione **Registros do aplicativo (Visualizar)** sob **Gerenciar**.</span><span class="sxs-lookup"><span data-stu-id="53ab2-104">Select **Azure Active Directory** in the left-hand navigation, then select **App registrations (Preview)** under **Manage**.</span></span>

    ![<span data-ttu-id="53ab2-105">Uma captura de tela dos registros de aplicativo</span><span class="sxs-lookup"><span data-stu-id="53ab2-105">A screenshot of the App registrations</span></span> ](./images/01.png)

1. <span data-ttu-id="53ab2-106">Selecione **Novo registro**.</span><span class="sxs-lookup"><span data-stu-id="53ab2-106">Select **New registration**.</span></span> <span data-ttu-id="53ab2-107">Na página **Registrar um aplicativo**, defina os valores da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="53ab2-107">On the **Register an application** page, set the values as follows.</span></span>

    - <span data-ttu-id="53ab2-108">Defina **Nome** para `GraphNotificationTutorial`.</span><span class="sxs-lookup"><span data-stu-id="53ab2-108">Set **Name** to `GraphNotificationTutorial`.</span></span>
    - <span data-ttu-id="53ab2-109">Defina **Tipos de conta com suporte** para **Contas em qualquer diretório organizacional e contas pessoais da Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="53ab2-109">Set **Supported account types** to **Accounts in any organizational directory and personal Microsoft accounts**.</span></span>
    - <span data-ttu-id="53ab2-110">Em **URI de Redirecionamento**, defina o primeiro menu suspenso para `Web` e defina o valor como `http://localhost`.</span><span class="sxs-lookup"><span data-stu-id="53ab2-110">Under **Redirect URI**, set the first drop-down to `Web` and set the value to `http://localhost`.</span></span>

    ![Uma captura de tela da página registrar um aplicativo](./images/02.png)

1. <span data-ttu-id="53ab2-112">Selecione **registrar**.</span><span class="sxs-lookup"><span data-stu-id="53ab2-112">Select **Register**.</span></span> <span data-ttu-id="53ab2-113">Na página **GraphNotificationTutorial** , copie o valor da ID do **aplicativo (cliente)** e da **ID de diretório (locatário)** salve-o, você precisará deles na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="53ab2-113">On the **GraphNotificationTutorial** page, copy the value of the **Application (client) ID** and **Directory (tenant) ID** save it, you will need them in the next step.</span></span>

    ![Uma captura de tela da ID do aplicativo do novo registro de aplicativo](./images/03.png)

1. <span data-ttu-id="53ab2-115">Selecione **Certificados e segredos** sob **Gerenciar**.</span><span class="sxs-lookup"><span data-stu-id="53ab2-115">Select **Certificates & secrets** under **Manage**.</span></span> <span data-ttu-id="53ab2-116">Selecione **novo segredo do cliente**.</span><span class="sxs-lookup"><span data-stu-id="53ab2-116">Select **New client secret**.</span></span> <span data-ttu-id="53ab2-117">Insira um valor em **Descrição** e selecione uma das opções para **expirar** e selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="53ab2-117">Enter a value in **Description** and select one of the options for **Expires** and select **Add**.</span></span>

    ![Uma captura de tela da caixa de diálogo Adicionar um segredo do cliente](./images/04.png)

1. <span data-ttu-id="53ab2-119">Copie o valor secreto do cliente antes de sair desta página.</span><span class="sxs-lookup"><span data-stu-id="53ab2-119">Copy the client secret value before you leave this page.</span></span> <span data-ttu-id="53ab2-120">Você precisará dele na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="53ab2-120">You will need it in the next step.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="53ab2-121">Este segredo do cliente nunca é mostrado novamente, portanto, copie-o agora.</span><span class="sxs-lookup"><span data-stu-id="53ab2-121">This client secret is never shown again, so make sure you copy it now.</span></span>

    ![Uma captura de tela do novo segredo do cliente recentemente adicionado](./images/05.png)

1. <span data-ttu-id="53ab2-123">Selecione **permissões de API** em **gerenciar**.</span><span class="sxs-lookup"><span data-stu-id="53ab2-123">Select **API Permissions** under **Manage**.</span></span> <span data-ttu-id="53ab2-124">**Adicione uma permissão** e selecione **Microsoft Graph**.</span><span class="sxs-lookup"><span data-stu-id="53ab2-124">**Add a permission** and select **Microsoft Graph**.</span></span> <span data-ttu-id="53ab2-125">Selecione **permissão de aplicativo** e expanda **usuário** e selecione o escopo **User. ReadWrite. All** .</span><span class="sxs-lookup"><span data-stu-id="53ab2-125">Select **Application Permission** and expand **User** and select the **User.ReadWrite.All** scope.</span></span> <span data-ttu-id="53ab2-126">Selecione **adicionar permissões** para salvar suas alterações.</span><span class="sxs-lookup"><span data-stu-id="53ab2-126">Select **Add permissions** to save your changes.</span></span>

    ![Uma captura de tela do novo segredo do cliente recentemente adicionado](./images/06.png)

<span data-ttu-id="53ab2-128">O aplicativo solicita uma permissão de aplicativo com o escopo **User. ReadWrite. All** .</span><span class="sxs-lookup"><span data-stu-id="53ab2-128">The application requests an application permission with the **User.ReadWrite.All** scope.</span></span> <span data-ttu-id="53ab2-129">Essa permissão exige o consentimento administrativo.</span><span class="sxs-lookup"><span data-stu-id="53ab2-129">This permission requires administrative consent.</span></span>

<span data-ttu-id="53ab2-130">Selecione **conceder consentimento do administrador para contoso** e, em seguida, selecione **Sim** para concordar com este aplicativo e conceder o acesso do aplicativo ao locatário usando os escopos especificados.</span><span class="sxs-lookup"><span data-stu-id="53ab2-130">Select **Grant admin consent for Contoso** and then select **Yes** to consent this application and grant the application access to your tenant using the scopes you specified.</span></span>

![Captura de tela de entrada](./images/07.png)
