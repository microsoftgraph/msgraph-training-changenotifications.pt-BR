<!-- markdownlint-disable MD002 MD041 -->

Selecione **Debug > iniciar depuração** para executar o aplicativo. Depois de criar o aplicativo, uma janela do navegador será aberta para uma página 404. Isso é válido, pois nosso aplicativo é uma API e não uma página da Web.

Para inscrever-se para notificações de alteração para usuários, `http://localhost:5000/api/notifications`navegue até a URL a seguir. Se tiver êxito, você verá a saída que inclui uma ID de assinatura como a seguinte:

```shell
Subscribed. Id: e2dbfbe1-160b-42b0-9b9f-8ab79bf8dfed
```

Seu aplicativo agora está inscrito para receber notificações do Microsoft Graph quando uma atualização é feita em qualquer usuário no locatário do Office 365.

Abra um navegador e visite o [centro de administração do Microsoft 365](https://admin.microsoft.com/AdminPortal). Entre usando uma conta de administrador. Selecione **usuários > usuários ativos**. Selecione um usuário ativo e selecione **Editar** para suas **informações de contato**. Atualize o valor do **telefone celular** com um novo número e selecione **salvar**.

![Captura de tela dos detalhes do usuário](./images/03.png)

No **console de depuração** do Visual Studio, você verá que uma notificação foi recebida. Às vezes, isso pode levar alguns minutos para chegar. Um exemplo de saída está abaixo de:

```shell
Received notification: 'Users/7a7fded6-0269-42c2-a0be-512d58da4463', 7a7fded6-0269-42c2-a0be-512d58da4463
```

Isso indica que o aplicativo recebeu com êxito a notificação do Microsoft Graph para o usuário especificado na saída. Você pode usar essas informações para consultar o gráfico para obter os detalhes completos, se quiser sincronizar seus detalhes no aplicativo.