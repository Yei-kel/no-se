 import discord
import random

coin = ['face','cross']
emoji = ["\U0001F604","\U0001F44D","\U00002764"]
caracteres = ["+", "-", "/", "*", "!", "&", "$", "#", "?", "=", "@", "a", "b", "c", "d", "e", "f", "g", "h", "i", "j", "k", "l", "n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z",  "A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z", "1", "2", "3", "4", "5", "6", "7", "8", "9", "0"]

# La variable intents almacena los privilegios del bot
intents = discord.Intents.default()
# Activar el privilegio de lectura de mensajes
intents.message_content = True
# Crear un bot en la variable cliente y transferirle los privilegios
client = discord.Client(intents=intents)

@client.event
async def on_ready():
    print(f'Hemos iniciado sesión como {client.user}')

@client.event
async def on_message(message):
    if message.author == client.user:
        return
    elif message.content.startswith('eliminate'):
            msg = await message.channel.send('I will eliminate now...')
            await msg.delete()

            await message.channel.send('Goodbye in 3 seconds...', delete_after=3.0)

    async def on_message_delete(self, message):
        msg = f'{message.author} has deleted the message: {message.content}'
        await message.channel.send(msg)
    if message.content.startswith('hello'):
        await message.channel.send("hi!")
    elif message.content.startswith('bye'):
        await message.channel.send("\U0001F44B")
    elif message.content.startswith('flip'):
        result = random.choice(coin)
        await message.channel.send(result)
    elif message.content.startswith('joke'):
        await message.channel.send('Como maldice un pollo a otro pollo?, Caldito seas')
    elif message.content.startswith('emoji'):
        result1 = random.choice(emoji)
        await message.channel.send(result1)
    elif message.content.startswith('password'):
        secuencia_aleatoria = (random.choice(caracteres))
        await message.channel.send(secuencia_aleatoria)
    elif message.content.startswith('help'):
        await message.channel.send('My comands are: hello, bye, flip, joke, emoji, password. If you need know what do the comand put 1,2,3,4,5,6,sc')
    elif message.content.startswith('1'):
        await message.channel.send('You say hello')
    elif message.content.startswith('2'):
        await message.channel.send('You say bye')
    elif message.content.startswith('3'):
        await message.channel.send('You flip a coin')
    elif message.content.startswith('4'):
        await message.channel.send('The chatbot say a joke')
    elif message.content.startswith('5'):
        await message.channel.send('The chatbot show a emoji')
    elif message.content.startswith('6'):
        await message.channel.send('The chatbot choose a character')
    elif message.content.startswith('sc'):
        await message.channel.send('mY secrets co|\/|4Nds ARE* e1imiNate aNd a!phabet')
    elif message.content.startswith('alphabet'):
        await message.channel.send('A = @, b = {, "c", "d", "e", "f", "g", "h", "i", "j", "k", "l", "n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z"')
    else:
        await message.channel.send(message.content)
    
        

client.run("") 
