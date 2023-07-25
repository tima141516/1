import discord
import random
from discord.ext import commands

f = open('main.py', 'r', encoding='utf-8')
text = f.read()
print(text)
f.close()




intents = discord.Intents.default()
intents.message_content = True

bot = commands.Bot(command_prefix='$', intents=intents)


@bot.event
async def on_ready():
    print(f'We have logged in as {bot.user}')


@bot.command()
async def hello(ctx):
    await ctx.send(f'Добрый день! Я бот {bot.user}!')
@bot.command()
async def dela(ctx):
    await ctx.send(f'хорошо,а у тебя {bot.user}!')

@bot.command()
async def bye(ctx):
    await ctx.send(f'пока {bot.user}!')

@bot.command()
async def add(ctx, left: int, right: int):
    """Adds two numbers together."""
    await ctx.send(left + right)


@bot.command()
async def heh(ctx, count_heh = 5):
    await ctx.send("he" * count_heh)


@bot.command()
async def revers(ctx, word):
    """Функция возвращает слово написанное наоборот"""
    word_revers = ''
    for letter in word[::-1]:
        word_revers = word_revers + letter

    await ctx.send(word_revers)


@bot.command()
async def mem(ctx):
    with open('images/mem1.jpg', 'rb') as f:
        # В переменную кладем файл, который преобразуется в файл библиотеки Discord!
        picture = discord.File(f)
   # Можем передавать файл как параметр!
    await ctx.send(file=picture)




@bot.command()
async def help_(ctx):
    """Функция возвращает список выполняемых ботом команд"""
    await ctx.send('Воспользуйтесь очень важной подсказкой:\n'
                   '$hello - приветствие бота\n'
                   '$dela - настроение бота\n'
                   '$add <два произвольных числа> - сложение двух чисел\n'
                   '$heh <количество повторов> - вывод размноженного слова "heh"\n'
                   '$bye - прощание бота\n'
                   '$revers <произвольное слово> - вывод слова в обратной последовательности')

bot.run("MTEyOTgxMjYxMTAyMjcyNTIzMQ.GgwTn4.pMmsF0KrdtNMIipijEMumS8MRis9zz0XfBXwaQ")

 



