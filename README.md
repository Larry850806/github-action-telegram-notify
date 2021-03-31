# Github Action Telegram Notify

This project is used to show how to use Github action to send telegram message when there is a new issue.

With the following workflow, When someone open a new issue on the repository. The bot will send "剛剛有人開了新 issue ～" to your telegram account

```yml
name: Telegram notify

on:
  issues:
    types: [opened]

jobs:
  send:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@master
      - name: send custom message with args
        uses: appleboy/telegram-action@master
        with:
          to: ${{ secrets.TELEGRAM_TO }}
          token: ${{ secrets.TELEGRAM_TOKEN }}
          args: 剛剛有人開了新 issue ～
```

