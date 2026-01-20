# bot-telegram-sinais
main.py

from telegram.ext import Updater, CommandHandler
import os

TOKEN = os.getenv("TOKEN")

def start(update, context):
    update.message.reply_text("🤖 Bot online! Use /sinal")

def sinal(update, context):
    update.message.reply_text("⚽ Sinal ativo!\nOver 1.5 gols\nOdd mínima: 1.60")

def main():
    updater = Updater(TOKEN, use_context=True)
    dp = updater.dispatcher

    dp.add_handler(CommandHandler("start", start))
    dp.add_handler(CommandHandler("sinal", sinal))

    updater.start_polling()
    updater.idle()

if __name__ == "__main__":
    main()