---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - json

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - become_compatible

search: true
---

# Introduction

> Current Base API Url

```
https://api.botbroker.io/api/v1
```

> If your API key is incorrect, you will get a `json` body returned to you that looks like this:

```json
{
  "success": false,
  "err": "Unauthorized",
  "apiKey": "{your api key}"
}
```

Welcome to the BotBroker API! You can use our API to retrieve BotBroker data.

Our API is a closed API and if you don't already have an API key, please follow [this](#apply-for-an-api-key) article

The other `.md` files within this directory contain API documentation

For all `GET` requests, you must put an `apiKey` parameter in the query strings of your request. For any other request, put an `apiKey` parameter in the body of your request.

# Apply for an API key

If you'd like to get access to the BotBroker REST API, you'll need to submit an application. The process is simple.

Draft out an email that gives clear, detailed answers to the following questions:

1. Who are you?
2. What is the core use case, or your purpose for your use with the BotBroker API?
3. How will BotBroker data be displayed to the users of your solution? If you plan to display BotBroker content, explain how and where you will be displaying data, as well as who will be seeing this data.
4. How many developers will be interacting with your BotBroker API key?

Please also provide your Twitter, and any other information you think is relevant to your application.

Then email your answers to `api@botbroker.io` with the subject line `API application`



# Bots


## Get All Bots


> The command returns JSON structured like this:

```json
[
  {
    "id":2,
    "name":"Ghost Phantom",
    "image":"https://i.imgur.com/8satPLU.png",
    "twitter":"ghostaio",
    "category":"footsites",
    "highest_bid":500,
    "lowest_ask":500
  },
  {
    "id":3,
    "name":"Ghost SNKRS",
    "image":"https://i.imgur.com/xc9OSts.png",
    "twitter":"ghostaio",
    "category":"nike",
    "highest_bid":0,
    "lowest_ask":0
  }
]
```

This endpoint retrieves all bots.

### HTTP Request

`GET /bots/all`

<aside class="success">
Remember — you must provide your API key in the URL parameters!
</aside>

## Get a Specific Bot

> The command returns JSON structured like this:

```json
{
  "id":2,
  "name":"Ghost Phantom",
  "image":"https://i.imgur.com/8satPLU.png",
  "twitter":"ghostaio",
  "category":"footsites",
  "highest_bid":500,
  "lowest_ask":500
}
```

This endpoint retrieves a specific bot and displays the data.
### HTTP Request

`GET bots/<ID>`
