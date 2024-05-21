# telegram-username-sniper
A lightning-fast and efficient telegram sniper written in Go. Automatically monitors and claims usernames as soon as they become available.

## How does it work?

Simple, it uses [fragment](https://fragment.com/) to check for the username availability, once it becomes available it will use the [telegram api](https://core.telegram.org/api) to create a new channel with the username that just became available, let's imagine the scenario where you're sniping `dead` and it suddenly becomes available, your account will then create a channel that you can find at `t.me/dead`

## FAQ

**Q: Can I snipe usernames on auction at fragment?** 

**A:** No, you can’t. The usernames being auctioned are autoswapped, so they never become available for claiming.

**Q: Can I use a bot token?** 

**A:** No, you can’t. bots don't have access to the `channels.createChannel` method, which is required for this program to work.

**Q: Why does it claim to a channel and not to my account?** 

**A:** You can change this in settings, but channel is recommended since it has less ratelimits, you can still auction the channel usernames in [fragment](https://fragment.com/).

**Q: Can I target as many usernames as I want?** 

**A:** Yes! You can, but it's not recommended, there's no limit set, but I advise you to not add more than 5 usernames, because if you're checking 50 usernames at the same time, the chance is you will miss out on an username that just became available, **having less usernames and a lot of patience will increase your chances of getting that username drastically**.

**Q: How do I find usernames to snipe?** 

**A:** I can provide you with the following options: 
  1. **Online Marketplaces**: Search for Telegram usernames being sold on various online marketplaces.
     
  2. **Telegram Inactive Accounts**: Look for your desired username on Telegram. If the account status says "Last seen a long time ago...", it might mean the account is set to be deleted soon due to inactivity. Telegram's "Delete if away for..." setting ranges from 1 month to 1 year.

## Configuration

```json
{
    "telegram": {
        "phone_number": "",
        "api_id": 0,
        "api_hash": ""
    },

    "claim_to": "user",
    "sleep_between_check": 100,
    "usernames": [
        "waquan"
    ]
}
```
- **phone_number**: Your phone number associated to the telegram account in international format (e.g., `+12342348237`)
- **api_id**, **api_hash**: Both of these you can obtain from the [telegram portal](https://my.telegram.org)
- **claim_to**: This is the method for claiming you want to use, it can either be `channel` or `user`
- **sleep_between_check**: The time to sleep between a check, in milliseconds, setting the value of this to less than `100` may trigger ratelimits
- **usernames**: Provide here the list of usernames you want to monitor (e.g., `["dead", "devious"]`)

## Usage
- [Download the latest release](https://github.com/qg5/telegram-username-sniper/releases)
- [Download the config file](https://github.com/qg5/telegram-username-sniper/blob/main/config.json)
- Fill the config file
- Place both, the executable and the config in the same folder
- Now you should be able to run the executable

## Usage with Go
- [Download Go](https://go.dev/dl/)
- [Download the repository](https://github.com/qg5/telegram-username-sniper/archive/refs/heads/main.zip)
- Extract the files
- Fill the config file
- Navigate to `cmd/app` and execute one of these commands in your terminal `go run .` or `go run main.go`
