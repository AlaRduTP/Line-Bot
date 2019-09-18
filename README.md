# Line-Bot

## Deploy

1. Create a new **Line Messaging API Channel**.
2. **Fork** this repository.
3. On **your repo**,
	- [Deploy to Heroku](https://heroku.com/deploy)
	- Set **Config Vars**
		- access_token: **Channel access token**
		- channel_secret: **Channel secret**
	- Deploy app
4. Back to **Line Channel settings**,
	- Enable webhook
	- Set **Webhook URL** to `https://your_heroku_app_url/webhook` and verify.
5. In Line Official Account Manager,
	- Enable **Webhook**

## Webhook

server.py
```python
from linebot import simple_bot

SB = simple_bot()


@SB.webhook
def webhook():
    pass

```

## reply.cfg

There are two methods: `regex`, `kwywd`
> Regular expression and keywords.

And support three types of message: `text`, `sticker`, `image`

---

### text

- text

### sticker

- packageId
- stickerId

You can find `packageId` and `stickerId` in [sticker list](https://developers.line.biz/media/messaging-api/sticker_list.pdf).

### image

- originalContentUrl
- previewImageUrl

---

You can find examples in `reply.cfg`.

## server.py

### Regular Expression
```python
SB.regex(regex_str)(reply_func)
```

### Keywords
```python
SB.keywds(kwywds_list)(reply_func)
```

---

#### reply_func

Each `reply_func` should return a `msg_dict`.
The keys and values in `msg_dict` are the same as in `reply.cfg`.

---

You can find examples in `server.py`.
