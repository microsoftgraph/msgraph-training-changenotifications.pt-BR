# <a name="using-change-notifications-and-track-changes-with-microsoft-graph"></a>Usando notificações de alteração e controlando alterações com o Microsoft Graph

Neste laboratório, você criará um aplicativo de console do .NET Core que recebe notificações de alteração do Microsoft Graph quando uma atualização é feita para uma conta de usuário no Azure Active Directory (Azure AD). O aplicativo gerenciará a assinatura de notificação de alteração e usará o controle de alterações no Microsoft Graph para garantir que nenhuma alteração seja perdida.

## <a name="in-this-lab"></a>Neste laboratório

1. [Introdução ao laboratório](./tutorial/01_intro.md)
1. [Registrar e conceder consentimento para o aplicativo no Microsoft Graph](./tutorial/02_create-app.md)
1. [Instalar o ngrok](./tutorial/03_ngrok.md)
1. [Criar o projeto do .NET Core](./tutorial/04_create-project.md)
1. [Codificar a API HTTP](./tutorial/05_add-code.md)
1. [Executar o aplicativo](./tutorial/06_run.md)
1. [Gerenciar assinaturas de notificação](./tutorial/07_subbscription-management.md)
1. [Consultar alterações](./tutorial/08_deltaquery.md)
1. [Laboratório concluído](./tutorial/09_completed.md)

## <a name="prerequisites"></a>Pré-requisitos

Antes de iniciar este tutorial, você deve ter o [.NET Core 2,2 SDK](https://dotnet.microsoft.com/download) e o [código do Visual Studio](https://code.visualstudio.com/) instalados em sua máquina de desenvolvimento. 

## <a name="completed-exercises"></a>Exercícios concluídos

As soluções concluídas são fornecidas [](./Demos) na pasta demos, se você ficar preso.