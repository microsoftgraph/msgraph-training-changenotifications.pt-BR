<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="5815b-101">As assinaturas para notificações expiram e precisam ser renovadas periodicamente.</span><span class="sxs-lookup"><span data-stu-id="5815b-101">Subscriptions for notifications expire and need to be renewed periodically.</span></span> <span data-ttu-id="5815b-102">As etapas a seguir demonstrarão como renovar notificações</span><span class="sxs-lookup"><span data-stu-id="5815b-102">The following steps will demonstrate how to renew notifications</span></span>

<span data-ttu-id="5815b-103">Abrir **>** arquivo de NotificationsController.cs</span><span class="sxs-lookup"><span data-stu-id="5815b-103">Open **Controllers > NotificationsController.cs** file</span></span>

<span data-ttu-id="5815b-104">Adicione as duas declarações de membros a seguir `NotificationsController` à classe:</span><span class="sxs-lookup"><span data-stu-id="5815b-104">Add the following two member declarations to the `NotificationsController` class:</span></span>

```csharp
private static Dictionary<string, Subscription> Subscriptions = new Dictionary<string, Subscription>();
private static Timer subscriptionTimer = null;
```

<span data-ttu-id="5815b-105">Adicione os seguintes métodos novos.</span><span class="sxs-lookup"><span data-stu-id="5815b-105">Add the following new methods.</span></span> <span data-ttu-id="5815b-106">Eles implementarão um timer de plano de fundo que será executado a cada 15 segundos para verificar se as assinaturas expiraram.</span><span class="sxs-lookup"><span data-stu-id="5815b-106">These will implement a background timer that will run every 15 seconds to check if subscriptions have expired.</span></span> <span data-ttu-id="5815b-107">Se eles tiverem, serão renovados.</span><span class="sxs-lookup"><span data-stu-id="5815b-107">If they have, they will be renewed.</span></span>

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

<span data-ttu-id="5815b-108">O `CheckSubscriptions` método é chamado a cada 15 segundos pelo cronômetro.</span><span class="sxs-lookup"><span data-stu-id="5815b-108">The `CheckSubscriptions` method is called every 15 seconds by the timer.</span></span> <span data-ttu-id="5815b-109">Para uso de produção, deve ser definido como um valor mais razoável para reduzir o número de chamadas desnecessárias para o Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="5815b-109">For production use this should be set to a more reasonable value to reduce the number of unnecessary calls to Microsoft Graph.</span></span>

<span data-ttu-id="5815b-110">O `RenewSubscription` método renova uma assinatura e só é chamado se uma assinatura expirar nos próximos dois minutos.</span><span class="sxs-lookup"><span data-stu-id="5815b-110">The `RenewSubscription` method renews a subscription and is only called if a subscription is going to expire in the next two minutes.</span></span>

<span data-ttu-id="5815b-111">Localize o método `Get()` e substitua-o pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="5815b-111">Locate the method `Get()` and replace it with the following code:</span></span>

```csharp
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

<span data-ttu-id="5815b-112">Adicione a seguinte instrução após as instruções `using` existentes na parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="5815b-112">Add the following statement after the existing `using` statements at the top of the file:</span></span>

```csharp
using System.Threading;
```

### <a name="test-the-changes"></a><span data-ttu-id="5815b-113">Teste as alterações:</span><span class="sxs-lookup"><span data-stu-id="5815b-113">Test the changes:</span></span>

<span data-ttu-id="5815b-114">No Visual Studio Code, selecione **Debug > iniciar a depuração** para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5815b-114">Within Visual Studio Code, select **Debug > Start debugging** to run the application.</span></span>
<span data-ttu-id="5815b-115">Navegue até a seguinte URL: **http://localhost:5000/api/notifications**.</span><span class="sxs-lookup"><span data-stu-id="5815b-115">Navigate to the following url: **http://localhost:5000/api/notifications**.</span></span> <span data-ttu-id="5815b-116">Isso registrará uma nova assinatura.</span><span class="sxs-lookup"><span data-stu-id="5815b-116">This will register a new subscription.</span></span>

<span data-ttu-id="5815b-117">Na janela do Visual Studio Code **debug console** , aproximadamente a cada 15 segundos, observe o timer verificando a validade da assinatura:</span><span class="sxs-lookup"><span data-stu-id="5815b-117">In the Visual Studio Code **Debug Console** window, approximately every 15 seconds, notice the timer checking the subscription for expiration:</span></span>

```shell
Checking subscriptions 12:32:51.882
Current subscription count 1
```

<span data-ttu-id="5815b-118">Aguarde alguns minutos e você verá o seguinte quando a assinatura precisar de renovação:</span><span class="sxs-lookup"><span data-stu-id="5815b-118">Wait a few minutes and you will see the following when the subscription needs renewing:</span></span>

```shell
Renewed subscription: 07ca62cd-1a1b-453c-be7b-4d196b3c6b5b, New Expiration: 3/10/2019 7:43:22 PM +00:00
```

<span data-ttu-id="5815b-119">Isso indica que a assinatura foi renovada e mostra o novo tempo de expiração.</span><span class="sxs-lookup"><span data-stu-id="5815b-119">This indicates that the subscription was renewed and shows the new expiry time.</span></span>