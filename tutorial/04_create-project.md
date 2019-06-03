<!-- markdownlint-disable MD002 MD041 -->

Abra o prompt de comando, navegue até um diretório no qual você tem direitos para criar arquivos e execute os seguintes comandos para criar um novo aplicativo do .NET Core WebApi.

```shell
dotnet new webapi -o msgraphapp
```

Quando o comando terminar, execute os seguintes comandos para garantir que o novo projeto seja executado corretamente.

```shell
cd msgraphapp
dotnet add package Microsoft.Identity.Client
dotnet add package Microsoft.Graph
dotnet run
```

O aplicativo será iniciado e a saída:

```shell
Now listening on: http://localhost:5000
```

Se você não vir essa saída ou se vir mensagens de erro, provavelmente haverá um problema com o [SDK do .NET Core 2,2](https://dotnet.microsoft.com/download) instalado em sua máquina de desenvolvimento que precisa ser corrigido antes de continuar.

Pare o aplicativo em execução pressionando <kbd>Ctrl</kbd>+<kbd>C</kbd>.

Abra o aplicativo no Visual Studio Code usando o seguinte comando:

```shell
code .
```

Quando uma caixa de diálogo pergunta se você deseja adicionar ativos necessários ao projeto, selecione **Sim**.
