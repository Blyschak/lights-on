# Lights On

Use Telegram Bot and GitHub Workflows to notify you about power supply status on your OpenWRT router.

## Installation

- Telegram Bot setup
    - Create a [Telegram Bot](https://core.telegram.org/bots#how-do-i-create-a-bot)
    - Obtain the Telegram bot token
- GitHub setup
    - Fork this repository
    - Create personal GitHub [access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)
    - Add Telegram bot token ```TELEGRAM_TOKEN``` [secret](https://docs.github.com/en/actions/security-guides/encrypted-secrets) to your repository
- Router setup
    - Install [OpenWrt](https://openwrt.org/docs/guide-user/installation/generic.flashing) on your Router
    - Install ```curl``` and ```jq```: <br>
        ```opkg update && opkg install curl jq```
    - Set the following variables in the ```lightson``` script:
        - ```TELEGRAM_TOKEN``` - Telegram bot token
        - ```GH_USER``` - Your GitHub user
        - ```GH_TOKEN``` - Your personal GitHub access token
    - Copy ```lightson``` script to ```/usr/bin/``` on the router. Make sure it's executable and owned by root
    - Copy ```etc/init.d/lightson``` script to ```/etc/init.d/lightson``` on the router. Make sure it's executable and owned by root
    - Enable and start the service: <br>
        ```/etc/init.d/lightson enable && /etc/init.d/lightson start```
