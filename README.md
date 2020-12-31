<h1 align="center">
    <a href="https://twitter.com/Spotted_do_tt">spotted</a>
</h1>
<p align="center">portal oficial do fogo no cu</p>

[![](https://img.shields.io/discord/794297088246153246?color=7289da&label=Discord&logo=Discord&style=for-the-badge)](https://discord.gg/fHaMSAKsg7)
[![](https://img.shields.io/static/v1?label=project%20version&message=v1.5&color=sucess&style=for-the-badge)](https://github.com/apatacadof/spotted/blob/main/spotted.py)
[![](https://img.shields.io/github/license/apatacadof/spotted?logo=&style=for-the-badge)](https://raw.githubusercontent.com/apatacadof/spotted/7a1142bd2d2aef7e32b69a8038080377b415d953/LICENSE)
[![](https://img.shields.io/static/v1?label=pyhon&message=2.7|3.5|3.6|3.7|3.8&logo=python&color=informational&style=for-the-badge)](https://www.python.org/)
[![](https://img.shields.io/static/v1?label=status&message=beta&color=yellowgreen&style=for-the-badge)](https://github.com/apatacadof/spotted/blob/main/spotted.py)

<b>#entenda o código: linha por linha<b>
 
    '''
    programa: spotted_do_tt
    linguagem: python v3.8
    autor: @Bruno_Miguelez_
    versão: v1.2
    '''

    <b>#importar as bibilhotecas necessarias para o projeto<b>
    import tweepy <b>#bibilhoteca não nativa, precisa digitar o comando 'pip install tweepy' no terminal para baixar<b>
    import time 

    <b>#logar pela api do twitter<b>
    auth = tweepy.OAuthHandler()
    auth.set_access_token()

    api = tweepy.API(auth, wait_on_rate_limit=True, wait_on_rate_limit_notify=True) <b>#estabelece limite de tempo entre requests<b>
    messages = api.list_direct_messages() <b>#defini mensagem<b>

    for message in messages: <b>#abre um loop, algo do tipo "se receber uma mensagem"<b>
        try:
            text = message.message_create["message_data"]["text"] <b>#filtra só o texto da msg e ""copia""<b>
            api.update_status(f'spotted: {text}') <b>#publica essa msg no perfil<b>
            api.destroy_direct_message(message.id) #apaga a dm
        
        
        except tweepy.TweepError as e: <b>#se der qualquer erro<b>
            print(e.reason)            <b>#me fala qual é<b>
        
    else: <b>#se n tiver nenuma DM<b>
        print ("nada bro") <b>#fala q n tem nd<b>
        time.sleep(60) <b>#espera 60 segundos (tempo limite da API do twitter) e volta pro começo, vê dnv se chegou alguma coisa<b>
