<!-- markdownlint-disable MD002 MD041 -->

Para que o Microsoft Graph envie notificações para seu aplicativo em execução na sua máquina de desenvolvimento, você precisa usar uma ferramenta como o ngrok para encapsular chamadas da Internet para seu computador de desenvolvimento. O Ngrok permite que as chamadas da Internet sejam direcionadas para o aplicativo executado localmente, sem a necessidade de criar regras de firewall.

Antes de continuar, você deve ter o [ngrok](https://ngrok.com) instalado em sua máquina de desenvolvimento. Se você não tiver o ngrok, visite o link anterior para obter instruções e opções de download.

Execute o ngrok executando o seguinte na linha de comando:

```shell
ngrok http 5000
```

Isso iniciará o ngrok e receberá o túnel de solicitações de uma URL de ngrok externa para sua máquina de desenvolvimento na porta 5000.

Copie o endereço de encaminhamento HTTPS. No exemplo abaixo, isso seria `https://787b8292.ngrok.io`. Isso será necessário posteriormente.

> [!IMPORTANT]
> Cada vez que o ngrok for reiniciado, um novo endereço será gerado e será necessário copiá-lo novamente.

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
