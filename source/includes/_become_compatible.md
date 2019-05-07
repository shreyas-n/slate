# Join BotBroker

## Required Endpoints

If you'd like your bot to be added to BotBroker, we require you to create two endpoints so we can safely conduct transactions of your bot keys.

1. Key verification / information
2. Unbind & Key change

We expect you to follow our instructions listed, as well as the error spec [here](#errors)

## Key Verification / Information

The first endpoint we require is a `GET` request to verify the existence and details of a given key.

We can either send the key in a `JSON` body, or include it in query strings if that's more convenient for you to build.

If any errors occur in this request, please respond according to the error spec defined [here](#errors)

> The body we will send for the Key Verification / Information endpoint

```json
{
	"key": "XXXX-XXXX-XXXX-XXXX"
}
```

> The expected body for the Key Verification / Information endpoint

```json
    {
    	"success": true,
    	"key": "XXXX-XXXX-XXXX-XXXX",
    	"discordID": "{discord ID of currently bound discord or null if not bound}",
    	"banned": "false",
    	"renewal": true, (false if key is lifetime)
    	"expiration": 154656000 (epoch timestamp in seconds of expiration time)
    }
```

## Unbind & Key change

The second endpoint we require is a `POST` request that is sent as the sale is being conducted. On request, this endpoint should shuffle a key to update it with a new key string, and unbind whatever discord is currently bound to the key so the buyer can bind their discord.

If any errors occur in this request, please respond according to the error spec defined [here](#errors)

> The body we will send for the Unbind & Key change endpoint

```json
{
	"key": "XXXX-XXXX-XXXX-XXXX"
}
```

> The JSON body we expect returned for the Unbind & Key change request

```json
{
	"success": true,
	"key": "new key after shuffling"
}
```

## Errors

We expect you to handle errors properly and return a description of any errors or exceptions that occur.

We also expect you to use proper HTTP response codes i.e 404 when a key isn't found, 500 when there's a server error, 200 when okay. Read more [here](https://www.restapitutorial.com/httpstatuscodes.html).

> The JSON response we expect along with the relevant HTTP status code:

```json
{
	"success": false,
	"message": "an explanation of what went wrong"
}
```
