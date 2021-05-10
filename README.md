# insomnia-plugin-ftx-signing

All private FTX API calls require an authentication `SIGN` header (HMAC-SHA256) (see [here](https://docs.ftx.com/?python#authentication). 

This plugin (when installed) checks all outgoing requests to see if:

- The request is going to [https://ftx.com/api](https://ftx.com/api)
- An Insomnia environment variable `API_SECRET` exists
- A request header `FTX-TS` is present

If the above conditions are met, this plugin:

- Computes the HMAC signature based on timestamp, request method, endpoint path and request body
- Appends the `FTX-SIGN` header with the computed digest.

---
This plugin is heavily based on [insomnia-plugin-binance-signing](https://github.com/anson-vandoren/insomnia-plugin-binance-signing)
