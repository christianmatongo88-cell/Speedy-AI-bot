from telegram import Update
from telegram.ext import Updater, CommandHandler, MessageHandler, Filters, CallbackContext

TELEGRAM_TOKEN =8543692267:AAGvtgYzb9IlurFYJ_2c_zoB0l7yuZ9wwaU

def start(update: Update, context: CallbackContext):
    update.message.reply_text("Hello! I am Speedy_IA. Ask me anything.")

def handle_message(update: Update, context: CallbackContext):
    user_text = update.message.text
    # For now, the bot just repeats the message
    reply = f"You said: {user_text}"
    update.message.reply_text(reply)

updater = Updater(TELEGRAM_TOKEN)
dp = updater.dispatcher
dp.add_handler(CommandHandler("start", start))
dp.add_handler(MessageHandler(Filters.text & ~Filters.command, handle_message))

updater.start_polling()
updater.idle()
