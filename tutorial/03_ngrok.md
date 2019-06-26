<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="77a44-101">Para que o Microsoft Graph envie notificações para seu aplicativo em execução na sua máquina de desenvolvimento, você precisa usar uma ferramenta como o ngrok para encapsular chamadas da Internet para seu computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="77a44-101">In order for the Microsoft Graph to send notifications to your application running on your development machine you need to use a tool such as ngrok to tunnel calls from the internet to your development machine.</span></span> <span data-ttu-id="77a44-102">O Ngrok permite que as chamadas da Internet sejam direcionadas para o aplicativo executado localmente, sem a necessidade de criar regras de firewall.</span><span class="sxs-lookup"><span data-stu-id="77a44-102">Ngrok allows calls from the internet to be directed to your application running locally without needing to create firewall rules.</span></span>

<span data-ttu-id="77a44-103">Antes de continuar, você deve ter o [ngrok](https://ngrok.com) instalado em sua máquina de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="77a44-103">Before you continue you should have [ngrok](https://ngrok.com) installed on your development machine.</span></span> <span data-ttu-id="77a44-104">Se você não tiver o ngrok, visite o link anterior para obter instruções e opções de download.</span><span class="sxs-lookup"><span data-stu-id="77a44-104">If you do not have ngrok, visit the previous link for download options and instructions.</span></span>

<span data-ttu-id="77a44-105">Execute o ngrok executando o seguinte na linha de comando:</span><span class="sxs-lookup"><span data-stu-id="77a44-105">Run ngrok by executing the following from the command line:</span></span>

```shell
ngrok http 5000
```

<span data-ttu-id="77a44-106">Isso iniciará o ngrok e receberá o túnel de solicitações de uma URL de ngrok externa para sua máquina de desenvolvimento na porta 5000.</span><span class="sxs-lookup"><span data-stu-id="77a44-106">This will start ngrok and will tunnel requests from an external ngrok url to your development machine on port 5000.</span></span>

<span data-ttu-id="77a44-107">Copie o endereço de encaminhamento HTTPS.</span><span class="sxs-lookup"><span data-stu-id="77a44-107">Copy the https forwarding address.</span></span> <span data-ttu-id="77a44-108">No exemplo abaixo, isso seria `https://787b8292.ngrok.io`.</span><span class="sxs-lookup"><span data-stu-id="77a44-108">In the example below that would be `https://787b8292.ngrok.io`.</span></span> <span data-ttu-id="77a44-109">Isso será necessário posteriormente.</span><span class="sxs-lookup"><span data-stu-id="77a44-109">You will need this later.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="77a44-110">Cada vez que o ngrok for reiniciado, um novo endereço será gerado e será necessário copiá-lo novamente.</span><span class="sxs-lookup"><span data-stu-id="77a44-110">Each time ngrok is restarted a new address will be generated and you will need to copy it again.</span></span>

```shell
ngrok by @inconshreveable

Session Status                online
Account                       ???? ???? (Plan: Free)
Version                       2.3.15
Region                        United States (us)
Web Interface                 http://127.0.0.1:4040
Forwarding                    http://787b8292.ngrok.io -> http://localhost:5000
Forwarding                    https://787b8292.ngrok.io -> http://localhost:5000

Connections                   ttl     opn     rt1     rt5     p50     p90
                              0       0       0.00    0.00    0.00    0.00
```
