---

copyright:
  years: 2015, 2017, 2019
lastupdated: "2019-06-06"

keywords: push notifications, notifications, configure sound, payload, ios badge, holding android notification

subcollection: mobile-pushnotification

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

#Ativando notificações push avançadas

Configure um badge iOS, som, carga útil JSON adicional, notificações acionáveis e notificações de participação.

## Configure o som, a carga útil e o badge do iOS
{: #badge-sound-payload}

Configure um badge iOS, som e carga útil JSON adicional.

1. No console do {{site.data.keyword.mobilepushshort}}, acesse a guia **Notificações**.
2. Acesse a seção **Campos opcionais** para configurar os recursos do {{site.data.keyword.mobilepushshort}}. 
	- **Arquivo de som** - insira uma sequência para apontar para o arquivo
de som em seu app móvel. Na carga útil, especifique o nome da sequência do
arquivo de som a ser usado.
	- **Badge iOS** - para dispositivos iOS, o
número a ser exibido como o badge do ícone do aplicativo. Se essa propriedade
estiver ausente, o badge não será mudado. Para remover o badge,
configure o valor dessa propriedade para 0.
3. Escolha uma das seguintes opções:	
	- No Android

     	Inclua seu arquivo de som no diretório `res/raw` do aplicativo Android. Ao enviar a notificação, inclua o nome do arquivo de som no campo de som do {{site.data.keyword.mobilepushshort}}:

    	```
    	"settings": {
         "gcm" : {
         "sound":"tt.wav",
	  }
    		}  
    	```	
    	{: codeblock}	
	
	- No iOS

    	```
    	"settings": {
    	     "apns" : {
    	      "badge": 10,
	      "sound": "tt.wav",
	  }
    	}
    	``` 
		{: codeblock}
		
**Carga útil adicional** - Essa carga útil pode ser qualquer par de valores de chave e deve ser um objeto JSON que você deseja enviar com o {{site.data.keyword.mobilepushshort}}.

```
{"key":"value", "key2":"value2"}
```
	{: codeblock}

## Participação de notificações do Android 
{: #hold-notifications-android}

Quando seu aplicativo entra em segundo plano, é possível que você queira que o {{site.data.keyword.mobilepushshort}} retenha as notificações enviadas para seu aplicativo. Para reter notificações, chame o método hold() no método onPause() da atividade que está manipulando o {{site.data.keyword.mobilepushshort}}.

```
@Override
protected void onPause() {
    super.onPause();
    if (push != null) {
        push.hold();
    }
} 
```
	{: codeblock}

    
