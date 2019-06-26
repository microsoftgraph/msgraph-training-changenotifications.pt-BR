<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="e0346-101">Abra o prompt de comando, navegue até um diretório no qual você tem direitos para criar seu projeto e execute o seguinte comando para criar um novo aplicativo do .NET Core WebApi:</span><span class="sxs-lookup"><span data-stu-id="e0346-101">Open your command prompt, navigate to a directory where you have rights to create your project, and run the following command to create a new .NET Core WebApi app:</span></span>

```shell
dotnet new webapi -o msgraphapp
```

<span data-ttu-id="e0346-102">Depois de criar o aplicativo, execute os seguintes comandos para garantir que o novo projeto seja executado corretamente.</span><span class="sxs-lookup"><span data-stu-id="e0346-102">After creating the application, run the following commands to ensure your new project runs correctly.</span></span>

  ```shell
  cd msgraphapp
  dotnet add package Microsoft.Identity.Client
  dotnet add package Microsoft.Graph
  dotnet run
  ```

  <span data-ttu-id="e0346-103">O aplicativo será iniciado e produzirá o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e0346-103">The application will start and output the following:</span></span>

  ```shell
  info: Microsoft.AspNetCore.DataProtection.KeyManagement.XmlKeyManager[0] ...
  info: Microsoft.AspNetCore.DataProtection.KeyManagement.XmlKeyManager[58] ...
  warn: Microsoft.AspNetCore.DataProtection.KeyManagement.XmlKeyManager[35] ...
  info: Microsoft.AspNetCore.DataProtection.Repositories.FileSystemXmlRepository[39] ...
  Hosting environment: Development
  Content root path: /Users/ac/_play/graphchangenotifications/msgraphapp
  Now listening on: https://localhost:5001
  Now listening on: http://localhost:5000
  Application started. Press Ctrl+C to shut down.
  ```

<span data-ttu-id="e0346-104">Pare o aplicativo em execução pressionando <kbd>Ctrl</kbd>+<kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="e0346-104">Stop the application running by pressing <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

<span data-ttu-id="e0346-105">Abra o aplicativo no Visual Studio Code usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="e0346-105">Open the application in Visual Studio Code using the following command:</span></span>

```shell
code .
```

<span data-ttu-id="e0346-106">Se o código do Visual Studio exibir uma caixa de diálogo perguntando se você deseja adicionar ativos necessários ao projeto, selecione **Sim**.</span><span class="sxs-lookup"><span data-stu-id="e0346-106">If Visual Studio code displays a dialog box asking if you want to add required assets to the project, select **Yes**.</span></span>
