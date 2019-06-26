<!-- markdownlint-disable MD002 MD041 -->

As assinaturas para notificações expiram e precisam ser renovadas periodicamente. As etapas a seguir demonstrarão como renovar notificações

Abrir **>** arquivo de NotificationsController.cs

Adicione as duas declarações de membros a seguir `NotificationsController` à classe:

```csharp
private static Dictionary<string, Subscription> Subscriptions = new Dictionary<string, Subscription>();
private static Timer subscriptionTimer = null;
```

Adicione os seguintes métodos novos. Eles implementarão um timer de plano de fundo que será executado a cada 15 segundos para verificar se as assinaturas expiraram. Se eles tiverem, serão renovados.

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

O `CheckSubscriptions` método é chamado a cada 15 segundos pelo cronômetro. Para uso de produção, deve ser definido como um valor mais razoável para reduzir o número de chamadas desnecessárias para o Microsoft Graph.

O `RenewSubscription` método renova uma assinatura e só é chamado se uma assinatura expirar nos próximos dois minutos.

Localize o método `Get()` e substitua-o pelo seguinte código:

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

Adicione a seguinte instrução após as instruções `using` existentes na parte superior do arquivo:

```csharp
using System.Threading;
```

### <a name="test-the-changes"></a>Teste as alterações:

No Visual Studio Code, selecione **Debug > iniciar a depuração** para executar o aplicativo.
Navegue até a seguinte URL: **http://localhost:5000/api/notifications**. Isso registrará uma nova assinatura.

Na janela do Visual Studio Code **debug console** , aproximadamente a cada 15 segundos, observe o timer verificando a validade da assinatura:

```shell
Checking subscriptions 12:32:51.882
Current subscription count 1
```

Aguarde alguns minutos e você verá o seguinte quando a assinatura precisar de renovação:

```shell
Renewed subscription: 07ca62cd-1a1b-453c-be7b-4d196b3c6b5b, New Expiration: 3/10/2019 7:43:22 PM +00:00
```

Isso indica que a assinatura foi renovada e mostra o novo tempo de expiração.