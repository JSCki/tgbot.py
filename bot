from telegram import Update, InlineKeyboardButton, InlineKeyboardMarkup
from telegram.ext import Updater, CommandHandler, CallbackQueryHandler, CallbackContext
import random

# List of photos (use your own images or URLs)
photos = [
    "https://via.placeholder.com/300.png?text=Photo+1",
    "https://via.placeholder.com/300.png?text=Photo+2",
    "?text=Photo+3",
]

def start(update: Update, context: CallbackContext):
    """Start command handler to show the refresh button."""
    keyboard = [
        [InlineKeyboardButton("Refresh", callback_data="refresh")]
    ]
    reply_markup = InlineKeyboardMarkup(keyboard)
    update.message.reply_text("Click the button to refresh the image.", reply_markup=reply_markup)

def refresh(update: Update, context: CallbackContext):
    """Handle the refresh button click."""
    query = update.callback_query
    query.answer()  # Acknowledge the button click

    # Delete the button message
    query.delete_message()

    # Choose a random photo and send it
    photo_url = random.choice(photos)
    keyboard = [
        [InlineKeyboardButton("Refresh", callback_data="refresh")]
    ]
    reply_markup = InlineKeyboardMarkup(keyboard)
    query.message.reply_photo(photo=photo_url, caption="Here is a new image!", reply_markup=reply_markup)

def main():
    """Main function to start the bot."""
    # Replace 'YOUR_BOT_TOKEN' with your actual bot token
    updater = Updater("7629367266:AAGK-Qcv0xmFHctTtTm1SM_SihDYOkj-2uw")

    # Register handlers
    updater.dispatcher.add_handler(CommandHandler("start", start))
    updater.dispatcher.add_handler(CallbackQueryHandler(refresh, pattern="refresh"))

    # Start the bot
    updater.start_polling()
    updater.idle()

if __name__ == "__main__":
    main()
