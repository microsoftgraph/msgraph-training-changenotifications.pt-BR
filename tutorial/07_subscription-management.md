<!-- markdownlint-disable MD002 MD041 -->

As assinaturas para notificações expiram e precisam ser renovadas periodicamente.

Abra **NotificationsController.cs** e substitua o `Get()` método pelo seguinte código:

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

Adicione a instrução using a seguir na parte superior do arquivo.

```csharp
using System.Threading;
```

Este código acima adiciona um temporizador de plano de fundo que será acionado a cada 15 segundos e verificará se há assinaturas para ver se eles expiraram.

Adicione os seguintes métodos novos:

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

O `CheckSubscriptions` método é chamado a cada 15 segundos pelo cronômetro. Para uso de produção, isso deve ser definido como um valor mais razoável para reduzir o número de chamadas desnecessárias ao gráfico. O `RenewSubscription` método renova uma assinatura e só é chamado se uma assinatura expirar nos próximos dois minutos.

Selecione **Debug > iniciar depuração** para executar o aplicativo. Navegue até a seguinte URL `*http://localhost:5000/api/notifications` para registrar uma nova assinatura.

Você verá o seguinte resultado na janela do `DEBUG OUTPUT` Visual Studio Code aproximadamente a cada 15 segundos.  Este é o timer verificando a validade da assinatura.

```shell
Checking subscriptions 12:32:51.882
Current subscription count 1
```

Aguarde alguns minutos e você verá o seguinte quando a assinatura precisar de renovação:

```shell
Renewed subscription: 07ca62cd-1a1b-453c-be7b-4d196b3c6b5b, New Expiration: 3/10/2019 7:43:22 PM +00:00
```

Isso indica que a assinatura foi renovada e mostra o novo tempo de expiração.
