<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="0f1ea-101">Abra o prompt de comando, navegue até um diretório no qual você tem direitos para criar arquivos e execute os seguintes comandos para criar um novo aplicativo do .NET Core WebApi.</span><span class="sxs-lookup"><span data-stu-id="0f1ea-101">Open your command prompt, navigate to a directory where you have rights to create files, and run the following commands to create a new .NET Core WebApi app.</span></span>

```shell
dotnet new webapi -o msgraphapp
```

<span data-ttu-id="0f1ea-102">Quando o comando terminar, execute os seguintes comandos para garantir que o novo projeto seja executado corretamente.</span><span class="sxs-lookup"><span data-stu-id="0f1ea-102">Once the command finishes, run the following commands to ensure your new project runs correctly.</span></span>

```shell
cd msgraphapp
dotnet add package Microsoft.Identity.Client
dotnet add package Microsoft.Graph
dotnet run
```

<span data-ttu-id="0f1ea-103">O aplicativo será iniciado e a saída:</span><span class="sxs-lookup"><span data-stu-id="0f1ea-103">The application will start and output:</span></span>

```shell
Now listening on: http://localhost:5000
```

<span data-ttu-id="0f1ea-104">Se você não vir essa saída ou se vir mensagens de erro, provavelmente haverá um problema com o [SDK do .NET Core 2,2](https://dotnet.microsoft.com/download) instalado em sua máquina de desenvolvimento que precisa ser corrigido antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="0f1ea-104">If you don't see this output, or you see error messages, there is likely a problem with the [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) installed on your development machine that needs to be fixed before continuing.</span></span>

<span data-ttu-id="0f1ea-105">Pare o aplicativo em execução pressionando <kbd>Ctrl</kbd>+<kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="0f1ea-105">Stop the application running by pressing <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

<span data-ttu-id="0f1ea-106">Abra o aplicativo no Visual Studio Code usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="0f1ea-106">Open the application in Visual Studio Code using the following command:</span></span>

```shell
code .
```

<span data-ttu-id="0f1ea-107">Quando uma caixa de diálogo pergunta se você deseja adicionar ativos necessários ao projeto, selecione **Sim**.</span><span class="sxs-lookup"><span data-stu-id="0f1ea-107">When a dialog box asks if you want to add required assets to the project, select **Yes**.</span></span>
