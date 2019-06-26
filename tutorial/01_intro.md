<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="034e6-101">Este tutorial ensina como criar um aplicativo do .NET Core que usa a API do Microsoft Graph para receber notificações (WebHooks) quando uma conta de usuário é alterada no Azure Active Directory (Azure AD) e realizar consultas usando a API de consulta Delta para receber todas as alterações do usuário contas desde que a última consulta foi feita.</span><span class="sxs-lookup"><span data-stu-id="034e6-101">This tutorial teaches you how to build a .NET Core app that uses the Microsoft Graph API to receive notifications (webhooks) when a user account changes in Azure Active Directory (Azure AD) and perform queries using the delta query API to receive all changes to user accounts since the last query was made.</span></span>

> [!TIP]
> <span data-ttu-id="034e6-102">Se preferir baixar o tutorial concluído, você poderá baixar ou clonar o repositório do [GitHub](https://github.com/microsoftgraph/msgraph-training-changenotifications).</span><span class="sxs-lookup"><span data-stu-id="034e6-102">If you prefer to just download the completed tutorial, you can download or clone the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-changenotifications).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="034e6-103">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="034e6-103">Prerequisites</span></span>

<span data-ttu-id="034e6-104">Antes de iniciar este tutorial, você deve ter o [.NET Core 2,2 SDK](https://dotnet.microsoft.com/download) e o [código do Visual Studio](https://code.visualstudio.com/) instalados em sua máquina de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="034e6-104">Before you start this tutorial, you should have [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com/) installed on your development machine.</span></span>

> [!NOTE]
> <span data-ttu-id="034e6-105">Este tutorial foi escrito com a versão 2,2 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="034e6-105">This tutorial was written with .NET Core version 2.2.</span></span> <span data-ttu-id="034e6-106">As etapas deste guia podem funcionar com outras versões, mas que não foram testadas.</span><span class="sxs-lookup"><span data-stu-id="034e6-106">The steps in this guide may work with other versions, but that has not been tested.</span></span>

## <a name="watch-the-tutorial"></a><span data-ttu-id="034e6-107">Assista ao tutorial</span><span class="sxs-lookup"><span data-stu-id="034e6-107">Watch the tutorial</span></span>

<span data-ttu-id="034e6-108">Este módulo foi gravado e está disponível no canal do Office Development YouTube.</span><span class="sxs-lookup"><span data-stu-id="034e6-108">This module has been recorded and is available in the Office Development YouTube channel.</span></span>

<!-- markdownlint-disable MD033 MD034 -->
<br/>

> [!VIDEO https://www.youtube-nocookie.com/embed/fThiCZmIcMQ]
<!-- markdownlint-enable MD033 MD034 -->

## <a name="feedback"></a><span data-ttu-id="034e6-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="034e6-109">Feedback</span></span>

<span data-ttu-id="034e6-110">Forneça comentários sobre este tutorial no [repositório do GitHub](https://github.com/microsoftgraph/msgraph-training-changenotifications).</span><span class="sxs-lookup"><span data-stu-id="034e6-110">Please provide any feedback on this tutorial in the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-changenotifications).</span></span>
