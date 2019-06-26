# <a name="using-change-notifications-and-track-changes-with-microsoft-graph"></a><span data-ttu-id="4a66b-101">Usando notificações de alteração e controlando alterações com o Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="4a66b-101">Using Change Notifications and Track Changes with Microsoft Graph</span></span>

<span data-ttu-id="4a66b-102">Neste laboratório, você criará um aplicativo de console do .NET Core que recebe notificações de alteração do Microsoft Graph quando uma atualização é feita para uma conta de usuário no Azure Active Directory (Azure AD).</span><span class="sxs-lookup"><span data-stu-id="4a66b-102">In this lab you will create a .NET Core console application that receives change notifications from the Microsoft Graph when an update is made to a users account in Azure Active Directory (Azure AD).</span></span> <span data-ttu-id="4a66b-103">O aplicativo gerenciará a assinatura de notificação de alteração e usará o controle de alterações no Microsoft Graph para garantir que nenhuma alteração seja perdida.</span><span class="sxs-lookup"><span data-stu-id="4a66b-103">The application will managed the Change Notification subscription and use Track Changes in the Microsoft Graph to ensure no changes are missed.</span></span>

## <a name="in-this-lab"></a><span data-ttu-id="4a66b-104">Neste laboratório</span><span class="sxs-lookup"><span data-stu-id="4a66b-104">In this lab</span></span>

1. [<span data-ttu-id="4a66b-105">Introdução ao laboratório</span><span class="sxs-lookup"><span data-stu-id="4a66b-105">Introduction to the lab</span></span>](./tutorial/01_intro.md)
1. [<span data-ttu-id="4a66b-106">Registrar e conceder consentimento para o aplicativo no Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="4a66b-106">Register and grant consent to the application in Microsoft Graph</span></span>](./tutorial/02_create-app.md)
1. [<span data-ttu-id="4a66b-107">Instalar o ngrok</span><span class="sxs-lookup"><span data-stu-id="4a66b-107">Install ngrok</span></span>](./tutorial/03_ngrok.md)
1. [<span data-ttu-id="4a66b-108">Criar o projeto do .NET Core</span><span class="sxs-lookup"><span data-stu-id="4a66b-108">Create the .NET Core project</span></span>](./tutorial/04_create-project.md)
1. [<span data-ttu-id="4a66b-109">Codificar a API HTTP</span><span class="sxs-lookup"><span data-stu-id="4a66b-109">Code the HTTP API</span></span>](./tutorial/05_add-code.md)
1. [<span data-ttu-id="4a66b-110">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="4a66b-110">Run the application</span></span>](./tutorial/06_run.md)
1. [<span data-ttu-id="4a66b-111">Gerenciar assinaturas de notificação</span><span class="sxs-lookup"><span data-stu-id="4a66b-111">Manage notification subscriptions</span></span>](./tutorial/07_subbscription-management.md)
1. [<span data-ttu-id="4a66b-112">Consultar alterações</span><span class="sxs-lookup"><span data-stu-id="4a66b-112">Query for changes</span></span>](./tutorial/08_deltaquery.md)
1. [<span data-ttu-id="4a66b-113">Laboratório concluído</span><span class="sxs-lookup"><span data-stu-id="4a66b-113">Completed Lab</span></span>](./tutorial/09_completed.md)

## <a name="prerequisites"></a><span data-ttu-id="4a66b-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4a66b-114">Prerequisites</span></span>

<span data-ttu-id="4a66b-115">Antes de iniciar este tutorial, você deve ter o [.NET Core 2,2 SDK](https://dotnet.microsoft.com/download) e o [código do Visual Studio](https://code.visualstudio.com/) instalados em sua máquina de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="4a66b-115">Before you start this tutorial, you should have [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com/) installed on your development machine.</span></span> 

## <a name="completed-exercises"></a><span data-ttu-id="4a66b-116">Exercícios concluídos</span><span class="sxs-lookup"><span data-stu-id="4a66b-116">Completed Exercises</span></span>

<span data-ttu-id="4a66b-117">As soluções concluídas são fornecidas [](./Demos) na pasta demos, se você ficar preso.</span><span class="sxs-lookup"><span data-stu-id="4a66b-117">Finished solutions are provided in the [Demos](./Demos) folder if you get stuck.</span></span>