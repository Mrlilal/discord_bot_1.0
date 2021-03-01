# Discord Twitter Bot

[![Discord](https://discordapp.com/api/guilds/(GUILD_ID)/embed.png)](https://discord.gg/(INVITE_CODE)) 

A Discord bot that forwards Tweets into your Discord server.

> Take note that this bot uses the search API and not the streaming API. This means that the results are not exhaustive nor are they instantaneous. However, the trade-off here is that the nature of searching allows for the use of powerful search operators to filter the results to your needs.

## Setup

> Don't forget to give your bot the `Manage Webhooks` permission!

> npm i -s twitter-lite@^0.14.0 to install this widget's dependencies.

- Open [config.json](https://github.com/peterthehan/discord-twitter-bot/blob/master/config.json) to configure your own settings:

```js
{
  "twitterKeys": {
    "consumer_key": "TWITTER_CONSUMER_KEY_PLACEHOLDER",
    "consumer_secret": "TWITTER_CONSUMER_SECRET_PLACEHOLDER",
    "access_token_key": "TWITTER_ACCESS_TOKEN_KEY_PLACEHOLDER",
    "access_token_secret": "TWITTER_ACCESS_TOKEN_SECRET_PLACEHOLDER"
  },
  "rules": [
    {
      "channelId": "CHANNEL_ID",
      "delay": 3600000,
      "randomDelay": 0,
      "parameters": {
        "q": "from:@NoContextWeeb exclude:replies exclude:retweets",
        "result_type": "recent",
        "count": 1
      }
    },
    // ...Add as many rules as you want.
  ]
}
```

- `twitterKeys`: Apply for a [Twitter developer account](https://developer.twitter.com/en/apply-for-access) in order to access their standard APIs. You will receive the necessary keys once your account is approved.
- `channelId` is the text channel you want Tweets to be forwarded to.
- `delay` (in milliseconds) is the interval the bot will run the Twitter search query to check for new results. `delay` defaults to 15 minutes if not provided.
  - Take note of search's [rate limit](https://developer.twitter.com/en/docs/twitter-api/v1/rate-limits) of `450 requests per 15 minutes` when configuring your rules.
- `randomDelay` (in milliseconds) is the random interval added to the `delay`. `randomDelay` defaults to 0 minutes if not provided.
- `parameters` are provided to the Twitter search endpoint. Reference can be found here: https://developer.twitter.com/en/docs/twitter-api/v1/tweets/search/api-reference/get-search-tweets
  - The `q` (query) parameter allows for powerful search operators. Reference can be found here: https://developer.twitter.com/en/docs/twitter-api/v1/tweets/search/guides/standard-operators