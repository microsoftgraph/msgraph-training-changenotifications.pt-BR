<!-- markdownlint-disable MD002 MD041 -->

Abra o prompt de comando, navegue até um diretório no qual você tem direitos para criar seu projeto e execute o seguinte comando para criar um novo aplicativo do .NET Core WebApi:

```shell
dotnet new webapi -o msgraphapp
```

Depois de criar o aplicativo, execute os seguintes comandos para garantir que o novo projeto seja executado corretamente.

  ```shell
  cd msgraphapp
  dotnet add package Microsoft.Identity.Client
  dotnet add package Microsoft.Graph
  dotnet run
  ```

  O aplicativo será iniciado e produzirá o seguinte:

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

Pare o aplicativo em execução pressionando <kbd>Ctrl</kbd>+<kbd>C</kbd>.

Abra o aplicativo no Visual Studio Code usando o seguinte comando:

```shell
code .
```

Se o código do Visual Studio exibir uma caixa de diálogo perguntando se você deseja adicionar ativos necessários ao projeto, selecione **Sim**.
