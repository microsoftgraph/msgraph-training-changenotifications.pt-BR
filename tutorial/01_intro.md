<!-- markdownlint-disable MD002 MD041 -->

Este tutorial ensina como criar um aplicativo do .NET Core que usa a API do Microsoft Graph para receber notificações (WebHooks) quando uma conta de usuário é alterada no Azure Active Directory (Azure AD) e realizar consultas usando a API de consulta Delta para receber todas as alterações do usuário contas desde que a última consulta foi feita.

> [!TIP]
> Se preferir baixar o tutorial concluído, você poderá baixar ou clonar o repositório do [GitHub](https://github.com/microsoftgraph/msgraph-training-changenotifications).

## <a name="prerequisites"></a>Pré-requisitos

Antes de iniciar este tutorial, você deve ter o [.NET Core 2,2 SDK](https://dotnet.microsoft.com/download) e o [código do Visual Studio](https://code.visualstudio.com/) instalados em sua máquina de desenvolvimento. Se você não os tiver instalado, visite os links anteriores para obter opções de download.

> [!NOTE]
> Este tutorial foi escrito com a versão 2,2 do .NET Core. As etapas deste guia podem funcionar com outras versões, mas que não foram testadas.

## <a name="feedback"></a>Comentários

Forneça comentários sobre este tutorial no [repositório do GitHub](https://github.com/microsoftgraph/msgraph-training-changenotifications).