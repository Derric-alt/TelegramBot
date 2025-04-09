import telebot
from telebot import types



#Conexion con nuestro BOT
TOKEN = "7732260952:AAFh8y64al-k7E46Wto5Y0pKwNC0Jrk-lqs"
bot = telebot.TeleBot(TOKEN)


 
 #creacion de comandos simples como "/start" y "/help"
@bot.message_handler(commands=["start"])
def send_welcome(message):
    bot.reply_to(message, "Hola! soy sabores locales bot para servirte, puedes usar el comando /help para saber los comandos que estan operativos")



@bot.message_handler(commands=["help"])
def send_help(message):
    bot.reply_to(message, "Puedes interactuar conmigo usando usando los comandos /start y /help tambien estan /foto y /ubicacion")


@bot.message_handler(commands=["ubicacion"])
def send_location(message):
    bot.reply_to(message, "Sí, Mega Arepa Cabimas está abierto todos los días de 12 PM a 12 AM. Se encuentra en el Centro Comercial El Paraíso, Carretera H.")
#@bot.message_handler(func=lambda m: True)
#def echo_all(message):
    #bot.reply_to(message, message.text)


    


@bot.message_handler(commands=["foto"])
def send_image(message):
    img_url = "https://th.bing.com/th/id/OIP.ymyGqQQPK_Vm0vEvVJDThgHaGh?rs=1&pid=ImgDetMain"
    bot.send_photo(chat_id=message.chat.id, photo=img_url, caption="Estos son los platos que sirven en Mega Arepa ofrecen: Arepitas, Hamburguesas, Patacones, Perros calientes, Pollo.")













if __name__ == "__main__":
    bot.polling(none_stop=True)
