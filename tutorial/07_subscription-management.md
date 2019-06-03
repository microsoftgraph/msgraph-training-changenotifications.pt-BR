<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="9a193-101">As assinaturas para notificações expiram e precisam ser renovadas periodicamente.</span><span class="sxs-lookup"><span data-stu-id="9a193-101">Subscriptions for notifications expire and need to be renewed periodically.</span></span>

<span data-ttu-id="9a193-102">Abra **NotificationsController.cs** e substitua o `Get()` método pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="9a193-102">Open **NotificationsController.cs** and replace the `Get()` method with the following code:</span></span>

```csharp
private static Dictionary<string, Subscription> Subscriptions = new Dictionary<string, Subscription>();
private static Timer subscriptionTimer = null;

[HttpGet]
public ActionResult<string> Get()
{
  var graphServiceClient = GetGraphClient();

  var sub = new Microsoft.Graph.Subscription();
  sub.ChangeType = "updated";
  sub.NotificationUrl = config.Ngrok + "/api/notifications";
  sub.Resource = "/users";
  sub.ExpirationDateTime = DateTime.UtcNow.AddMinutes(5);
  sub.ClientState = "SecretClientState";

  var newSubscription = graphServiceClient
    .Subscriptions
    .Request()
    .AddAsync(sub).Result;

  Subscriptions[newSubscription.Id] = newSubscription;

  if(subscriptionTimer == null)
  {
      subscriptionTimer = new Timer(CheckSubscriptions, null, 5000, 15000);
  }

  return $"Subscribed. Id: {newSubscription.Id}, Expiration: {newSubscription.ExpirationDateTime}";
}
```

<span data-ttu-id="9a193-103">Adicione a instrução using a seguir na parte superior do arquivo.</span><span class="sxs-lookup"><span data-stu-id="9a193-103">Add the following using statement at the top of the file.</span></span>

```csharp
using System.Threading;
```

<span data-ttu-id="9a193-104">Este código acima adiciona um temporizador de plano de fundo que será acionado a cada 15 segundos e verificará se há assinaturas para ver se eles expiraram.</span><span class="sxs-lookup"><span data-stu-id="9a193-104">This code above adds a background timer that will fire every 15 seconds and check subscriptions to see if they have expired.</span></span>

<span data-ttu-id="9a193-105">Adicione os seguintes métodos novos:</span><span class="sxs-lookup"><span data-stu-id="9a193-105">Add the following new methods:</span></span>

```csharp
private void CheckSubscriptions(Object stateInfo)
{
  AutoResetEvent autoEvent = (AutoResetEvent)stateInfo;

  Console.WriteLine($"Checking subscriptions {DateTime.Now.ToString("h:mm:ss.fff")}");
  Console.WriteLine($"Current subscription count {Subscriptions.Count()}");

  foreach(var subscription in Subscriptions)
  {
    // if the subscription expires in the next 2 min, renew it
    if(subscription.Value.ExpirationDateTime < DateTime.UtcNow.AddMinutes(2))
    {
      RenewSubscription(subscription.Value);
    }
  }
}

private void RenewSubscription(Subscription subscription)
{
  Console.WriteLine($"Current subscription: {subscription.Id}, Expiration: {subscription.ExpirationDateTime}");

  var graphServiceClient = GetGraphClient();

  subscription.ExpirationDateTime = DateTime.UtcNow.AddMinutes(5);

  var foo = graphServiceClient
    .Subscriptions[subscription.Id]
    .Request()
    .UpdateAsync(subscription).Result;

  Console.WriteLine($"Renewed subscription: {subscription.Id}, New Expiration: {subscription.ExpirationDateTime}");
}
```

<span data-ttu-id="9a193-106">O `CheckSubscriptions` método é chamado a cada 15 segundos pelo cronômetro.</span><span class="sxs-lookup"><span data-stu-id="9a193-106">The `CheckSubscriptions` method is called every 15 seconds by the timer.</span></span> <span data-ttu-id="9a193-107">Para uso de produção, isso deve ser definido como um valor mais razoável para reduzir o número de chamadas desnecessárias ao gráfico.</span><span class="sxs-lookup"><span data-stu-id="9a193-107">For production use this should be set to a more reasonable value to reduce the number of unnecessary calls to Graph.</span></span> <span data-ttu-id="9a193-108">O `RenewSubscription` método renova uma assinatura e só é chamado se uma assinatura expirar nos próximos dois minutos.</span><span class="sxs-lookup"><span data-stu-id="9a193-108">The `RenewSubscription` method renews a subscription and is only called if a subscription is going to expire in the next two minutes.</span></span>

<span data-ttu-id="9a193-109">Selecione **Debug > iniciar depuração** para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9a193-109">Select **Debug > Start debugging** to run the application.</span></span> <span data-ttu-id="9a193-110">Navegue até a seguinte URL `*http://localhost:5000/api/notifications` para registrar uma nova assinatura.</span><span class="sxs-lookup"><span data-stu-id="9a193-110">Navigate to the following url `*http://localhost:5000/api/notifications` to register a new subscription.</span></span>

<span data-ttu-id="9a193-111">Você verá o seguinte resultado na janela do `DEBUG OUTPUT` Visual Studio Code aproximadamente a cada 15 segundos.</span><span class="sxs-lookup"><span data-stu-id="9a193-111">You will see the following output in the `DEBUG OUTPUT` window of Visual Studio Code approximately every 15 seconds.</span></span>  <span data-ttu-id="9a193-112">Este é o timer verificando a validade da assinatura.</span><span class="sxs-lookup"><span data-stu-id="9a193-112">This is the timer checking the subscription for expiry.</span></span>

```shell
Checking subscriptions 12:32:51.882
Current subscription count 1
```

<span data-ttu-id="9a193-113">Aguarde alguns minutos e você verá o seguinte quando a assinatura precisar de renovação:</span><span class="sxs-lookup"><span data-stu-id="9a193-113">Wait a few minutes and you will see the following when the subscription needs renewing:</span></span>

```shell
Renewed subscription: 07ca62cd-1a1b-453c-be7b-4d196b3c6b5b, New Expiration: 3/10/2019 7:43:22 PM +00:00
```

<span data-ttu-id="9a193-114">Isso indica que a assinatura foi renovada e mostra o novo tempo de expiração.</span><span class="sxs-lookup"><span data-stu-id="9a193-114">This indicates that the subscription was renewed and shows the new expiry time.</span></span>
