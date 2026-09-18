# Telcom Tech — Telegram Bot

A Telegram storefront bot for Telcom Tech, selling IKE PBX systems and Panaphone desk phones. This is a fresh, standalone project — it shares no files or history with the old farm-tools bot.

## 1. Configure

```bash
cd telcomtech-bot
cp .env.example .env
```

Open `.env` and fill in:
- `BOT_TOKEN` — from @Telcomtech_bot's setup with BotFather:
  `8398839029:AAHYRcAPmRP2o0O7gDBdmAVOnZ2-DvPhLvM`
  (Consider running `/revoke` with BotFather to get a fresh token, since this one has been shared in chat.)
- `ADMIN_CHAT_ID` — your personal Telegram chat ID from @userinfobot (optional, enables order alerts to you)

## 2. Install and run

```bash
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt
python bot.py
```

Message **@Telcomtech_bot** on Telegram and send `/start`.

Orders are saved to `orders.json` in this folder as they come in — this file starts empty and is created automatically on the first order.

## 3. The Mini App website

The "Open Shop" button opens a website hosted separately on GitHub Pages, expected at:

`https://kheangrithyreak-sudo.github.io/telcomtech-store/`

That website lives in its own repository (`telcomtech-store`), not in this one. If you change that URL, update the `SHOP_URL` constant near the top of `bot.py` to match.

## 4. Editing the product catalog

Products live near the top of `bot.py` in the `PRODUCTS` list — add, remove, or reprice items there. Keep this in sync with the product list in the website's `index.html` (in the `telcomtech-store` repo) so customers see the same catalog in both places.

## 5. Deploying so it runs all the time

Running `python bot.py` on your own PC only works while it's on. To keep the bot running permanently, deploy this folder to a host such as Railway or Render — set `BOT_TOKEN` and `ADMIN_CHAT_ID` as environment variables there, and use `python bot.py` as the start command.
