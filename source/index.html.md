---
title: Huobi API Reference v1.0

language_tabs: # must be one of https://git.io/vQNgJ
  - json

toc_footers:
  - <a href='https://www.huobi.pro/apikey/'>Sign Up for a Huobi API key </a>
  - Login is required for creating an API key

includes:

search: true
---

# Change Log

| Release Time (Singapore Time UTC +8) | API | New / Update | Description |
|-----|-----|-----|-----|
| 2020.1.10 19:00 | `GET /v1/cross-margin/loan-info` | Update | Added new field for actual interest rate post deduction |
| 2020.1.7 19:00 | `GET /v1/account/history` | Update | Allowed sub user to call this endpoint |
| 2019.12.27 19:00 | `POST /v2/sub-user/management` | New | Added "Lock/Unlock Sub User" endpoint |
| 2019.12.27 19:00 | `POST /v1/order/orders/batchcancel` | Update | Support cancel based on client order id |
| 2019.12.27 19:00 | `POST /v1/order/batch-orders` | New | Added creating batch orders endpoint |
|2019.12.23 15:00| `market.$symbol.mbp.$levels` |New|Added MBP subscription topic|
|2019.12.05 11:00| `trade.clearing#${symbol}` & `accounts.update#${mode}`  |New|Added new subscription topic for trade updates and account change updates|
| 2019.11.22 15:00 | `GET /v1/order/orders`<br />`GET /v1/order/history` | Update | The query time range of canceled order is shortened to the last 1 day |
| 2019.11.13 19:00 | `GET /v1/margin/loan-info`<br />`GET /v1/cross-margin/loan-info` | New | Added loan interest and amount query |
|2019.11.08 19:45| `GET /v1/order/orders/{order-id}/matchresult`<br />`GET /v1/order/matchresults` |New|Added response field `trade-id`|
|2019.10.18 19:00| `GET /v1/account/history` |New|Added account history querying|
|2019.10.12 11:00| `POST /v1/dw/withdraw/api/create` |Update|Adjusted ERC20 as default chain for USDT|
|2019.10.11 10:00| Cross margin related |New|Added cross margin trading|
|2019.10.09 20:00| `GET /market/trade`<br />`GET /market/history/trade`<br />`market.$symbol.trade.detail` |Update|Added new response field "trade id"|
|2019.09.25 20:00| `GET /v2/account/withdraw/quota` |New|Added withdraw quota querying|
|2019.09.23 15:00| `POST /v1/order/orders/{order-id}/submitcancel`<br />`POST /v1/order/orders/batchcancel` |Update|Optimized error message|
|2019.09.20 10:00| `GET /v2/reference/currencies` |New|Added querying reference information of currency and chains|
|2019.09.19 16:00| `market.$symbol.bbo` |New|Added  best bid/offer update in tick by tick mode|
|2019.09.18 20:00| `GET /v1/subuser/aggregate-balance`<br />`GET /v1/account/accounts/{sub-uid}`<br />`GET /v1/margin/loan-orders`<br />`GET /v1/margin/accounts/balance` |New|Added sub account isolated margin trading|
|2019.09.16 15:00| `GET /v2/account/deposit/address` |New|Added deposit address querying|
|2019.09.11 17:00| `GET v1/stable-coin/quote`<br />`POST v1/stable-coin/exchange` |New|Added stable coin exchange|
|2019.09.11 16:00| N/A |Delete|Removed part of code demo.|
|2019.09.10 10:00| Order related API Except `POST /v1/order/orders/submitCancelClientOrder` & `GET /v1/order/openOrders` |Update|Removed order state values `submitting` and `cancelling`|
|2019.09.09 11:00| `POST /v1/order/orders/submitCancelClientOrder` |Update|Revised response message detail|
|2019.09.09 10:00| `GET /v1/order/orders`<br />`GET /v1/order/matchresults` |Update|Revised description of default value and value range for "start-date" and "end-date"|
|2019.09.02 18:00| `POST /v1/order/orders/batchCancelOpenOrders` |Update|Revised description of request field `symbol` |
|2019.09.02 16:00|"Stable Coin Exchange" related |Delete|Deleted "Stable Coin Exchange" relavant API|
|2019.08.29 21:00| Order related|New|Add stop-limit order classification|
|2019.08.21 18:00| `GET /v1/order/openOrders` |Update|Corrected query parameters|
|2019.08.05 18:00| `orders.$symbol.update` |New|Added new fileds "client-order-id" and "order-type"。|
|2019.08.02 18:00| `orders.$symbol.update` |Update|Revised the description of field "unfilled-amount"|
|2019.07.23 21:00| `GET /v1/order/orders/{order-id}/matchresult`<br />`GET /v1/order/matchresults` |New|Added transaction fee deduction details|
|2019.07.23 20:00| `GET /v1/fee/fee-rate/get` |New|Added transaction fee rate |
|2019.07.22 12:00| `GET /v1/order/orders/{order-id}/matchresults`<br />`GET /v1/order/matchresults` |New|Added new fields `role` to indicate the order was "taker" or "maker"|
|2019.07.11 20:00| `POST /v1/order/orders/place`<br />`POST /v1/order/orders/submitCancelClientOrder`<br />`GET /v1/order/orders/getClientOrder` |Update<br />New|Support client order ID。|
|2019.07.08 12:00| Websocket Asset and order topics|Update|Enhanced Websocket heartbeat and rate limit|
|2019.06.14 16:00| `POST /v1/dw/withdraw/api/create` |Update|support 'fast withdraw' |
|2019.06.17 16:00| `GET /v1/stable_coin/exchange_rate`<br />`POST /v1/stable_coin/exchange` |New| Support user query Stable Coin exchange rate, and perform exchange |
|2019.06.12 16:00| `GET /v1/common/symbols` |Update|Add more reference information of a symbol|
|2019.06.06 18:00| `GET /v1/query/deposit-withdraw` |Update|Ehanced the request parameters|
|2019.06.05 20:00| All APIs that need authentication|Update|Set up 3 permission for API Key: Read, Trade and Withdraw|
|2019.06.10 00:00| `GET /v1/order/orders`<br />`GET /v1/order/matchresults` |Update|Adjusted query window as 48 hours|
|2019.05.15 10:00| `POST /v1/futures/transfer` |New|Allow a user to tranfer fund between spot account and future contract account.|
|2019.04.29 19:00| `GET /v1/order/history` |New|Support historical order querying within 48 hours. With the launching of this new endpoint, the existing REST endpoint “v1/order/orders” will be kept in service. However, the new endpoint “/v1/order/history” will have better service level than the “/v1/order/orders”, especially when the service loading exceeds the threshold of our system, which means in some extremely cases, “v1/order/orders” would become unavailable, but “/v1/order/history” would be kept alive. Meanwhile, Huobi is planning to have a delegated data service to support users’ demands on long-term history data. Once this new service become available, the “v1/order/orders” will be deprecated. We will keep you informed promptly once the timeline determined.|
|2019.04.17 10:00| `GET /v1/order/orders` |Update|Add clarification on the value range for start-date in documents|
| 2019.04.16 10:00 | `GET /v1/order/openOrders` |Update| Correct the documents error. Both account-id and symbol are required |
| 2019.01.17 07:00 | Websocket accounts           |Update| Add subscription parameter model<br>Subscription does not return frozen balance of sub-account anymore |
| 2018.07.10 11:00 | `GET /market/history/kline`  |Update| The size parameter value range changes from [1-1000] to [1-2000]|
| 2018.07.06 16:00 | `POST /v1/order/orders/place` |Update| Added buy-limit-maker and sell-limit-maker order types|
| 2018.07.06 16:00 | `GET /v1/order/openOrders`<br>`POST /v1/order/orders/batchCancelOpenOrders` | New | Added open orders query<br />Added batch cancel open orders |
| 2018.07.02 16:00 | ETF related | New | Support transfer in/out of HB10.|
| 2018.06.20 16:00 | `GET /market/tickers` | New | Added tickers query |

# Introduction

## API Introduction

Welcome to Huobi API！  

This is the official Huobi API document, and will be continue updating, please follow us to get latest news.

You can switch to different API business in the top menu, and switch to different language by clicking the button in the top right.

The example of request and response is showing in the right hand side.

## Market Maker Program

It is very welcome for market maker who has good market making strategy and large trading volume. If your Huobi Spot account or Contract account has at least 10 BTC, you can send your email to:

- [MM_service@huobi.com](mailto:MM_service@huobi.com) for Huobi Global (spot / leverage) market maker
- [dm_mm@huobi.com](mailto:dm_mm@huobi.com) for Huobi Contract market maker

And provide below details:

1. UID (not linked to any rebate program in any accounts)
2. Screenshot of trading volume in other transaction platform (such as trading volume within 30 days, or VIP status)
3. A brief description of your market-making strategy 

<aside class="notice">
Market makers will not be able to use point cards, VIP rate, rebate or any other fee promotion.
</aside>

## Subscription

Huobi will publish API announcement in advance for any API change, please subscribe our announcements so that you can get latest update. 

You can click <a href='https://huobiglobal.zendesk.com/hc/en-us/sections/360000070201-API-Announcements'>Here</a> to subscribe the announcements. 

How to subscribe: Login to API Announcements page, click "Follow" button in the top right of the page, then choose the type you want to follow. After you subscribe, the button will changed to "Following". If you don't have any account, you need to register first. 

## Contact Us

If you have any other questions on API, you can contact us by below ways:

- Join official QQ group (火币网API交流群(8), 595882031), please tell your UID and programming language in your join request.
- Send email to api_service@huobi.com.

# Quick Start

## Preparation

Before you use API, you need to login the website to create API Key with proper permissions.

You can manage your API Key <a href='https://www.hbg.com/zh-cn/apikey/'>here</a>.

Every user can create at most 5 API Key, each of them has three permissions:

- Read permission: It is used to query the data, such as order query, trade query.
- Trade permission: It is used to create order, cancel order and transfer, etc.
- Withdraw permission: It is used to create withdraw order, cancel withdraw order, etc.

Please remember below information after creation:

- `Access Key`  It is used in API request
  
- `Secret Key`  It is used to generate the signature (only visible once after creation)

<aside class="notice">
The API Key can bind one or more IP addresses, we strongly suggest you bind IP address for security purpose. The API Key without IP binding will be expired after 90 days.
</aside>
<aside class="warning">
<red><b>Warning</b></red>: These two keys are important to your account safety, please don't share <b>both</b> of them together to anyone else. If you find your API Key is disposed, please remove it immediately.
</aside> 

## SDK and Demo

**SDK (Suggested)**

[Java](https://github.com/huobiapi/huobi_Java)

[Python3](https://github.com/huobiapi/huobi_Python)

[C++](https://github.com/huobiapi/huobi_Cpp)

**其它代码示例**

https://github.com/huobiapi?tab=repositories

## Interface Type

There are two types of interface, you can choose the proper one according to your scenario and preferences.

### REST API

REST (Representational State Transfer) is one of the most popular communication mechanism under HTTP, each URL represents a type of resource.

It is suggested to use Rest API for one-off operation, like trading and withdraw.

### WebSocket API

WebSocket is a new protocol in HTML5. It is full-duplex between client and server. The connection can be established by a single handshake, and then server can push the notification to client actively.

It is suggest to use WebSocket API to get data update, like market data and order update.

**Authentication**

Both API has two levels of authentication:

Public API: It is for basic information and market data. It doesn't need authentication.

Private API: It is for account related operation like trading and account management. Each private API must be authenticated with API Key.

## Access URLs
You can compare the network latency between two domain <u>api.huobi.pro</u> and <u>api-aws.huobi.pro</u>, and then choose the better one for you.

In general, the domain <u>api-aws.huobi.pro</u> is optimized for AWS client, the latency will be lower.

**REST API**

**`https://api.huobi.pro`**  

**`https://api-aws.huobi.pro`**  

**Websocket Feed (market)**

**`wss://api.huobi.pro/ws`**  

**`wss://api-aws.huobi.pro/ws`**  

**Websocket Feed (account and order)**

**`wss://api.huobi.pro/ws/v1`**  

**`wss://api-aws.huobi.pro/ws/v1`**     

<aside class="notice">
Please initiate API calls with non-China IP.
</aside>
<aside class="notice">
It is not recommended to use proxy to access Huobi API because it will introduce high latency and low stability.
</aside>
<aside class="notice">
It is recommended to access Huobi API from AWS Japan for better stability. If your server is in China mainland, it may be not stable.
</aside> 

## Authentication

### Overview

The API request may be tampered during internet, therefore all private API must be signed by your API Key (Secrete Key).

Each API Key has permission property, please check the API permission, and make sure your API key has proper permission.

A valid request consists of below parts:

- API Path: for example <u>api.huobi.pro/v1/order/orders</u>
- API Access Key: The 'Access Key' in your API Key
- Signature Method: The Hash method that is used to sign, it uses **HmacSHA256**
- Signature Version: The version for the signature protocol, it uses **2**
- Timestamp: The UTC time when the request is sent, e.g. 2017-05-11T16:22:06. It is useful to prevent the request to be intercepted by third-party.
- Parameters: Each API Method has a group of parameters, you can refer to detailed document for each of them. 
  - For GET request, all the parameters must be signed.
  - For POST request, the parameters needn't be signed and they should be put in request body.
- Signature: The value after signed, it is guarantee the signature is valid and the request is not be tempered.

### Signature Method

The signature may be different if the request text is different, therefore the request should be normalized before signing. Below signing steps take the order query as an example:

This is a full URL to query one order:

`https://api.huobi.pro/v1/order/orders?`

`AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx`

`&SignatureMethod=HmacSHA256`

`&SignatureVersion=2`

`&Timestamp=2017-05-11T15:19:30`

`&order-id=1234567890`

#### 1. The request Method (GET or POST), append line break “\n”


`GET\n`

#### 2. The host with lower case, append line break “\n”

`
api.huobi.pro\n
`

#### 3. The path, append line break “\n”

`
/v1/order/orders\n
`

#### 4. The parameters are URI encoded, and ordered based on ASCII

For example below is the original parameters:

`AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx`

`order-id=1234567890`

`SignatureMethod=HmacSHA256`

`SignatureVersion=2`

`Timestamp=2017-05-11T15%3A19%3A30`

<aside class="notice">
Use UTF-8 encoding and URI encoded, the hex must be upper case. For example, The semicolon ':' should be encoded as '%3A', The space should be encoded as '%20'.
</aside>
<aside class="notice">
The 'timestamp' should be formated as 'YYYY-MM-DDThh:mm:ss' and URI encoded.
</aside>

Then above parameter should be ordered like below:


`AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx`

`SignatureMethod=HmacSHA256`

`SignatureVersion=2`

`Timestamp=2017-05-11T15%3A19%3A30`

`order-id=1234567890`

#### 5. Use char  “&” to concatenate all parameters


`AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx&SignatureMethod=HmacSHA256&SignatureVersion=2&Timestamp=2017-05-11T15%3A19%3A30&order-id=1234567890`

#### 6. Assemble the pre-signed text

`GET\n`

`api.huobi.pro\n`

`/v1/order/orders\n`

`AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx&SignatureMethod=HmacSHA256&SignatureVersion=2&Timestamp=2017-05-11T15%3A19%3A30&order-id=1234567890`


#### 7. Use the pre-signed text and your Secret Key to generate a signature

- Use the pre-signed text in above step and your API Secret Key to generate hash code by HmacSHA256 hash function.
- Encode the hash code with base-64 to generate the signature.

`4F65x5A2bLyMWVQj3Aqp+B4w+ivaA7n5Oi2SuYtCJ9o=`

#### 8. Put the signature into request URL

- Put all the parameters in the URL
- Append the signature in the URL, with parameter name “Signature”.

Finally, the request sent to API should be:

`https://api.huobi.pro/v1/order/orders?AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx&order-id=1234567890&SignatureMethod=HmacSHA256&SignatureVersion=2&Timestamp=2017-05-11T15%3A19%3A30&Signature=4F65x5A2bLyMWVQj3Aqp%2BB4w%2BivaA7n5Oi2SuYtCJ9o%3D`

## Sub User

Sub user can be used to isolate the assets and trade, the assets can be transferred between parent and sub users. Sub user can only trade with the sub user. The assets can not be transferred between sub users, only parent user has the transfer permission.  

Sub user has independent login password and API Key, they are managed under parent user in website.

Each parent user can create **200** sub user, each sub user can create at most **5** API Key, each API key can have two permissions: **read** and **trade**.

The sub user API Key can also bind IP address, the expiry policy is the same with parent user.

You can access <a href='https://account.hbg.com/en-us/subaccount/management'>here</a> to create and manage sub user.

The sub user can access all public API (including basic information and market data), below are the private APIs that sub user can access:

API|Description
----------------------|---------------------
[POST /v1/order/orders/place](#fd6ce2a756)	|Create and execute an order
[POST /v1/order/orders/{order-id}/submitcancel](#4e53c0fccd)	|Cancel an order
[POST /v1/order/orders/submitCancelClientOrder](#submit-cancel-for-an-order-based-on-client-order-id)	| Cancel an Order based on client order ID
[POST /v1/order/orders/batchcancel](#ad00632ed5)	|Cancel multiple orders
[POST /v1/order/orders/batchCancelOpenOrders](#open-orders)	|Cancel the open orders
[GET /v1/order/orders/{order-id}](#92d59b6aad)	|Query a specific order
[GET /v1/order/orders](#d72a5b49e7)	|Query orders with criteria
[GET /v1/order/openOrders](#95f2078356)	|Query open orders
[GET /v1/order/matchresults](#0fa6055598)	|Query the order matching result
[GET /v1/order/orders/{order-id}/matchresults](#56c6c47284)	|Query a specific order matching result
[GET /v1/account/accounts](#bd9157656f)	|Query all accounts in current user
[GET /v1/account/accounts/{account-id}/balance](#870c0ab88b)	|Query the specific account balance
[POST /v1/futures/transfer](#e227a2a3e8)	|Transfer with future account
[POST /v1/dw/transfer-in/margin](#0d3c2e7382)|Transfer from spot to margin account
[POST /v1/dw/transfer-out/margin](#0d3c2e7382)|Transfer from margin to spot account
[POST /v1/margin/orders](#48cca1ce88)|Request margin loan
[POST /v1/margin/orders/{order-id}/repay](#48aa7c8199)|Repay the debit for specific order
[GET /v1/margin/loan-orders](#e52396720a)|Query history loan orders
[GET /v1/margin/accounts/balance](#6e79ba8e80)|Query margin account balance
[GET /v1/account/history](#84f1b5486d)|Query account ledger

<aside class="notice">
All other APIs couldn't be accessed by sub user, otherwise the API will return “error-code 403”。
</aside>

## Glossary

### Trading symbols

The trading symbols are consist of base currency and quote currency. Take the symbol `BTC/USDT` as an example, `BTC` is the base currency, and `USDT` is the quote currency.  

### Account

The `account-id` defines the Identity for different business type, it can be retrieved from API `/v1/account/accounts` , where the `account-type` is the business types.
The types include:

* spot: Spot account
* otc: OTC account
* margin: Isolated margin account, the detailed currency type is defined in `subType`
* super-margin / cross-margin:  Cross-margin account
* point: Point card account
* minepool: Minepool account
* etf: ETF account

### Identity

The frequently used Identities are listed below:

* order-id: The unique identity for order.
* client-order-id: The identity that defined by client. This id is included in order creation request, and will be returned as order-id. This id is valid within 24 hours.
* match-id : The identity for order matching.
* trade-id : The unique identity for the trade.

### Order Type
The order type is consist of trade direction and order classification. Take `buy-market` as an example, the trade direction is `buy`, the operation type is `market`.  

Trade direction includes:

* buy
* sell  

Order classification includes:

* limit: Both of the price and amount should be specified in order creation request.
* market : The price is not required in order creation request, you only need to specify either money or amount. The matching and trade will happen automatically according to the request.
* limit-maker: The price is specified in order creation request as market maker. It will not be matched in the matching queue.
* ioc: ioc stands for "immediately or cancel", it means the order will be canceled if it couldn't be matched. If the order is partially traded, the remaining part will be canceled.
* stop-limit: The price in order creation request is the trigger price. The order will be put into matching queue only when the market price reaches the trigger price.

### Order Status

* submitted: The order is submitted, and already in the matching queue, waiting for deal.
* partial-filled: The order is already in the matching queue and partially traded, and is waiting for further matching and trade.
* filled: The order is already traded and not in the matching queue any more.
* partial-canceled: The order is not in the matching queue any more. The status is transferred from 'partial-filled', the order is partially trade, but remaining is canceled.
* canceled: The order is not in the matching queue any more, and completely canceled. There is no trade associated with this order.
* canceling: The order is under canceling, but haven't been removed from matching queue yet.

You can refer to <a href='https://www.huobi.com/en-us/guide/'>Huobi Course</a> to get detailed information

# API Access

## Overview

Category| URL Path | Description 
--------- | --------- | -----------
Common |/v1/common/* | Common interface, including currency, currency pair, timestamp, etc 
Market Data |/market/*| Market data interface, including trading, depth, quotation, etc 
Account |/v1/account/*  /v1/subuser/* | Account interface, including account information, sub-account ,etc 
Order |/v1/order/* | Order interface, including order creation, cancellation, query, etc 
Margin|/v1/margin/* | Margin interface, including debit, payment, query, etc 
Cross Margin| /v1/cross-margin/* | Cross margin interface, including debit, payment, query, etc 

Above is a general category, it doesn't cover all API, you can refer to detailed API document according to your requirement.

## Rate Limiting Rule

* Each API Key is limited to 10 times per second
* If API Key is empty in request, then each IP is limited to 10 times per second

For example

* Order interface is limited by API Key: no more than 10 times within 1 sec
* Market data interface is limited by IP: no more than 10 times within 1 sec

## Request Format

The API is restful and there are two method: GET and POST.

* GET request: All parameters are included in URL
* POST request: All parameters are formatted as JSON and put int the request body

## Response Format

The response is JSON format.There are four fields in the top level: `status`, `ch`, `ts` and `data`. The first three fields indicate the general status, the business data is is under `data` field.

Below is an example of response:

```json
{
  "status": "ok",
  "ch": "market.btcusdt.kline.1day",
  "ts": 1499223904680,
  "data": // per API response data in nested JSON object
}
```

Field| Data Type | Description 
--------- | --------- | -----------
status    | string    | Status of API response 
ch        | string    | The data stream. It may be empty as some API doesn't have data stream 
ts        | int       | The UTC timestamp when API respond, the unit is millisecond 
data      | object    | The body data in response 

## Error Message

### Market Data  API Error Message

| Error Message | Description |
|-----|-----|
| bad-request | The request is wrong |
| invalid-parameter | The parameter is invalid |
| invalid-command | The command is invalid |
### Order API Error Message

| Error Message | Description |
|-----|-----|
| base-symbol-error | Trade pair doesn't exist |
| base-currency-error | Currency doesn't exist |
| base-date-error | The date format is wrong |
| account for id `12,345` and user id `6,543,210` does not exist| The`account-id` is wrong, please use GET `/v1/account/accounts` to get account |
| account-frozen-balance-insufficient-error | Can not froze due to insufficient balance |
| account-transfer-balance-insufficient-error | Can not transfer due to insufficient balance |
| bad-argument | The arugment is wrong |
| api-signature-not-valid | The API signature is wrong |
| gateway-internal-error | System is too busy |
| ad-ethereum-addresss| The Ethereum address is required |
| order-accountbalance-error| Insufficient balance in account |
| order-limitorder-price-error|The limited order price exceeds limitation |
|order-limitorder-amount-error|The limited order amount exceeds limitation |
|order-orderprice-precision-error|The limited order price exceeds precision limitation |
|order-orderamount-precision-error|The limited order amount exceeds precision limitation|
|order-marketorder-amount-error|The order amount exceeds limitation|
|order-queryorder-invalid|Can not query the order|
|order-orderstate-error|The order status is wrong|
|order-datelimit-error|The query exceeds date limitation|
|order-update-error|The order fail to update|

## Suggestions

1. To get market data: Use WebSocket to subscribe the real time data and cache the data for further usage
2. To get latest trade price: Use `/market/trade` or WebSocket to subscribe `market.$symbol.trade.detail`.
3. To get successful transaction: Use WebSocket to subscribe `orders.$symbol.update`, it has better performance and time-ordered.
4. To change account assents: Use WebSocket to subscribe accounts topic, and regularly call API to get latest data.

# Frequently Asked Questions

## API Announcements
Huobi will publish API announcement in advance for any API change, please subscribe our announcements so that you can get latest update. 

How to subscribe: Login to [API Announcements page](https://huobiglobal.zendesk.com/hc/en-us/sections/360000070201-API-Announcements), click "Follow" button in the top right of the page, then choose the type you want to follow. After you subscribe, the button will changed to "Following". If you don't have any account, you need to register first. 

## Access and Authentication

### Q1：How many API Keys one user can apply?
A:  Every user can create 5 API Keys, and each API Key can be granted with 3 permissions: **read**, **trade** and **withdraw**.
Each user could create up to 200 sub users, and each sub user could create 5 API Keys, each API key can be granted with 2 permissions: **read** and **trade**.

Below are the explanation for permissions:

1、Read permission: It is used to query data, for example, **query orders**, **query trades**. 

2、Trade permission: it is used to **place order**, **cancel order** and **transfer**.

3、Withdraw permission: it is used to **withdraw**, **cancel withdraw**.

### Q2：Why APIs are always disconnected or timeout?
A：Please follow below suggestions:

1、It is unstable if the client's server locates in China mainland, it is suggested to invoke API from a server at AWS Japan.

2、It is suggested to invoke API only to host <u>api.huobi.pro</u> or <u>api-was.huobi.pro</u>.

### Q3：Why the WebSocket is often disconnected?
A：Please check below possible reasons:

1、The client didn't respond 'Pong'. It is requird to respond 'Pong' after receive 'Ping' from server.

2、The server didn't receive 'Pong' successfully due to network issue.

3、The connection is broken due to network issue.

4、It is suggested to implement WebSocket re-connect mechanism. If Ping/Pong works well but the connection is broken, the application should be able to re-connect automatically.

### Q4：What is the difference between <u>api.huobi.pro</u> and <u>api-aws.huobi.pro</u>?
A：The host <u>api-aws.huobi.pro</u> is optimized for AWS client, the latency is lower.

### Q5：Why the signature authentication always fail?
A：Please compare  your signature text with below example: 

`GET\n`

`api.huobi.pro\n`

`/v1/account/accounts\n`

`AccessKeyId=rfhxxxxx-950000847-boooooo3-432c0&SignatureMethod=HmacSHA256&SignatureVersion=2&Timestamp=2019-10-28T07%3A28%3A38`

Please check whether you follow below rules:

1、The parameter in signature text should be ordered by ASCII, for example below is the original parameters:

`AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx`

`order-id=1234567890`

`SignatureMethod=HmacSHA256`

`SignatureVersion=2`

`Timestamp=2017-05-11T15%3A19%3A30`

They should be ordered like below:

`AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx`

`SignatureMethod=HmacSHA256`

`SignatureVersion=2`

`Timestamp=2017-05-11T15%3A19%3A30`

`order-id=1234567890`

2、The signature text should be URI encoded, for example

- The semicolon `:`should be encoded as `%3A`, The space should be encoded as `%20`.
- The timestamp should be formatted as `YYYY-MM-DDThh:mm:ss` and after encoded it should be like `2017-05-11T15%3A19%3A30`  

3、The signature should be base64 encoded.

4、The parameter for Get request should be included in signature request.

5、The Timestamp should be UTC time and the format should be YYYY-MM-DDTHH:mm:ss.

6、The time difference between your timestamp and standard should be less than 1 minute.

7、The message body doesn't need URI encoded if you are using WebSocket for authentication.

8、The host in signature text should be the same as the host in your API request.

9、The hidden text in API Key and Secret Key may have impact on the signature.

Right now the official SDK supports 3 language: Java, Python3 and C++, you can choose the one that suitable for you. 

<a href='https://github.com/HuobiRDCenter'>Download SDK </a>    

<a href='https://github.com/HuobiRDCenter/huobi_Python/blob/master/example/python_signature_demo.md'>Python signature example</a>   

<a href='https://github.com/HuobiRDCenter/huobi_Java/blob/master/java_signature_demo.md'>JAVA signature example</a>   

<a href='https://github.com/HuobiRDCenter/huobi_Cpp/blob/master/examples/cpp_signature_demo.md'>C++ signature example</a>   

### Q6：Why the API return 'gateway-internal-error'?
A：Please check below possible reasons:

1、Check the `account-id`, it could be returned from `GET /v1/account/accounts`.

2、It may be due to network issue, please try again later.

3、The data format should be correct (standard JSON).

4、The `Content-Type` in POST header should be `application/json` .

### Q7：Why the API return 'login-required'?
A：Please check below possible reasons:

1、The parameter should include `AccessKeyId`.

2、Check the `account-id` it could be returned from `GET /v1/account/accounts`.

3、The request body in POST request should NOT be included in signature text.

4、The request parameter in GET request should be ordered by ASCII.

## Market Data

### Q1：What is the update frequency of market depth?
A：The data is updated **once per second**. But, the BBO (Best Bid/Offer) feed upon WebSocket subscription to `market.$symbol.bbo` is updating in tick by tick mode.

### Q2：Could the total volume of Last 24h Market Summary (GET /v1/market/detail) decrease?
A：Yes, it is possible that the accumulated volume and the accumulated value counted for current 24h window is smaller than previous.

### Q3：How to retrieve the last trade price in market?
A：It is suggested to request to `GET /v1/market/trade` to get last market price, or to subscribe WebSocket topic `market.$symbol.trade.detail` for getting the same.

### Q4：Which timezone the start time of candlesticks falls into?
A： The start time for candlesticks is based on Singapore time (GMT+8), for example, the duration for daily candlesticks is from 00:00:00 to 23:59:59 Singapore time.

## Order and Trade

### Q1：What is account-id?
A： The `account-id` defines the Identity for different business type, it can be retrieved from API `/v1/account/accounts` , where the `account-type` is the business types.

The types include:

- spot: Spot account
- otc: OTC account
- margin: Isolated margin account, the detailed currency type is defined in `subType`
- super-margin / cross-margin:  Cross-margin account
- point: Point card account
- minepool: Minepool account
- etf: ETF account

### Q2：What is client-order-id?
A： The `client-order-id` is an optional request parameter while placing order. It's string type which maximum length is 64. The client order id is generated by client, and is only valid within 24 hours.

### Q3：How to get the order size, price and decimal precision?
A： You can call API `GET /v1/common/symbols` to get the currency pair information, pay attention to the difference between the minimum amount and the minimum price.   

Below are common errors:

- order-value-min-error: The order price is less than minimum price
- order-orderprice-precision-error : The precision for limited order price is wrong 
- order-orderamount-precision-error : The precision for limited order amount is wrong
- order-limitorder-price-max-error : The limited order price is higher than the threshold
- order-limitorder-price-min-error : The limited order price is lower than the threshold
- order-limitorder-amount-max-error : The limited order amount is larger than the threshold
- order-limitorder-amount-min-error : The limited order amount is smaller than the threshold  

### Q4：What is the difference between two WebSocket topic 'orders.\$symbol' and 'orders.\$symbol.update'?
A： Below are the difference:

1、The topic `order.$symbol` is the legacy version, which will be no longer supported in the near future. It is strongly recommended to subscribe topic `orders.$symbol.update` instead for getting order updates.

2、The update message sequence of `orders.$symbol.update` strictly follows transaction time, with lower latency.

3、In order to reduce latency, the topic `orders.$symbol.update` doesn't include original order details and transaction fee etc. If you require the original order information or transaction fee details, you may query to corresponding REST API endpoint.

### Q5：Why I got insufficient balance error while placing an order just after a successful order matching?
A：The time order matching update being sent down, the clearing service of that order may be still in progress at backend. Suggest to follow either of below to ensure a successful order submission:

1、Subscribe to WebSocket topic `accounts` for getting account balance moves to ensure the completion of asset clearing.

2、Check account balance from REST endpoint to ensure sufficient available balance for the next order submission.

3、Leave sufficient balance in your account.

### Q6: What is the difference between 'filled-fees' and 'filled-points' in match result?
A: Transaction fee can be paid from either of below.

1、filled-fees: Filled-fee is also called transaction fee. It's charged from your income currency from the transaction. For example, if your purchase order of BTC/USDT got matched，the transaction fee will be based on BTC.

2、filled-points: If user enabled transaction fee deduction, the fee should be charged from either HT or Point. User could refer to field `fee-deduct-currency` to get the exact deduction type of the transaction.

### Q7: What is the difference between 'match-id' and 'trade-id' in matching result?
A: The `match-id` is the identity for order matching, while the `trade-id` is the unique identifier for each trade. One `match-id` may be correlated with multiple `trade-id`, or no `trade-id`(if the order is cancelled). For example, if a taker's order got matched with 3 maker's orders at the same time, it generates 3 trade IDs but only one match ID.

### Q8: Why the order submission could be rejected even though the order price is set as same as current best bid (or best ask)?
A: For some extreme illiquid trading symbols, the best quote price at particular time might be far away from last trade price. But the price limit is actually based on last trade price which could possibly exclude best quote price from valid range for any new order.

### Q9: How to retrieve the trading symbols for margin trade

A: You can get details from Rest API ` GET /v1/common/symbols`. The `leverage-ratio` represents the isolated-margin ratio. The `super-margin-leverage-ratio` represents the cross-margin.

The value `0` indicates that the trading symbols doesn't support margin trading.

## Deposit and Withdraw

### Q1：Why the API returns error 'api-not-support-temp-addr' when withdrawing?
A：User has to include the address into the pre-defined address table on Huobi official website before withdrawing through API.

### Q2：Why the API returns error 'Invaild-Address' when withdraw USDT?
A：USDT locates on multiple chains, therefore the withdraw order should clearly specify which chain the withdrawal goes to. See the table below:

| Chain           | Field Value |
| --------------- | --------------- |
| ERC20 (default) | `usdterc20`     |
| OMNI            | `usdt`          |
| TRX             | `trc20usdt`     |

If leaving the field empty, default target chain is `ERC20`, or you can explicitly set the chain to `usdterc20`.

If the target chain is `OMNI` or `TRX`, the field value should be `usdt` or `trc20usdt`.

The full chain name list for all currencies can be retrieved from endpoint `GET /v2/reference/currencies`.

### Q3：How to specify 'fee' when creating a withdraw request?

A：Please refer to the response from endpoint `GET /v2/reference/currencies`, where the field `withdrawFeeType` defining different fee types below: 

- transactFeeWithdraw : The withdraw fee per request (only applicable when withdrawFeeType=fixed).    	
- minTransactFeeWithdraw : The minimum withdraw fee per request (only applicable when withdrawFeeType=circulated).
- maxTransactFeeWithdraw : The maximum withdraw fee per request (only applicable when withdrawFeeType=circulated or ratio).
- transactFeeRateWithdraw : The withdraw fee rate per request (only applicable when withdrawFeeType=ratio).

### Q4：How to query my withdraw quota?
A：Please refer to the response from endpoint `GET /v2/account/withdraw/quota`, where quota per request, daily quota, annual quota, overall quota are available.

Note: If you need to withdraw large amount which breaking the limitation, you can contact our official support (support@huobi.pro) for assistance.

## API Technical Support
If you have any other questions on API, you can contact us by below ways:

1、Join official QQ group (火币网API交流群(8), 595882031), please tell your UID and programming language in your join request.

2、Send email to api_service@huobi.com
In order to better understand your question and respond you quickly, please use below template in your email:

`1. UID`  
`2. AccessKey`  
`3. Full URL request`  
`4. Request parameters`  
`5. Request time`  
`6. Original response`  
`7. Problem description: (such as steps, field question, frequency)`  
`8. Signature text (mandatory if you have signature authentication issue)`  

Below is an example：

`1. UID：123456`  
`2. AccessKey:rfhxxxxx-950000847-boooooo3-432c0`  
`3. Full URL request: https://api.huobi.pro/v1/account/accounts?&SignatureVersion=2&SignatureMethod=HmacSHA256&Timestamp=2019-11-06T03%3A25%3A39&AccessKeyId=rfhxxxxx-950000847-boooooo3-432c0&Signature=HhJwApXKpaLPewiYLczwfLkoTPnFPHgyF61iq0iTFF8%3D`  
`4. Request parameters: N/A`  
`5. Request time: 2019-11-06 11:26:14`  
`6. Original response：{"status":"error","err-code":"api-signature-not-valid","err-msg":"Signature not valid: Incorrect Access key [Access key错误]","data":null}`  
`7. Problem description: API returns error`  
`8. Signature text:`  
`GET\n`  
`api.huobi.pro\n`  
`/v1/account/accounts\n`    
`AccessKeyId=rfhxxxxx-950000847-boooooo3-432c0&SignatureMethod=HmacSHA256&SignatureVersion=2&Timestamp=2019-11-06T03%3A26%3A13`

Note：It is safe to share your Access Key, which is to prove your identity, and it will not affect your account safety. Remember do **not** share your `Secret Key` to any one. If you expose your `Secret Key` by accident, please [remove](https://www.hbg.com/zh-cn/apikey/) the related API Key immediately.

# Reference Data

## Get all Supported Trading Symbol

This endpoint returns all Huobi's supported trading symbol.

```shell
curl "https://api.huobi.pro/v1/common/symbols"
```

### HTTP Request

`GET /v1/common/symbols`

### Request Parameters

No parameter is needed for this endpoint.

> Responds:

```json
  "data": [
   {"base-currency":"etc",
    "quote-currency":"usdt",
    "price-precision":6,
    "amount-precision":4,
    "symbol-partition":"default",
    "symbol":"etcusdt",
    "state":"online",
    "value-precision":8,
    "min-order-amt":0.001,
    "max-order-amt":10000,
    "min-order-value":0.0001
    },
    {
    "base-currency":"ltc",
    "quote-currency":"usdt",
    "price-precision":6,
    "amount-precision":4,
    "symbol-partition":"main",
    "symbol":"ltcusdt",
    "state":"online",
    "value-precision":8,
    "min-order-amt":0.001,
    "max-order-amt":10000,
    "min-order-value":100,
    "leverage-ratio":4
    }
  ]
```

### Response Content

Field           | Data Type | Description
---------       | --------- | -----------
base-currency   | string    | Base currency in a trading symbol
quote-currency  | string    | Quote currency in a trading symbol
price-precision | integer   | Quote currency precision when quote price(decimal places)
amount-precision| integer   | Base currency precision when quote amount(decimal places)
symbol-partition| string    | Trading section, possible values: [main，innovation]
symbol          | string    | 
state           | string    | The status of the symbol；Allowable values: [online，offline,suspend]. "online" - Listed, available for trading, "offline" - de-listed, not available for trading， "suspend"-suspended for trading
value-precision | integer   | Precision of value in quote currency (value = price * amount)
min-order-amt   | long      | Minimum order amount (order amount is the ‘amount’ defined in ‘v1/order/orders/place’ when it’s a limit order or sell-market order)
max-order-amt   | long      | Max order amount
min-order-value | long      | Minimum order value (order value refers to ‘amount’ * ‘price’ defined in ‘v1/order/orders/place’ when it’s a limit order or ‘amount’ when it’s a buy-market order)
leverage-ratio  | int       | The applicable leverage ratio


## Get all Supported Currencies

This endpoint returns all Huobi's supported trading currencies.

```shell
curl "https://api.huobi.pro/v1/common/currencys"
```

### HTTP Request

`GET /v1/common/currencys`

### Request Parameters

No parameter is needed for this endpoint.

> Response:

```json
  "data": [
    "usdt",
    "eth",
    "etc"
  ]
```

### Response Content

<aside class="notice">The returned "data" field contains a list of string with each string represents a suppported currency.</aside>
## APIv2 - Currency & Chains

API user could query static reference information for each currency, as well as its corresponding chain(s). (Public Endpoint)

### HTTP Request

`GET https://api.huobi.pro/v2/reference/currencies`

```shell
curl "https://api.huobi.pro/v2/reference/currencies?currency=usdt"
```

### Request Parameters

| Field Name       | Mandatory | Data Type     | Description     |Value Range |
| ---------- | ---- | ------ | ------ | ---- |
| currency | false | string | Currency   |  btc, ltc, bch, eth, etc ...(available currencies in Huobi Global) |
| authorizedUser | false | boolean | Authorized user   |  true or false (if not filled, default value is true) |

> Response:

```json
{
    "code":200,
    "data":[
        {
            "chains":[
                {
                    "chain":"trc20usdt",
                    "depositStatus":"allowed",
                    "maxTransactFeeWithdraw":"1.00000000",
                    "maxWithdrawAmt":"280000.00000000",
                    "minDepositAmt":"100",
                    "minTransactFeeWithdraw":"0.10000000",
                    "minWithdrawAmt":"0.01",
                    "numOfConfirmations":999,
                    "numOfFastConfirmations":999,
                    "withdrawFeeType":"circulated",
                    "withdrawPrecision":5,
                    "withdrawQuotaPerDay":"280000.00000000",
                    "withdrawQuotaPerYear":"2800000.00000000",
                    "withdrawQuotaTotal":"2800000.00000000",
                    "withdrawStatus":"allowed"
                },
                {
                    "chain":"usdt",
                    "depositStatus":"allowed",
                    "maxWithdrawAmt":"19000.00000000",
                    "minDepositAmt":"0.0001",
                    "minWithdrawAmt":"2",
                    "numOfConfirmations":30,
                    "numOfFastConfirmations":15,
                    "transactFeeRateWithdraw":"0.00100000",
                    "withdrawFeeType":"ratio",
                    "withdrawPrecision":7,
                    "withdrawQuotaPerDay":"90000.00000000",
                    "withdrawQuotaPerYear":"111000.00000000",
                    "withdrawQuotaTotal":"1110000.00000000",
                    "withdrawStatus":"allowed"
                },
                {
                    "chain":"usdterc20",
                    "depositStatus":"allowed",
                    "maxWithdrawAmt":"18000.00000000",
                    "minDepositAmt":"100",
                    "minWithdrawAmt":"1",
                    "numOfConfirmations":999,
                    "numOfFastConfirmations":999,
                    "transactFeeWithdraw":"0.10000000",
                    "withdrawFeeType":"fixed",
                    "withdrawPrecision":6,
                    "withdrawQuotaPerDay":"180000.00000000",
                    "withdrawQuotaPerYear":"200000.00000000",
                    "withdrawQuotaTotal":"300000.00000000",
                    "withdrawStatus":"allowed"
                }
            ],
            "currency":"usdt",
            "instStatus":"normal"
        }
        ]
}

```

### Response Content


| Field Name | Mandatory  | Data Type | Description   | Value Range |
| ---- | ----- | ---- | ---- | ---- |
| code| true | int | Status code |      |
| message| false | string | Error message (if any) |      |
| data| true | object |  |      |
|   { currency | true | string | Currency |      |
|      { chains| true | object |  |      |
|        chain| true | string | Chain name |      |
|        numOfConfirmations| true | int | Number of confirmations required for deposit success (trading & withdrawal allowed once reached) |      |
|        numOfFastConfirmations| true | int | Number of confirmations required for quick success (trading allowed but withdrawal disallowed once reached) |      |
|        minDepositAmt| true | string | Minimal deposit amount in each request |      |
|        depositStatus| true | string | Deposit status | allowed,prohibited     |
|        minWithdrawAmt| true | string | Minimal withdraw amount in each request |      |
|        maxWithdrawAmt| true | string | Maximum withdraw amount in each request |      |
|        withdrawQuotaPerDay| true | string | Maximum withdraw amount in a day |      |
|        withdrawQuotaPerYear| true | string | Maximum withdraw amount in a year |      |
|        withdrawQuotaTotal| true | string |Maximum withdraw amount in total |      |
|        withdrawPrecision| true | int |Withdraw amount precision |      |
|        withdrawFeeType| true | string |Type of withdraw fee (only one type can be applied to each currency)| fixed,circulated,ratio     |
|        transactFeeWithdraw| false | string |Withdraw fee in each request (only applicable to withdrawFeeType = fixed) |      |
|        minTransactFeeWithdraw| false | string |Minimal withdraw fee in each request (only applicable to withdrawFeeType = circulated) |      |
|        maxTransactFeeWithdraw| false | string |Maximum withdraw fee in each request (only applicable to withdrawFeeType = circulated or ratio) |      |
|        transactFeeRateWithdraw| false | string |Withdraw fee in each request (only applicable to withdrawFeeType = ratio) |      |
|        withdrawStatus}| true | string | Withdraw status | allowed,prohibited     |
|      instStatus }| true | string | Instrument status | normal,delisted     |

### Status Code

| Status Code | Error Message  | Scenario |
| ---- | ----- | ---- |
| 200| success | Request successful |
| 500| error |  System error |
| 2002| invalid field value in "field name" | Invalid field value |

## Get Current Timestamp

This endpoint returns the current timestamp, i.e. the number of **milliseconds** that have elapsed since 00:00:00 **UTC** on 1 January 1970. 

```shell
curl "https://api.huobi.pro/v1/common/timestamp"
```

### HTTP Request

`GET /v1/common/timestamp`

### Request Parameters

No parameter is needed for this endpoint.

> Response:

```json
  "data": 1494900087029
```

### Response Content

The returned "Data" field contains an integer represents the timestamp in milliseconds adjusted to Singapore time.

# Market Data

## Get Klines(Candles)

This endpoint retrieves all klines in a specific range.

### HTTP Request

`GET https://api.huobi.pro/market/history/kline`

```shell
curl "https://api.huobi.pro/market/history/kline?period=1day&size=200&symbol=btcusdt"
```

### Query Parameters

Parameter | Data Type | Required | Default | Description                 | Value Range
--------- | --------- | -------- | ------- | -----------                 | -----------
symbol    | string    | true     | NA      | The trading symbol to query | All trading symbol supported, e.g. btcusdt, bccbtc
period    | string    | true     | NA      | The period of each candle   | 1min, 5min, 15min, 30min, 60min, 4hour, 1day, 1mon, 1week, 1year
size      | integer   | false    | 150     | The number of data returns  | [1, 2000]

<aside class="notice">This API doesn't support customized period, refer to Websocket K line API to get the emurated period value.</aside>
<aside class="notice">To query HB10, put "hb10" at symbol position.</aside>
<aside class="notice">The start time for candlesticks is based on Singapore time (GMT+8), for example, the duration for daily candlesticks is from 00:00:00 to 23:59:59 Singapore time.</aside>
> The above command returns JSON structured like this:

```json
"data": [
  {
    "id": 1499184000,
    "amount": 37593.0266,
    "count": 0,
    "open": 1935.2000,
    "close": 1879.0000,
    "low": 1856.0000,
    "high": 1940.0000,
    "vol": 71031537.97866500
  }
]
```

### Response Content

Field     | Data Type | Description
--------- | --------- | -----------
id        | integer   | The UNIX timestamp in seconds as response id
amount    | float     | The aggregated trading volume in USDT
count     | integer   | The number of completed trades
open      | float     | The opening price
close     | float     | The closing price
low       | float     | The low price
high      | float     | The high price
vol       | float     | The trading volume in base currency

## Get Latest Aggregated Ticker

This endpoint retrieves the latest ticker with some important 24h aggregated market data.

### HTTP Request

`GET https://api.huobi.pro/market/detail/merged`

```shell
curl "https://api.huobi.pro/market/detail/merged?symbol=ethusdt"
```

### Request Parameters

Parameter | Data Type | Required | Default | Description                  | Value Range
--------- | --------- | -------- | ------- | -----------                  | --------
symbol    | string    | true     | NA      | The trading symbol to query  | All supported trading symbol, e.g. btcusdt, bccbtc.Refer to `/v1/common/symbols` 

> The above command returns JSON structured like this:

```json
"data": {
  "id":1499225271,
  "ts":1499225271000,
  "close":1885.0000,
  "open":1960.0000,
  "high":1985.0000,
  "low":1856.0000,
  "amount":81486.2926,
  "count":42122,
  "vol":157052744.85708200,
  "ask":[1885.0000,21.8804],
  "bid":[1884.0000,1.6702]
}
```

### Response Content

Field     | Data Type | Description
--------- | --------- | -----------
id        | integer   | The internal identity 
amount    | float     | The aggregated trading volume in USDT
count     | integer   | The number of completed trades
open      | float     | The opening price of last 24 hours
close     | float     | The last price of last 24 hours
low       | float     | The low price of last 24 hours
high      | float     | The high price of last 24 hours
vol       | float     | The trading volume in base currency of last 24 hours
bid       | object    | The current best bid in format [price, quote volume]
ask       | object    | The current best ask in format [price, quote volume]

## Get Latest Tickers for All Pairs

This endpoint retrieves the latest tickers for all supported pairs.

<aside class="notice">The returned data object can contain large amount of tickers.</aside>
### HTTP Request

`GET https://api.huobi.pro/market/tickers`

```shell
curl "https://api.huobi.pro/market/tickers"
```

### Request Parameters

No parameters are needed for this endpoint.

> The above command returns JSON structured like this:

```json
"data": [  
    {  
        "open":0.044297,
        "close":0.042178,
        "low":0.040110,
        "high":0.045255,
        "amount":12880.8510,  
        "count":12838,
        "vol":563.0388715740,
        "symbol":"ethbtc"
    },
    {  
        "open":0.008545,
        "close":0.008656,
        "low":0.008088,
        "high":0.009388,
        "amount":88056.1860,
        "count":16077,
        "vol":771.7975953754,
        "symbol":"ltcbtc"
    }
]
```

### Response Content

Response content is an array of object, each object has below fields.

Field     | Data Type | Description
--------- | --------- | -----------
amount    | float     | The aggregated trading volume in USDT of last 24 hours
count     | integer   | The number of completed trades of last 24 hours
open      | float     | The opening price of last 24 hours
close     | float     | The last price of last 24 hours
low       | float     | The low price of last 24 hours
high      | float     | The high price of last 24 hours
vol       | float     | The trading volume in base currency of last 24 hours
symbol    | string    | The trading symbol of this object, e.g. btcusdt, bccbtc

## Get Market Depth

This endpoint retrieves the current order book of a specific pair.

### HTTP Request

`GET https://api.huobi.pro/market/depth`

```shell
curl "https://api.huobi.pro/market/depth?symbol=btcusdt&type=step1"
```

### Request Parameters

Parameter | Data Type | Required | Default Value         | Description                                       | Value Range
--------- | --------- | -------- | -------------         | -----------                                       | -----------
symbol    | string    | true     | NA                    | The trading symbol to query                       | Refer to `GET /v1/common/symbols` 
depth     | integer   | false    | 20                    | The number of market depth to return on each side | 5, 10, 20
type      | string    | true     | step0                 | Market depth aggregation level, details below     | step0, step1, step2, step3, step4, step5

<aside class="notice">when type is set to "step0", the default value of "depth" is 150 instead of 20.</aside>
**"type" Details**

Value     | Description
--------- | ---------
step0     | No market depth aggregation
step1     | Aggregation level = precision*10
step2     | Aggregation level = precision*100
step3     | Aggregation level = precision*1000
step4     | Aggregation level = precision*10000
step5     | Aggregation level = precision*100000

> The above command returns JSON structured like this:

```json
"tick": {
    "version": 31615842081,
    "ts": 1489464585407,
    "bids": [
      [7964, 0.0678],
      [7963, 0.9162],
      [7961, 0.1],
      [7960, 12.8898],
      [7958, 1.2],
      [7955, 2.1009],
      [7954, 0.4708],
      [7953, 0.0564],
      [7951, 2.8031],
      [7950, 13.7785],
      [7949, 0.125],
      [7948, 4],
      [7942, 0.4337],
      [7940, 6.1612],
      [7936, 0.02],
      [7935, 1.3575],
      [7933, 2.002],
      [7932, 1.3449],
      [7930, 10.2974],
      [7929, 3.2226]
    ],
    "asks": [
      [7979, 0.0736],
      [7980, 1.0292],
      [7981, 5.5652],
      [7986, 0.2416],
      [7990, 1.9970],
      [7995, 0.88],
      [7996, 0.0212],
      [8000, 9.2609],
      [8002, 0.02],
      [8008, 1],
      [8010, 0.8735],
      [8011, 2.36],
      [8012, 0.02],
      [8014, 0.1067],
      [8015, 12.9118],
      [8016, 2.5206],
      [8017, 0.0166],
      [8018, 1.3218],
      [8019, 0.01],
      [8020, 13.6584]
    ]
  }
```

### Response Content

<aside class="notice">The returned data object is under 'tick' object instead of 'data' object in the top level JSON</aside>
Field     | Data Type | Description
--------- | --------- | -----------
ts        | integer   | The UNIX timestamp in milliseconds adjusted to Singapore time
version   | integer   | Internal data
bids      | object    | The current all bids in format [price, quote volume]
asks      | object    | The current all asks in format [price, quote volume]


## Get the Last Trade

This endpoint retrieves the latest trade with its price, volume, and direction.

### HTTP Request

`GET https://api.huobi.pro/market/trade`

```shell
curl "https://api.huobi.pro/market/trade?symbol=ethusdt"
```

### Request Parameters

Parameter | Data Type | Required | Default Value         | Description                                       | Value Range
--------- | --------- | -------- | -------------         | -----------                                       | -----------
symbol    | string    | true     | NA                    | The trading symbol to query                       | Refer to `GET /v1/common/symbols`

> The above command returns JSON structured like this:

```json
"tick": {
    "id": 600848670,
    "ts": 1489464451000,
    "data": [
      {
        "id": 600848670,
        "trade-id": 102043494568,
        "price": 7962.62,
        "amount": 0.0122,
        "direction": "buy",
        "ts": 1489464451000
      }
    ]
}
```

### Response Content

<aside class="notice">The returned data object is under 'tick' object instead of 'data' object in the top level JSON</aside>
Parameter | Data Type | Description
--------- | --------- | -----------
id        | integer   | The unique trade id of this trade (to be obsoleted)
trade-id|integer| The unique trade id (NEW)
amount    | float     | The trading volume in base currency
price     | float     | The trading price in quote currency
ts        | integer   | The UNIX timestamp in milliseconds adjusted to Singapore time
direction | string    | The direction of the taker trade: 'buy' or 'sell'

## Get the Most Recent Trades

This endpoint retrieves the most recent trades with their price, volume, and direction.

### HTTP Request

`GET https://api.huobi.pro/market/history/trade`

```shell
curl "https://api.huobi.pro/market/history/trade?symbol=ethusdt&size=2"
```

### Request Parameters

Parameter | Data Type | Required | Default Value    | Description                   | Value Range
--------- | --------- | -------- | -------------    | ----------                    | -----------
symbol    | string    | true     | NA               | The trading symbol to query   | All supported trading symbol, e.g. btcusdt, bccbtc.Refer to `GET /v1/common/symbols`
size      | integer   | false    | 1                | The number of data returns    | [1, 2000]

> The above command returns JSON structured like this:

```json
"data": [  
   {  
      "id":31618787514,
      "ts":1544390317905,
      "data":[  
         {  
            "amount":9.000000000000000000,
            "ts":1544390317905,
            "id":3161878751418918529341,
            "trade-id": 102043495672,
            "price":94.690000000000000000,
            "direction":"sell"
         },
         {  
            "amount":73.771000000000000000,
            "ts":1544390317905,
            "id":3161878751418918532514,
            "trade-id": 102043495673,
            "price":94.660000000000000000,
            "direction":"sell"
         }
      ]
   },
   {  
      "id":31618776989,
      "ts":1544390311353,
      "data":[  
         {  
            "amount":1.000000000000000000,
            "ts":1544390311353,
            "id":3161877698918918522622,
            "trade-id": 102043495674,
            "price":94.710000000000000000,
            "direction":"buy"
         }
      ]
   }
}
```

### Response Content

<aside class="notice">The returned data object is an array represents one recent timestamp; each timestamp object again is an array represents all trades occurred at this timestamp.</aside>
Field     | Data Type | Description
--------- | --------- | -----------
id        | integer   | The unique trade id of this trade (to be obsoleted)
trade-id|integer| The unique trade id (NEW)
amount    | float     | The trading volume in base currency
price     | float     | The trading price in quote currency
ts        | integer   | The UNIX timestamp in milliseconds adjusted to Singapore time
direction | string    | The direction of the taker trade: 'buy' or 'sell'

## Get the Last 24h Market Summary

This endpoint retrieves the summary of trading in the market for the last 24 hours.

### HTTP Request

`GET https://api.huobi.pro/market/detail/`

```shell
curl "https://api.huobi.pro/market/detail?symbol=ethusdt"
```

### Request Parameters

Parameter | Data Type | Required | Default Value    | Description                   | Value Range
--------- | --------- | -------- | -------------    | ----------                    | -----------
symbol    | string    | true     | NA               | The trading symbol to query   | Refer to /v1/common/symbols

> The above command returns JSON structured like this:

```json
"tick": {  
   "amount":613071.438479561,
   "open":86.21,
   "close":94.35,
   "high":98.7,
   "id":31619471534,
   "count":138909,
   "low":84.63,
   "version":31619471534,
   "vol":5.6617373443873316E7
}
```

### Response Content

<aside class="notice">The returned data object is under 'tick' object instead of 'data' object in the top level JSON</aside>
Field     | Data Type | Description
--------- | --------- | -----------
id        | integer   | The internal identity 
amount    | float     | The aggregated trading volume in USDT
count     | integer   | The number of completed trades
open      | float     | The opening price of last 24 hours
close     | float     | The last price of last 24 hours
low       | float     | The low price of last 24 hours
high      | float     | The high price of last 24 hours
vol       | float     | The trading volume in base currency of last 24 hours
version   | integer   | Internal data


# Account

<aside class="notice">All endpoints in this section require authentication</aside>
## Get all Accounts of the Current User

API Key Permission：Read

This endpoint returns a list of accounts owned by this API user.

### HTTP Request

`GET https://api.huobi.pro/v1/account/accounts`

```shell
curl "https://api.huobi.pro/v1/account/accounts"
```

### Request Parameters

<aside class="notice">No parameter is available for this endpoint</aside>
> The above command returns JSON structured like this:

```json
  "data": [
    {
      "id": 100009,
      "type": "spot",
      "subtype": "",
      "state": "working"
    }
  ]
```

### Response Content

Field               | Data Type | Description              | Value Range
---------           | --------- | -----------              | -----------
id                  | integer   | Unique account id        | NA
state               | string    | Account state            | working, lock
type                | string    | The type of this account | spot, margin, otc, point, super-margin
subtype                | string    | The type of sub account (applicable only for isolated margin accout)| The corresponding trading symbol (currency pair) the isolated margin is based on, e.g. btcusdt

<aside class="notice">Margin/super-margin account will only be created after the first time asset transfer-in.</aside>
## Get Account Balance of a Specific Account

API Key Permission：Read

This endpoint returns the balance of an account specified by account id.

### HTTP Request

`GET https://api.huobi.pro/v1/account/accounts/{account-id}/balance`

'account-id': The specified account id to get balance for, can be found by query '/v1/account/accounts' endpoint.

```shell
curl "https://api.huobi.pro/v1/account/accounts/100009/balance"
```

### Request Parameters

<aside class="notice">No parameter is needed for this endpoint</aside>
> The above command returns JSON structured like this:

```json
"data": {
    "id": 100009,
    "type": "spot",
    "state": "working",
    "list": [
      {
        "currency": "usdt",
        "type": "trade",
        "balance": "500009195917.4362872650"
      },
      {
        "currency": "usdt",
        "type": "frozen",
        "balance": "328048.1199920000"
      },
     {
        "currency": "etc",
        "type": "trade",
        "balance": "499999894616.1302471000"
      }
    ],
  }
}
```

### Response Content

Field               | Data Type | Description              | Value Range
---------           | --------- | -----------              | -----------
id                  | integer   | Unique account id        | NA
state               | string    | Account state            | working, lock
type                | string    | The type of this account | spot, margin, otc, point, super-margin
list                | object    | The balance details of each currency

**Per list item content**

Field               | Data Type | Description                           | Value Range
---------           | --------- | -----------                           | -----------
currency            | string    | The currency of this balance          | NA
type                | string    | The balance type                      | trade, frozen
balance             | string    | The balance in the main currency unit | NA


## Get Account History

API Key Permission：Read

This endpoint returns the amount changes of specified user's account.

### HTTP Request

`GET https://api.huobi.pro/v1/account/history`

```shell
curl "https://api.huobi.pro/v1/account/history?account-id=5260185"
```

### Request Parameters

Parameter  | Required | Data Type | Description | Default Value                                  | Value Range
---------  | --------- | -------- | ------- | -----------                                   | ----------
account-id     | true  | string | Account Id, refer to `GET /v1/account/accounts` |     |  
currency      | false | string | Currency name |       | Refer to /v1/common/currencys 
transact-types | false | string | Amount change types (multiple selection allowed)  | all     |trade,etf, transact-fee, deduction, transfer, credit, liquidation, interest, deposit-withdraw, withdraw-fee, exchange, other-types 
start-time   | false | long | Far point of time of the query window (unix time in millisecond). Searching based on transact-time. The maximum size of the query window is 1 hour. The query window can be shifted within 30 days. | ((end-time) – 1hour)     | [((end-time) – 1hour), (end-time)]   
end-time     | false  | long | Near point of time of the query window (unix time in millisecond). Searching based on transact-time. The maximum size of the query window is 1 hour. The query window can be shifted within 30 days.  |  current-time    |[(current-time) – 29days,(current-time)]
sort     | false  | string | Sorting order  |  asc    |asc or desc
size     | false  | int | Maximum number of items in each response  |   100   |[1,500]

> The above command returns JSON structured like this:

```json
{
    "status": "ok",
    "data": [
        {
            "account-id": 5260185,
            "currency": "btc",
            "transact-amt": "0.002393000000000000",
            "transact-type": "transfer",
            "record-id": 89373333576,
            "avail-balance": "0.002393000000000000",
            "acct-balance": "0.002393000000000000",
            "transact-time": 1571393524526
        },
        {
            "account-id": 5260185,
            "currency": "btc",
            "transact-amt": "-0.002393000000000000",
            "transact-type": "transfer",
            "record-id": 89373382631,
            "avail-balance": "0E-18",
            "acct-balance": "0E-18",
            "transact-time": 1571393578496
        }
    ]
}
```

### Response Content

Field               | Data Type | Description              | Value Range
---------           | --------- | -----------              | -----------
status                 | string   | Status code        | 
data               | object    |             | 
{ account-id  | long   | Account ID|
currency               | string    | Currency|
transact-amt                 | string   | Amount change (positive value if income, negative value if outcome)        | 
transact-type                 | string   | Amount change types        | 
avail-balance                 | string   | Available balance        | 
acct-balance                | string   | Account balance        | 
transact-time                 | long   | Transaction time (database time)      | 
record-id }                 | string   | Unique record ID in the database      | 



## Transfer Fund Between Spot Account and Future Contract Account

API Key Permission：Trade

This endpoint allows a user to transfer fund between spot account and futrue contract account. 

The Rate Limit for this endpoint is 10 requests per minute.

### HTTP Request

`POST /v1/futures/transfer`

```json
  {"currency":  "btc",
  "amount": 0.01,
  "type": "pro-to-futures"
  }
 
```
### Request Parameters

Parameter  | Data Type | Required | Description|Values
---------  | --------- | -------- | ------- | -----------
currency|TRUE|String|Currency name|Refer to `GET /v1/common/currencys`
amount|TRUE|Decimal|Amount of fund to transfer|
type|TRUE|String|Type of the transfer|“futures-to-pro” or “pro-to-futures”

> Response:

```json
  {"data":  123456,
  "status": "ok"
  }
 
```
### Response Content

Field               | Data Type | Description
---------           | --------- | -----------
data                | Long   | Transfer id
status              |string| Request status. "ok" or "error"
err-code            |string| error code. Please refer to the err-code list below for details
err-msg             |string| error message. Please refer to the err-code and err-msg list below for details

### error code
err-code              | err-msg | Comments
---------           | --------- | -----------
base-msg||Other errors, please refer to err-msg list below for details. 
base-currency-error|The currency is invalid|
frequent-invoke|the operation is too frequent. Please try again later|Rate limit is 10/min
banned-by-blacklist|Blacklist restriction|
dw-insufficient-balance|Insufficient balance. You can only transfer {0} at most.|Insufficient balance of spot account
dw-account-transfer-unavailable|account transfer unavailable|This API endpoint is not available.
dw-account-transfer-error|account transfer error|
dw-account-transfer-failed|Failed to transfer. Please try again later.|
dw-account-transfer-failed-account-abnormality|Account abnormality, failed to transfer。Please try again later.|

### error message for 'base-msg' err-code
err-code              | err-msg | Comments
---------           | --------- | -----------
base-msg|Unable to transfer in currently. Please contact customer service.|
base-msg|Unable to transfer out currently. Please contact customer service.|
base-msg|Abnormal contracts status. Can’t transfer.|
base-msg|Sub-account doesn't own the permissions to transfer in. Please contact customer service.|
base-msg|Sub-account doesn't own the permissions to transfer out. Please contact customer service.|
base-msg|The sub-account does not have transfer permissions. Please login main account to authorize.|
base-msg|Insufficient amount available.|Insufficient amount of Future Contract Account
base-msg|The single transfer-out amount must be no less than {0}{1}.|
base-msg|The single transfer-out amount must be no more than {0}{1}.|
base-msg|The single transfer-in amount must be no less than {0}{1}.|
base-msg|The single transfer-in amount must be no more than {0}{1}.|
base-msg|Your accumulative transfer-out amount is over the daily maximum, {0}{1}. You can't transfer out for the time being.|
base-msg|Your accumulative transfer-in amount is over the daily maximum, {0}{1}. You can't transfer in for the time being.|
base-msg|Your accumulative net transfer-out amount is over the daily maximum, {0}{1}. You can't transfer out for the time being.|
base-msg|Your accumulative net transfer-in amount is over the daily maximum, {0}{1}. You can't transfer in for the time being.|
base-msg|The platform's accumulative transfer-out amount is over the daily maximum. You can't transfer out for the time being.|
base-msg|The platform's accumulative transfer-in amount is over the daily maximum. You can't transfer in for the time being.|
base-msg|The platform's accumulative net transfer-out amount is over the daily maximum. You can't transfer out for the time being.|
base-msg|The platform's accumulative net transfer-in amount is over the daily maximum. You can't transfer in for the time being.|
base-msg|Transfer failed. Please try again later or contact customer service.|
base-msg|Abnormal service, transfer failed. Please try again later.|
base-msg|You don’t have access permission as you have not opened contracts trading.|
base-msg|This contract type doesn't exist.|There is no corresponding Future Contract for the currency defined in the request.


## Transfer Asset between Parent and Sub Account

API Key Permission：Trade

This endpoint allows user to transfer asset between parent and sub account.

### HTTP Request

`POST https://api.huobi.pro/v1/subuser/transfer`

```shell
curl -X POST "https://api.huobi.pro/v1/subuser/transfer" -H "Content-Type: application/json" -d '{"sub-uid": 12345, "currency": "btc", "amount": 123.5, "type": "master-transfer-in"}'
```

### Request Parameters

Parameter  | Data Type | Required | Description                                       | Value Range
---------  | --------- | -------- | -----------                                       | -----------
sub-uid    | integer   | true     | The target sub account uid to transfer to or from | NA
currency   | string    | true     | The crypto currency to transfer                   | NA
amount     | decimal   | true     | The amount of asset to transfer                   | NA
type       | string    | true     | The type of transfer                              | master-transfer-in, master-transfer-out, master-point-transfer-in, master-point-transfer-out

> The above command returns JSON structured like this:

```json
  "data": 12345
```

### Response Content

<aside class="notice">The return data contains a single value instead of an object</aside>
Field               | Data Type | Description
---------           | --------- | -----------
data                | integer   | Unique transfer id


## Get the Aggregated Balance of all Sub-accounts of the Current User

API Key Permission：Read

This endpoint returns the balances of all the sub-account aggregated.

### HTTP Request

`GET https://api.huobi.pro/v1/subuser/aggregate-balance`

```shell
curl "https://api.huobi.pro/v1/subuser/aggregate-balance"
```

> The above command returns JSON structured like this:

```json
  "data": [
      {
        "currency": "eos",
        "type": "spot",
        "balance": "1954559.809500000000000000"
      },
      {
        "currency": "btc",
        "type": "spot",
        "balance": "0.000000000000000000"
      },
      {
        "currency": "usdt",
        "type": "spot",
        "balance": "2925209.411300000000000000"
      }
   ]
```

### Request Parameters

<aside class="notice">No parameter is needed for this endpoint</aside>
### Response Content

<aside class="notice">The returned "data" object is a list of aggregated balances</aside>
Field               | Data Type | Description
---------           | --------- | -----------
currency            | string    | The currency of this balance
type|string|account type (spot, margin, point)
balance             | string    | The total balance in the main currency unit including all balance and frozen banlance

## Get Account Balance of a Sub-Account

API Key Permission：Read

This endpoint returns the balance of a sub-account specified by sub-uid.

### HTTP Request

`GET https://api.huobi.pro/v1/account/accounts/{sub-uid}`

'sub-uid': The specified sub user id to get balance for.

```shell
curl "https://api.huobi.pro/v1/account/accounts/10758899"
```

### Request Parameters

<aside class="notice">No parameter is needed for this endpoint</aside>
> The above command returns JSON structured like this:

```json
"data": [
  {
    "id": 9910049,
    "type": "spot",
    "list": [
              {
        "currency": "btc",
          "type": "trade",
          "balance": "1.00"
      },
      {
        "currency": "eth",
        "type": "trade",
        "balance": "1934.00"
      }
      ]
  },
  {
    "id": 9910050,
    "type": "point",
    "list": []
  }
]
```

### Response Content

<aside class="notice">The returned "data" object is a list of accounts under this sub-account</aside>
Field               | Data Type | Description                           | Value Range
---------           | --------- | -----------                           | -----------
id                  | integer   | Unique account id                     | NA
type                | string    | The type of this account              | spot, margin, otc, point
list                | object    | The balance details of each currency  | NA

**Per list item content**

Field               | Data Type | Description                           | Value Range
---------           | --------- | -----------                           | -----------
currency            | string    | The currency of this balance          | NA
type                | string    | The balance type                      | trade, frozen
balance             | string    | The balance in the main currency unit | NA


## Lock/Unlock Sub User(by Parent user)

API Key Permission：Trade

This endpoint allows parent user to lock or unlock a specific sub user.

### HTTP Request

`POST https://api.huobi.pro/v2/sub-user/management`

### Request Parameters

| Parameter  | Data Type | Required | Description                                       | Value Range
| ---------  | --------- | -------- | -----------                                       | -----------
| subUid    | long  | true     | Sub user UID | NA
| action   | string    | true     | Action                   | lock,unlock 

> The above command returns JSON structured like this:

```json
{
  "code": 200,
	"data": {
     "subUid": 12902150,
     "userState":"lock"}
}
```

### Response Content

| Field               | Data Type | Description                           | Value Range
| ---------           | --------- | -----------                           | -----------
| subUid                 | long   | sub user UID                     | NA
| userState                | string    | The state of sub user             | lock,normal



# Wallet (Deposit and Withdraw)

<aside class="notice">All endpoints in this section require authentication</aside>
## APIv2 - Query Deposit Address

API user could query deposit address of corresponding chain, for a specific crypto currency (except IOTA)

API Key Permission：Read

<aside class="notice"> The endpoint does not support deposit address querying for currency "IOTA" at this moment </aside>
### HTTP Request

`GET https://api.huobi.pro/v2/account/deposit/address`

```shell
curl "https://api.huobi.pro/v2/account/deposit/address?currency=btc"
```

### Request Parameters

Field Name  | Data Type | Mandatory | Default Value | Description
---------  | --------- | -------- | ------- | -----------
currency   | string    | true     | N/A      | Crypto currency,refer to `GET /v1/common/currencys`

> The above command returns JSON structured like this:

```json
{
    "code": 200,
    "data": [
        {
            "currency": "btc",
            "address": "1PSRjPg53cX7hMRYAXGJnL8mqHtzmQgPUs",
            "addressTag": "",
            "chain": "btc"
        }
    ]
}
```

### Response Content

Field Name            | Data Type | Description
---------           | --------- | -----------
code                | int   | Status code
message                | string   | Error message (if any)
data                | object  | 
  { currency|string|Crypto currency
    address|string|Deposit address
    addressTag|string|Deposit address tag
    chain }|string|Block chain name

### Status Code

| Status Code | Error Message  | Scenario |
| ---- | ----- | ---- |
| 200| success | Request successful |
| 500| error | System error |
| 1002| unauthorized | Unauthorized |
| 1003| invalid signature | Signature failure |
| 2002| invalid field value in "field name" | Invalid field value |
| 2003| missing mandatory field "field name" | Mandatory field missing |


## APIv2 - Query Withdraw Quota

API user could query withdraw quota for currencies

API Key Permission：Read

### HTTP Request

`GET https://api.huobi.pro/v2/account/withdraw/quota`

```shell
curl "https://api.huobi.pro/v2/account/withdraw/quota?currency=btc"
```

### Request Parameters

Field Name  | Data Type | Mandatory | Default Value | Description
---------  | --------- | -------- | ------- | -----------
currency   | string    | true     | N/A      | Crypto currency,refer to `GET /v1/common/currencys`

> The above command returns JSON structured like this:

```json
{
    "code": 200,
    "data": 
        {
            "currency": "btc",
            "chains": [
                {
                    "chain": "btc",
                    "maxWithdrawAmt": "200.00000000",
                    "withdrawQuotaPerDay": "200.00000000",
                    "remainWithdrawQuotaPerDay": "200.000000000000000000",
                    "withdrawQuotaPerYear": "700000.00000000",
                    "remainWithdrawQuotaPerYear": "700000.000000000000000000",
                    "withdrawQuotaTotal": "7000000.00000000",
                    "remainWithdrawQuotaTotal": "7000000.000000000000000000"
                }
        }
    ]
}
```

### Response Content

Field Name            | Data Type | Description
---------           | --------- | -----------
code                | int   | Status code
message                | string   | Error message (if any)
data                | object  | 
  currency|string|Crypto currency
    chains|object|
    { chain |string|Block chain name
      maxWithdrawAmt |  string | Maximum withdraw amount in each request |      |
      withdrawQuotaPerDay |  string | Maximum withdraw amount in a day |      |
      remainWithdrawQuotaPerDay |  string | Remaining withdraw quota in the day |      |
      withdrawQuotaPerYear |  string | Maximum withdraw amount in a year |      |
      remainWithdrawQuotaPerYear |  string | Remaining withdraw quota in the year |      |
      withdrawQuotaTotal |  string | Maximum withdraw amount in total |      |
      remainWithdrawQuotaTotal }|  string | Remaining withdraw quota in total |      |

### Status Code

| Status Code | Error Message  | Scenario |
| ---- | ----- | ---- |
| 200| success | Request successful |
| 500| error | System error |
| 1002| unauthorized | Unauthorized |
| 1003| invalid signature | Signature failure |
| 2002| invalid field value in "field name" | Invalid field value |


## Create a Withdraw Request

API Key Permission：Withdraw

This endpoint creates a withdraw request from your spot trading account to an external address.

<aside class="notice">If user has chosen fast withdraw preferred in  <a href='https://www.hbg.com/en-us/user_center/uc_setting/'>Settings </a>, the withdraw requests submitted via this endpoint would choose 'fast withdraw' as preferred channel. </aside>
<aside class="notice">Only support the existed addresses in your  <a href='https://www.hbg.com/en-us/withdraw_address/'>withdraw address list</a>. The once-off withdraw address of IOTA couldn't be set in the list, thus IOTA withdrawal is not supported through API. </aside>
### HTTP Request

`POST https://api.huobi.pro/v1/dw/withdraw/api/create`

```shell
curl -X POST -H "Content-Type: application/json" "https://api.huobi.pro/v1/dw/withdraw/api/create" -d
'{
  "address": "0xde709f2102306220921060314715629080e2fb77",
  "amount": "0.05",
  "currency": "eth",
  "fee": "0.01"
}'
```

### Request Parameters

Parameter  | Data Type | Required | Default | Description
---------  | --------- | -------- | ------- | -----------
address    | string    | true     | NA      | The desination address of this withdraw
currency   | string    | true     | NA      | Crypto currency,refer to `GET /v1/common/currencys`
amount     | string    | true     | NA      | The amount of currency to withdraw
fee        | string    | true    | NA      | The fee to pay with this withdraw
chain      | string    | false    | NA      |Refer to`GET /v2/reference/currencies`.Set as "usdt" to withdraw USDT to OMNI, set as "trc20usdt" to withdraw USDT to TRX
addr-tag   | string    | false    | NA      | A tag specified for this address

> The above command returns JSON structured like this:

```json
{  
  "data": 1000
}
```

### Response Content

<aside class="notice">The return data contains a single value instead of an object</aside>
Field               | Data Type | Description
---------           | --------- | -----------
data                | integer   | Transfer id

<aside class="notice">All new transfer id will be incremental to the previous ids. This allows search by transfer id sequences</aside>
## Cancel a Withdraw Request

API Key Permission：Withdraw

This endpoint cancels a previously created withdraw request by its transfer id.

### HTTP Request

`POST https://api.huobi.pro/v1/dw/withdraw-virtual/{withdraw-id}/cancel`

```shell
curl -X POST "https://api.huobi.pro/v1/dw/withdraw-virtual/1000/cancel"
```

'withdraw-id': the id returned when previously created a withdraw request

### Request Parameters

<aside class="notice">No parameter is needed for this endpoint</aside>
> The above command returns JSON structured like this:

```json
  "data": 700
```

### Response Content

<aside class="notice">The return data contains a single value instead of an object</aside>
Parameter           | Data Type | Description
---------           | --------- | -----------
data                | integer   | Withdraw cancel id


## Search for Existed Withdraws and Deposits

API Key Permission：Read

This endpoint searches for all existed withdraws and deposits and return their latest status.

### HTTP Request

`GET https://api.huobi.pro/v1/query/deposit-withdraw`

```shell
curl "https://api.huobi.pro/v1/query/deposit-withdraw?currency=xrp&type=deposit&from=5&size=12"
```

### Request Parameters

Parameter  | Data Type | Required | Description                     | Value Range | Default Value|
---------  | --------- | -------- | -----------                     | ------------|------------------|
currency   | string    | false     | The crypto currency to withdraw | NA |When currency is not specified, the reponse would include the records of ALL currencies. 
type       | string    | true     | Define transfer type to search  | deposit, withdraw| |
from       | string    | false    | The transfer id to begin search | 1 ~ latest record ID| When 'from' is not specified, the default value would be 1 if 'direct' is 'prev' with the response in ascending order, the default value would be the ID of latest record if 'direct' is 'next' with the response in descending order.
size       | string    | false     | The number of items to return   | 1-500 | 100 |
direct     | string    | false     | the order of response | 'prev' (ascending), 'next' (descending)| 'prev' |

> The above command returns JSON structured like this:

```json
{
	"status": "ok",
	"data": [{
		"id": 24383070,
		"type": "deposit",
		"currency": "usdt",
		"chain": "usdterc20",
		"tx-hash": "16382690",
		"amount": 4.000000000000000000,
		"address": "0x138d709030b4e096044d371a27efc5c562889b9b",
		"address-tag": "",
		"fee": 0,
		"state": "safe",
		"created-at": 1571303815800,
		"updated-at": 1571303815826
	}]
}
```

### Response Content

Field               | Data Type | Description
---------           | --------- | -----------
id                  | integer   | Transfer id
type                | string    | Define transfer type to search, possible values: [deposit, withdraw]
currency            | string    | The crypto currency to withdraw
tx-hash             | string    | The on-chain transaction hash
chain             | string    | Block chain name
amount              | float   | The number of crypto asset transfered in its minimum unit
address             | string    | The deposit or withdraw source address
address-tag         | string    | The user defined address tag
fee                 | float   | Withdraw fee
state               | string    | The state of this transfer (see below for details)
created-at          | integer   | The timestamp in milliseconds for the transfer creation
updated-at          | integer   | The timestamp in milliseconds for the transfer's latest update

**List of possible withdraw state**

State           | Description
---------       | -----------
submitted       | Withdraw request submitted successfully
reexamine       | Under examination for withdraw validation
canceled        | Withdraw canceled by user
pass            | Withdraw validation passed
reject          | Withdraw validation rejected
pre-transfer    | Withdraw is about to be released
wallet-transfer | On-chain transfer initiated
wallet-reject   | Transfer rejected by chain
confirmed       | On-chain transfer completed with one confirmation
confirm-error   | On-chain transfer faied to get confirmation
repealed        | Withdraw terminated by system

**List of possible deposit state**

State           | Description
---------       | -----------
unknown         | On-chain transfer has not been received
confirming      | On-chain transfer waits for first confirmation
confirmed       | On-chain transfer confirmed for at least one block
safe            | Multiple on-chain confirmation happened
orphan          | Confirmed but currently in an orphan branch


# Trading

<aside class="notice">All endpoints in this section require authentication</aside>
<aside class="warning">When trade with margin loan from your margin account, "account-id" parameter should be set to margin account id, "source" parameter should be set to "margin-api"; When trade with super-margin loan from your super-margin account, "account-id" parameter should be set to super-margin account id, "source" parameter should be set to "super-margin-api"</aside>
## Place a New Order

API Key Permission：Trade

This endpoint place a new order and send to the exchange to be matched.

### HTTP Request

`POST https://api.huobi.pro/v1/order/orders/place`

```shell
curl -X POST -H "Content-Type: application/json" "https://api.huobi.pro/v1/order/orders/place" -d
'{
   "account-id": "100009",
   "amount": "10.1",
   "price": "100.1",
   "source": "api",
   "symbol": "ethusdt",
   "type": "buy-limit",
   "client-order-id": "a0001"
  }'
```

### Request Parameters

Parameter  | Data Type | Required | Default | Description                               | Value Range
---------  | --------- | -------- | ------- | -----------                               | -----------
account-id | string    | true     | NA      | The account id used for this trade        | Refer to `GET /v1/account/accounts` 
symbol     | string    | true     | NA      | The trading symbol to trade               | Refer to `GET /v1/common/symbols` 
type       | string    | true     | NA      | The order type                            | buy-market, sell-market, buy-limit, sell-limit, buy-ioc, sell-ioc, buy-limit-maker, sell-limit-maker, buy-stop-limit, sell-stop-limit
amount     | string    | true     | NA      | order size (for market buy order type, it's order value) | NA
price      | string    | false    | NA      | The limit price of limit order, only needed for limit order   | NA
source     | string    | false    | api     | When trade with margin use 'margin-api'; When trade with super-margin use 'super-margin-api';    | api, margin-api,super-margin-api
client-order-id| string    | false    | NA     | Client order ID (maximum 64-character length, to be unique within 24 hours)  | 
stop-price    | string          | false | NA    | Trigger price of stop limit order   | 
operator       | string       | false  | NA   | operation charactor of stop price   | gte – greater than and equal (>=), lte – less than and equal (<=) 

> The above command returns JSON structured like this:

```json
  "data": "59378"
```

### Response Content

<aside class="notice">The returned data object is a single string which represents the order id</aside>
If client order ID duplicates with a previous order (within 24 hours), the endpoint responds that previous order ID.

## Place a Batch of Orders

API Key Permission：Trade

A batch contains at most 10 orders

### HTTP Request

- POST ` /v1/order/batch-orders`

```json
 [
 	{
     "account-id": "123456",
     "price": "7801",
     "amount": "0.001",
     "symbol": "btcusdt",
     "type": "sell-limit",
     "client-order-id": "c1"
 	},
 	{
     "account-id": "123456",
     "price": "7802",
     "amount": "0.001",
     "symbol": "btcusdt",
     "type": "sell-limit",
     "client-order-id": "d2"
 	}
 ]
```

### Request Parameters

Parameter | Data Type | Required | Default | Description 
---------  | --------- | -------- | ------- | -----------
[{ account-id | string    | true     | NA      | The account id, refer to `GET /v1/account/accounts`. Use 'spot' `account-id` for spot trading, use 'margin' `account-id` for isolated margin trading, use ‘super-margin’  `account-id` for cross margin trading. 
symbol     | string    | true     | NA      | The trading symbol, i.e. btcusdt, ethbtc...(Refer to `GET /v1/common/symbols`) 
 type       | string    | true     | NA      | The type of order, including 'buy-market', 'sell-market', 'buy-limit', 'sell-limit', 'buy-ioc', 'sell-ioc', 'buy-limit-maker', 'sell-limit-maker' (refer to detail below), 'buy-stop-limit', 'sell-stop-limit'. 
amount     | string    | true     | NA      | The order size (for market buy order type, it's order value) 
price      | string    | false    | NA      | The limit price of limit order, only needed for limit order 
client-order-id| string    | false    | NA     | Client order ID (maximum 64-character length, to be unique within 24 hours) 
stop-price|string|false|NA|Trigger price of stop limit order
operator}] |string|false|NA|Operation character of stop price, use 'gte' for greater than and equal (>=), use 'lte' for less than and equal (<=)

**buy-limit-maker**

If the order price is greater than or equal to the lowest selling price in the market, the order will be rejected.

If the order price is less than the lowest selling price in the market, the order will be accepted.

**sell-limit-maker**

If the order price is less than or equal to the highest buy price in the market, the order will be rejected.

If the order price is greater than the highest buy price in the market, the order will be accepted.

> Response:

```json
{
    "status": "ok",
    "data": [
        {
            "order-id": 61713400772,
            "client-order-id": "c1"
        },
        {
            "order-id": 61713400940,
            "client-order-id": "d2"
        }
    ]
}
```

### Response Content

Field    | Data Type | Description 
---------           | --------- | -----------
[{order-id                  | integer   | The order id 
client-order-id              | string    | The client order id (if available) 
err-code            | string    | The error code (only for rejected order) 
err-msg}] | string    | The error message (only for rejected order) 

If client order ID duplicates with a previous order (within 24 hours), the endpoint responds that previous order's Id and client order ID.

## Submit Cancel for an Order

API Key Permission：Trade

This endpoint submit a request to cancel an order.

<aside class="warning">This only submit the cancel request, the actual result of the canel request needs to be checked by order status or match result endpoints</aside>
### HTTP Request

`POST https://api.huobi.pro/v1/order/orders/{order-id}/submitcancel`

'order-id': the previously returned order id when order was created

```shell
curl -X POST "https://api.huobi.pro/v1/order/orders/59378/submitcancel"
```

### Request Parameters

No parameter is needed for this endpoint.

> The above command returns JSON structured like this:

```json
  "data": "59378"
```

### Response Content

<aside class="notice">The returned data object is a single string which represents the order id</aside>
### Error Code

> Response:

```json
{
  "status": "error",
  "err-code": "order-orderstate-error",
  "err-msg": "Incorrect order state",
  "order-state":-1 // current order state
}
```

The possible values of "order-state" includes -

order-state           |  Description
---------       | -----------
-1| order was already closed in the long past (order state = canceled, partial-canceled, filled, partial-filled)
5| partial-canceled
6| filled
7| canceled
10| cancelling

## Submit Cancel for an Order (based on client order ID)

API Key Permission：Trade

This endpoint submit a request to cancel an order.

<aside class="warning">This only submit the cancel request, the actual result of the canel request needs to be checked by order status or match result endpoints</aside>
### HTTP Request

`POST https://api.huobi.pro/v1/order/orders/submitCancelClientOrder`

```shell
curl -X POST -H "Content-Type: application/json" "https://api.huobi.pro/v1/order/orders/submitCancelClientOrder" -d
'{
  "client-order-id": "a0001"
  }'
```

### Request Parameters

Parameter  | Data Type | Required | Default | Description
---------  | --------- | -------- | ------- | -----------
client-order-id     | string    | true     | NA      | Client order ID

> The above command returns JSON structured like this:

```json
  "data": "59378"
```

### Response Content

Field           | Data Type | Description
---------       | --------- | -----------
data         | int      | Cancellation status code

Status Code           |  Description
---------       | -----------
-1| order was already closed in the long past (order state = canceled, partial-canceled, filled, partial-filled)
0| client-order-id not found
5| partial-canceled
6| filled
7| canceled
10| cancelling


## Get All Open Orders

API Key Permission：Read

This endpoint returns all open orders which have not been filled completely.

### HTTP Request

`GET https://api.huobi.pro/v1/order/openOrders`

```shell
curl "https://api.huobi.pro/v1/order/openOrders?account-id=100009&symbol=btcusdt&side=buy&size=5"
```

### Request Parameters

Parameter  | Data Type | Required | Default | Description                             | Value Range
---------  | --------- | -------- | ------- | -----------                             | -----------
account-id | string    | true    | NA      | The account id used for this trade      | Refer to `GET /v1/account/accounts`
symbol     | string    | true    | NA      | The trading symbol to trade             | Refer to `GET /v1/common/symbols`
side       | string    | false    | NA      | Filter on the direction of the trade    | buy, sell
from       | string    | false    | NA      |  start order ID the searching to begin with   |
direct       | string    | false (if field "from" is defined, this field "direct" becomes mandatory)   | NA      |  searching direction    | prev - in ascending order from the start order ID; next - in descending order from the start order ID
size       | int       | false    | 100      | The number of orders to return          | [1, 500]

> The above command returns JSON structured like this:

```json
  "data": [
    {
      "id": 5454937,
      "symbol": "ethusdt",
      "account-id": 30925,
      "amount": "1.000000000000000000",
      "price": "0.453000000000000000",
      "created-at": 1530604762277,
      "type": "sell-limit",
      "filled-amount": "0.0",
      "filled-cash-amount": "0.0",
      "filled-fees": "0.0",
      "source": "web",
      "state": "submitted"
    }
  ]
```

### Response Content

Field               | Data Type | Description
---------           | --------- | -----------
id                  | integer   | order id
symbol              | string    | The trading symbol to trade, e.g. btcusdt, bccbtc
price               | string    | The limit price of limit order
created-at          | int       | The timestamp in milliseconds when the order was created
type                | string    | The order type, possible values are: buy-market, sell-market, buy-limit, sell-limit, buy-ioc, sell-ioc, buy-limit-maker, sell-limit-maker, buy-stop-limit, sell-stop-limit
filled-amount       | string    | The amount which has been filled
filled-cash-amount  | string    | The filled total in quote currency
filled-fees         | string    | Transaction fee paid so far
source              | string    | The source where the order was triggered, possible values: sys, web, api, app
state               | string    | submitted, partial-filled, cancelling, created
stop-price    | string          | false | NA    | Trigger price of stop limit order   | |
operator       | string       | false  | NA   | operation charactor of stop price   | gte – greater than and equal (>=), lte – less than and equal (<=) |

## Submit Cancel for Multiple Orders by Criteria

API Key Permission：Trade

This endpoint submit cancellation for multiple orders at once with given criteria.

### HTTP Request

`POST https://api.huobi.pro/v1/order/orders/batchcancelopenorders`

```shell
curl -X POST -H 'Content-Type: application/json' "https://api.huobi.pro/v1/order/orders/batchCancelOpenOrders" -d
'{
  "account-id": "100009",
  "symbol": "btcusdt,btchusd",
  "side": "buy",
  "size": 5
}'
```

Parameter  | Data Type | Required | Default | Description                             | Value Range
---------  | --------- | -------- | ------- | -----------                             | -----------
account-id | string    | true    | NA      | The account id used for this cancel     | Refer to `GET /v1/account/accounts`
symbol     | string    | false    | NA      | The trading symbol list (maximum 10 symbols, separated by comma, default value all symbols)            | All supported trading symbol, e.g. btcusdt, bccbtc.Refer to `GET /v1/common/symbols`
side       | string    | false    | NA      | Filter on the direction of the trade    | buy, sell
size       | int       | false    | 100     | The number of orders to cancel          | [1, 100]

> The above command returns JSON structured like this:

```json
  "data": {
    "success-count": 2,
    "failed-count": 0,
    "next-id": 5454600
  }
```

### Response Content

Field           | Data Type | Description
---------       | --------- | -----------
success-count   | integer   | The number of cancel request sent successfully
failed-count    | integer   | The number of cancel request failed
next-id         | integer   | the next order id that can be cancelled

## Submit Cancel for Multiple Orders by IDs

API Key Permission：Trade

This endpoint submit cancellation for multiple orders at once with given ids.

### HTTP Request

`POST https://api.huobi.pro/v1/order/orders/batchcancel`

```shell
curl -X POST -H 'Content-Type: application/json' "https://api.huobi.pro/v1/order/orders/batchcancel" -d
'{
  "client-order-ids": [
    "5983466", "5722939", "5721027", "5719487"
  ]
}'
```

### Request Parameters

 Parameter        | Data Type | Required | Description                                                  | Value Range         
 ---------------- | --------- | -------- | ------------------------------------------------------------ | ------------------- 
 order-ids        | string[]  | false    | The order ids to cancel (Either order-ids or client-order-ids can be filled in one batch request) | No more than 50 ids 
 client-order-ids | string[]  | false    | The client order ids to cancel (Either order-ids or client-order-ids can be filled in one batch request) | No more than 50 ids 

> The above command returns JSON structured like this:

```json
{
    "status": "ok",
    "data": {
        "success": [
            "5983466"            
        ],
        "failed": [
            {
              "err-msg": "Incorrect order state",
              "order-state": 7,
              "order-id": "",
              "err-code": "order-orderstate-error",
              "client-order-id": "first"
            },
            {
              "err-msg": "Incorrect order state",
              "order-state": 7,
              "order-id": "",
              "err-code": "order-orderstate-error",
              "client-order-id": "second"
            },
            {
              "err-msg": "The record is not found.",
              "order-id": "",
              "err-code": "base-not-found",
              "client-order-id": "third"
            }
          ]
    }
}
```

### Response Content

 Field    | Data Type | Description                                                  
 -------- | --------- | ------------------------------------------------------------ 
 {success | string[]  | Cancelled order list (Can be order ID list or client order list, upon the request) 
 failed}  | string[]  | Failed order list (Can be order ID list or client order list, upon the request) 

The failed id list has below fields

Fields | Data Type | Description 
---- | ----- | ----
[{ order-id | long | The order id (if the request is based on order-ids) 
client-order-id | string | The client order id (if the request is based on client-order-ids) 
err-code | string | The error code (only applicable for rejected order) 
err-msg | string | The error message (only applicable for rejected order) 
order-state }] | string | Current order state (if available) 

The possible values of "order-state" includes -

order-state           |  Description
---------       | -----------
-1| order was already closed in the long past (order state = canceled, partial-canceled, filled, partial-filled)
5| partial-canceled
6| filled
7| canceled
10| cancelling


## Get the Order Detail of an Order

API Key Permission：Read

This endpoint returns the detail of one order.

### HTTP Request

`GET https://api.huobi.pro/v1/order/orders/{order-id}`

'order-id': the previously returned order id when order was created

```shell
curl "https://api.huobi.pro/v1/order/orders/59378"
```

### Request Parameters

No parameter is needed for this endpoint.

> The above command returns JSON structured like this:

```json
{  
  "data": {
    "id": 59378,
    "symbol": "ethusdt",
    "account-id": 100009,
    "amount": "10.1000000000",
    "price": "100.1000000000",
    "created-at": 1494901162595,
    "type": "buy-limit",
    "field-amount": "10.1000000000",
    "field-cash-amount": "1011.0100000000",
    "field-fees": "0.0202000000",
    "finished-at": 1494901400468,
    "user-id": 1000,
    "source": "api",
    "state": "filled",
    "canceled-at": 0
  }
}
```

### Response Content

Field               | Data Type | Description
---------           | --------- | -----------
id                  | integer   | order id
symbol              | string    | The trading symbol to trade, e.g. btcusdt, bccbtc
account-id          | string    | The account id which this order belongs to
amount              | string    | The amount of base currency in this order
price               | string    | The limit price of limit order
created-at          | int       | The timestamp in milliseconds when the order was created
finished-at         | int       | The timestamp in milliseconds when the order was changed to a final state. This is not the time the order is matched.
canceled-at         | int       | The timestamp in milliseconds when the order was canceled, if not canceled then has value of 0
type                | string    | The order type, possible values are: buy-market, sell-market, buy-limit, sell-limit, buy-ioc, sell-ioc, buy-limit-maker, sell-limit-maker, buy-stop-limit, sell-stop-limit
filled-amount       | string    | The amount which has been filled
filled-cash-amount  | string    | The filled total in quote currency
filled-fees         | string    | Transaction fee paid so far
source              | string    | The source where the order was triggered, possible values: sys, web, api, app
state               | string    | Order state: submitted, partial-filled, filled, canceled
exchange            | string    | Internal data
batch               | string    | Internal data
stop-price|string|trigger price of stop limit order
operator|string|operation character of stop price



## Get the Order Detail of an Order (based on client order ID)

API Key Permission：Read

This endpoint returns the detail of one order.

### HTTP Request

`GET https://api.huobi.pro/v1/order/orders/getClientOrder`

```shell
curl "https://api.huobi.pro/v1/order/orders/getClientOrder?clientOrderId=a0001"
```

### Request Parameters

Parameter  | Data Type | Required | Default | Description
---------  | --------- | -------- | ------- | -----------
clientOrderID     | string    | true     | NA      | Client order ID

> The above command returns JSON structured like this:

```json
{  
  "data": {
    "id": 59378,
    "symbol": "ethusdt",
    "account-id": 100009,
    "amount": "10.1000000000",
    "price": "100.1000000000",
    "created-at": 1494901162595,
    "type": "buy-limit",
    "field-amount": "10.1000000000",
    "field-cash-amount": "1011.0100000000",
    "field-fees": "0.0202000000",
    "finished-at": 1494901400468,
    "user-id": 1000,
    "source": "api",
    "state": "filled",
    "canceled-at": 0
  }
}
```

### Response Content

Field               | Data Type | Description
---------           | --------- | -----------
id                  | integer   | order id
symbol              | string    | The trading symbol to trade, e.g. btcusdt, bccbtc
account-id          | string    | The account id which this order belongs to
amount              | string    | The amount of base currency in this order
price               | string    | The limit price of limit order
created-at          | int       | The timestamp in milliseconds when the order was created
finished-at         | int       | The timestamp in milliseconds when the order was changed to a final state. This is not the time the order is matched.
canceled-at         | int       | The timestamp in milliseconds when the order was canceled, if not canceled then has value of 0
type                | string    | The order type, possible values are: buy-market, sell-market, buy-limit, sell-limit, buy-ioc, sell-ioc, buy-limit-maker, sell-limit-maker, buy-stop-limit, sell-stop-limit
filled-amount       | string    | The amount which has been filled
filled-cash-amount  | string    | The filled total in quote currency
filled-fees         | string    | Transaction fee paid so far
source              | string    | The source where the order was triggered, possible values: sys, web, api, app
state               | string    | Order state: submitted, partial-filled, filled, canceled
exchange            | string    | Internal data
batch               | string    | Internal data
stop-price|string|trigger price of stop limit order
operator|string|operation character of stop price

If the client order ID is not found, following error message will be returned:
{
    "status": "error",
    "err-code": "base-record-invalid",
    "err-msg": "record invalid",
    "data": null
}



## Get the Match Result of an Order

API Key Permission：Read

This endpoint returns the match result of an order.

### HTTP Request

`GET https://api.huobi.pro/v1/order/orders/{order-id}/matchresults`

'order-id': the previously returned order id when order was created

```shell
curl "https://api.huobi.pro/v1/order/orders/59378/matchresults"
```

### Request Parameters

No parameter is needed for this endpoint.

> The above command returns JSON structured like this:

```json
  "data": [
    {
      "id": 29553,
      "order-id": 59378,
      "match-id": 59335,
      "trade-id": 100282808529,
      "symbol": "ethusdt",
      "type": "buy-limit",
      "source": "api",
      "price": "100.1000000000",
      "filled-amount": "9.1155000000",
      "filled-fees": "0.0182310000",
      "created-at": 1494901400435,
      "role": maker,
      "filled-points": "0.0",
      "fee-deduct-currency": ""
    }
  ]
```

### Response Content

<aside class="notice">The return data contains a list and each item in the list represents a match result</aside>
Parameter           | Data Type | Description
---------           | --------- | -----------
id                  | integer   | Internal id
symbol              | string    | The trading symbol to trade, e.g. btcusdt, bccbtc
order-id            | string    | The order id of this order
match-id            | string    | The match id of this match
trade-id            | int    | Unique trade ID (NEW)
price               | string    | The limit price of limit order
created-at          | int       | The timestamp in milliseconds when the match and fill is done
type                | string    | The order type, possible values are: buy-market, sell-market, buy-limit, sell-limit, buy-ioc, sell-ioc, buy-limit-maker, sell-limit-maker, buy-stop-limit, sell-stop-limit
filled-amount       | string    | The amount which has been filled
filled-fees         | string    | Transaction fee paid so far
source              | string    | The source where the order was triggered, possible values: sys, web, api, app
role                  | string   | the role in the transaction: taker or maker
filled-points      | string   | deduction amount (unit: in ht or hbpoint) 
fee-deduct-currency      | string   | deduction type. if blank, the transaction fee is based on original currency; if showing value as "ht", the transaction fee is deducted by HT; if showing value as "hbpoint", the transaction fee is deducted by HB point.    



## Search Past Orders

API Key Permission：Read

This endpoint returns orders based on a specific searching criteria.

### HTTP Request

`GET https://api.huobi.pro/v1/order/orders`

```shell
curl "https://api.huobi.pro/v1/order/orders?symbol=ethusdt&type=buy-limit&staet=filled"
```

### Request Parameters

Parameter  | Data Type | Required | Default | Description                                   | Value Range
---------  | --------- | -------- | ------- | -----------                                   | ----------
symbol     | string    | true     | NA      | The trading symbol | All supported trading symbols, e.g. btcusdt, bccbtc
types      | string    | false    | NA      | One or more types of order to include in the search, use comma to separate. | buy-market, sell-market, buy-limit, sell-limit, buy-ioc, sell-ioc, buy-stop-limit, sell-stop-limit
start-date | string    | false    | -1d    | Search starts date, in format yyyy-mm-dd      | Value range [((end-date) – 1), (end-date)], maximum query window size is 2 days, query window shift should be within past 180 days, query window shift should be within past 7 days for cancelled order (state = "canceled") 
end-date   | string    | false    | today   | Search ends date, in format yyyy-mm-dd        |Value range [(today-179), today], maximum query window size is 2 days, query window shift should be within past 180 days, queriable range should be within past 1 day for cancelled order (state = "canceled") 
states     | string    | true    | NA      | One or more  states of order to include in the search, use comma to separate. | submitted, partial-filled, partial-canceled, filled, canceled, created
from       | string    | false    | NA      | Search order id to begin with                 | NA
direct     | string    | false    | both    | Search direction when 'from' is used          | next, prev
size       | int       | false    | 100     | The number of orders to return                | [1, 100]

> The above command returns JSON structured like this:

```json
  "data": [
    {
      "id": 59378,
      "symbol": "ethusdt",
      "account-id": 100009,
      "amount": "10.1000000000",
      "price": "100.1000000000",
      "created-at": 1494901162595,
      "type": "buy-limit",
      "field-amount": "10.1000000000",
      "field-cash-amount": "1011.0100000000",
      "field-fees": "0.0202000000",
      "finished-at": 1494901400468,
      "user-id": 1000,
      "source": "api",
      "state": "filled",
      "canceled-at": 0
    }
  ]
```

### Response Content

Field               | Data Type | Description
---------           | --------- | -----------
id                  | integer   | Order id
account-id          | integer   | Account id
user-id             | integer   | User id
amount              | string    | The amount of base currency in this order
symbol              | string    | The trading symbol to trade, e.g. btcusdt, bccbtc
price               | string    | The limit price of limit order
created-at          | int       | The timestamp in milliseconds when the order was created
canceled-at         | int       | The timestamp in milliseconds when the order was canceled, or 0 if not canceled
finished-at         | int       | The timestamp in milliseconds when the order was finished, or 0 if not finished
type                | string    | The order type, possible values are: buy-market, sell-market, buy-limit, sell-limit, buy-ioc, sell-ioc, buy-limit-maker, sell-limit-maker, buy-stop-limit, sell-stop-limit
filled-amount       | string    | The amount which has been filled
filled-cash-amount  | string    | The filled total in quote currency
filled-fees         | string    | Transaction fee paid so far
source              | string    | The source where the order was triggered, possible values: sys, web, api, app
state               | string    | created, submitted, partial-filled, filled, canceled, partial-canceled
exchange            | string    | Internal data
batch               | string    | Internal data
stop-price|string|trigger price of stop limit order
operator|string|operation character of stop price

### Error code for invalid start-date/end-date

|err-code| scenarios|
|--------|---------------------------------------------------------------|
|invalid_interval| Start date is later than end date; the date between start date and end date is greater than 2 days|
|invalid_start_date| Start date is a future date; or start date is earlier than 180 days ago.|
|invalid_end_date| end date is a future date; or end date is earlier than 180 days ago.|



## Search Historical Orders within 48 Hours

API Key Permission：Read

This endpoint returns orders based on a specific searching criteria.
Note: queriable range should be within past 1 day for cancelled order (state = "canceled") 

### HTTP Request

`GET https://api.huobi.pro/v1/order/history`

```json
{
   "symbol": "btcusdt",
   "start-time": "1556417645419",
   "end-time": "1556533539282",
   "direct": "prev",
   "size": "10"
}
```

### Request Parameters

Parameter  | Required | Data Type | Description | Default Value                                  | Value Range
---------  | --------- | -------- | ------- | -----------                                   | ----------
symbol     | false  | string | The trading symbol to trade      |all      |All supported trading symbol, e.g. btcusdt, bccbtc.Refer to `GET /v1/common/symbols` |
start-time      | false | long | Start time (included)   |The time 48 hours ago      |UTC time in millisecond |
end-time | false | long | End time (included)  | The query time     |UTC time in millisecond |
direct   | false | string | Direction of the query. (Note: If the total number of items in the search result is within the limitation defined in “size”, this field does not take effect.)| next     |prev, next   |
size     | false  | int | Number of items in each response  |100      | [10,1000] |



> The above command returns JSON structured like this:

```json
{
    "status": "ok",
    "data": [
        {
            "id": 31215214553,
            "symbol": "btcusdt",
            "account-id": 4717043,
            "amount": "1.000000000000000000",
            "price": "1.000000000000000000",
            "created-at": 1556533539282,
            "type": "buy-limit",
            "field-amount": "0.0",
            "field-cash-amount": "0.0",
            "field-fees": "0.0",
            "finished-at": 1556533568953,
            "source": "web",
            "state": "canceled",
            "canceled-at": 1556533568911
        }
    ]
}
```

### Response Content

Field               | Data Type | Description
---------           | --------- | -----------
{account-id         | long      | Account ID
amount              | string    | Order size
canceled-at             | long   | Order cancellation time
created-at              | long    | Order creation time
field-amount              | string    | Executed order amount
field-cash-amount               | string    | Executed cash amount
field-fees          | string       | Transaction fee
finished-at         | long       | Last trade time
id         | long       | Order ID
price                | string   | Order price
source       | string    | Order source
state  | string    | Order status ( filled, partial-canceled, canceled )
symbol         | string    | Trading symbol
stop-price|string|trigger price of stop limit order
operator|string|operation character of stop price
type}              | string    | Order type (buy-market, sell-market, buy-limit, sell-limit, buy-ioc, sell-ioc, buy-limit-maker, sell-limit-maker, buy-stop-limit, sell-stop-limit)
next-time               | long    | Next query “start-time” (in response of “direct” = prev), Next query “end-time” (in response of “direct” = next). Note: Only when the total number of items in the search result exceeded the limitation defined in “size”, this field exists. UTC time in millisecond. 


## Search Match Results

API Key Permission：Read

This endpoint returns the match results of past and open orders based on specific search criteria.

### HTTP Request

`GET https://api.huobi.pro/v1/order/matchresults`

```shell
curl "https://api.huobi.pro/v1/order/matchresults?symbol=ethusdt"
```

### Request Parameters

Parameter  | Data Type | Required | Default | Description                                   | Value Range
---------  | --------- | -------- | ------- | -----------                                   | ----------
symbol     | string    | true     | NA      | The trading symbol to trade                   | All supported trading symbol, e.g. btcusdt, bccbtc.Refer to `GET /v1/common/symbols`
types      | string    | false    | all      | The types of order to include in the search   | buy-market, sell-market, buy-limit, sell-limit, buy-ioc, sell-ioc, buy-limit-maker, sell-limit-maker, buy-stop-limit, sell-stop-limit
states     | string    | false    | NA      | The states of order to include in the search  | submitted, partial-filled, partial-canceled, filled, canceled
start-date | string    | false    | -1d    | Search starts date, in format yyyy-mm-dd      |Value range [((end-date) – 1), (end-date)], maximum query window size is 2 days, query window shift should be within past 61 days |
end-date   | string    | false    | today   | Search ends date, in format yyyy-mm-dd        |Value range [(today-60), today], maximum query window size is 2 days, query window shift should be within past 61 days|
from       | string    | false    | NA      | Search internal id to begin with                 | NA
direct     | string    | false    | both    | Search direction when 'from' is used          | next, prev
size       | int       | false    | 100     | The number of orders to return                | [1, 100]

> The above command returns JSON structured like this:

```json
  "data": [
    {
      "id": 29553,
      "order-id": 59378,
      "match-id": 59335,
      "symbol": "ethusdt",
      "type": "buy-limit",
      "source": "api",
      "price": "100.1000000000",
      "filled-amount": "9.1155000000",
      "filled-fees": "0.0182310000",
      "created-at": 1494901400435,
      "trade-id": 100282808529,
      "role": "taker",
      "filled-points": "0.0",
      "fee-deduct-currency": ""
    }
  ]
```

### Response Content

<aside class="notice">The return data contains a list and each item in the list represents a match result</aside>
Field               | Data Type | Description
---------           | --------- | -----------
id                  | integer   | Internal id
symbol              | string    | The trading symbol to trade, e.g. btcusdt, bccbtc
order-id            | string    | The order id of this order
match-id            | string    | The match id of this match
trade-id            | int    | Unique trade ID (NEW)
price               | string    | The limit price of limit order
created-at          | int       | The timestamp in milliseconds when the match and fill is done
type                | string    | The order type, possible values are: buy-market, sell-market, buy-limit, sell-limit, buy-ioc, sell-ioc, buy-limit-maker, sell-limit-maker, buy-stop-limit, sell-stop-limit
filled-amount       | string    | The amount which has been filled
filled-fees         | string    | Transaction fee paid so far
source              | string    | The source where the order was triggered, possible values: sys, web, api, app
role                  | string   | The role in the transaction: taker or maker.
filled-points      | string   | deduction amount (unit: in ht or hbpoint)  
fee-deduct-currency      | string   | deduction type: ht or hbpoint.    

### Error code for invalid start-date/end-date

|err-code| scenarios|
|--------|---------------------------------------------------------------|
|invalid_interval| Start date is later than end date; the date between start date and end date is greater than 2 days|
|invalid_start_date| Start date is a future date; or start date is earlier than 61 days ago.|
|invalid_end_date| end date is a future date; or end date is earlier than 61 days ago.|



## Get Current Fee Rate Applied to The User

This endpoint returns the current transaction fee rate applied to the user.

API Key Permission：Read

```shell
curl "https://api.huobi.pro/v1/fee/fee-rate/get?symbols=btcusdt,ethusdt,ltcusdt"
```

### HTTP Request

`GET /v1/fee/fee-rate/get`

### Request Parameters

Parameter | Data Type | Required | Default | Description                 | Value Range
--------- | --------- | -------- | ------- | -----------                 | -----------
symbols    | string    | true     | NA      | The trading symbols to query, separated by comma | Refer to `GET /v1/common/symbols`

> Response:

```json
 {
  "status": "ok",
  "data": [
     {
        "symbol": "btcusdt",
        "maker-fee":"0.0001",
        "taker-fee":"0.0002"
     },
     {
        "symbol": "ethusdt",
        "maker-fee":"0.002",
        "taker-fee":"0.002"
    },
     {
        "symbol": "ltcusdt",
        "maker-fee":"0.0015",
        "taker-fee":"0.0018"
    }
  ]
}
```

### Response Content

Field Name      | Data Type | Mandatory| Description
--------- | --------- | -----------| -----------
status        | string  |Y | status code
err-code    | string   |N  | error code
err-msg     | string |N   | error message
data|list|Y| Fee rate list

### List
Field Name|	Datat Type|	Description
--------- | --------- | ------
symbol|	string|	trading symbol
maker-fee|	string|	maker fee rate
taker-fee|	string|	taker fee rate

### Error Code
Error Code|	Description|	Data Type|	Remark
--------- | --------- | ------ | ------
base-symbol-error|	invalid symbol|	string|	-
base-too-many-symbol|	exceeded maximum number of symbols|	string|	-



# Margin Loan (isolated margin mode)

<aside class="notice">All endpoints in this section require authentication</aside>
<aside class="notice">Currently loan only supports base currency of USDT, HUSD, and BTC</aside>
## Transfer Asset from Spot Trading Account to Isolated Margin Account

API Key Permission：Trade

This endpoint transfer specific asset from spot trading account to isolated margin account.

### HTTP Request

`POST https://api.huobi.pro/v1/dw/transfer-in/margin`

```shell
curl -X POST -H 'Content-Type: application/json' "https://api.huobi.pro/v1/dw/transfer-in/margin" -d
'{
  "symbol": "ethusdt",
  "currency": "eth",
  "amount": "1.0"
}'
```

### Request Parameters

Parameter  | Data Type | Required | Default | Description
---------  | --------- | -------- | ------- | -----------
symbol     | string    | true     | NA      | The trading symbol, e.g. btcusdt, bccbtc
currency   | string    | true     | NA      | The currency to transfer
amount     | string    | true     | NA      | The amount of currency to transfer

> The above command returns JSON structured like this:

```json
  "data": 1000
```

### Response Content

<aside class="notice">The return data contains a single value instead of an object</aside>
Field               | Data Type | Description
---------           | --------- | -----------
data                | integer   | Transfer id

## Transfer Asset from Isolated Margin Account to Spot Trading Account

API Key Permission：Trade

This endpoint transfer specific asset from isolated margin account to spot trading account.

### HTTP Request

`POST https://api.huobi.pro/v1/dw/transfer-out/margin`

```shell
curl -X POST -H 'Content-Type: application/json' "https://api.huobi.pro/v1/dw/transfer-out/margin" -d
'{
  "symbol": "ethusdt",
  "currency": "eth",
  "amount": "1.0"
}'
```

### Request Parameters

Parameter  | Data Type | Required | Default | Description
---------  | --------- | -------- | ------- | -----------
symbol     | string    | true     | NA      | The trading symbol, e.g. btcusdt, bccbtc
currency   | string    | true     | NA      | The currency to transfer
amount     | string    | true     | NA      | The amount of currency to transfer

> The above command returns JSON structured like this:

```json
  "data": 1000
```

### Response Content

<aside class="notice">The return data contains a single value instead of an object</aside>
Field               | Data Type | Description
---------           | --------- | -----------
data                | integer   | Transfer id

## Get Loan Interest Rate and Quota

API Key Permission: Read

The endpoint returns loan interest rates and quota applied on the user.

### HTTP Request

- GET ` /v1/margin/loan-info`

```shell
curl "https://api.huobi.pro/v1/margin/loan-info?symbols=btcusdt"
```

### Request Parameters

Parameter  | Data Type | Required | Default | Description
---------  | --------- | -------- | ------- | -----------
symbols     | string    | false     | all      | Trading symbol (multiple selections acceptable, separated by comma)

> Response:

```json
{
    "status": "ok",
    "data": 
        {
            "symbol": "btcusdt",
            "currencies": [
                {
                    "currency": "btc",
                    "interest-rate": "0.00098",
                    "min-loan-amt": "0.020000000000000000",
                    "max-loan-amt": "550.000000000000000000",
                    "loanable-amt": "0.045696000000000000"
                },
                {
                    "currency": "usdt",
                    "interest-rate": "0.00098",
                    "min-loan-amt": "100.000000000000000000",
                    "max-loan-amt": "4000000.000000000000000000",
                    "loanable-amt": "400.000000000000000000"
                }
            ]
        }
}
```

### Response Content

Field | Data Type | Description
------ | ------- | -----
{ symbol|string|Trading symbol
  currencies   | object | 
  { currencies   | string | Currency
interest-rate|string|Basic daily interest rate
min-loan-amt|string|Minimal loanable amount
max-loan-amt|string|Maximum loanable amount
loanable-amt }}|string|Remaining loanable amount

## Request a Margin Loan

API Key Permission：Trade

This endpoint place an order to apply a margin loan.

### HTTP Request

`POST https://api.huobi.pro/v1/margin/orders`

```shell
curl -X POST -H 'Content-Type: application/json' "https://api.huobi.pro/v1/margin/orders" -d
'{
  "symbol": "ethusdt",
  "currency": "eth",
  "amount": "1.0"
}'
```

### Request Parameters

Parameter  | Data Type | Required | Default | Description
---------  | --------- | -------- | ------- | -----------
symbol     | string    | true     | NA      | The trading symbol to borrow margin, e.g. btcusdt, bccbtc
currency   | string    | true     | NA      | The currency to borrow
amount     | string    | true     | NA      | The amount of currency to borrow (precision: 3 decimal places)

> The above command returns JSON structured like this:

```json
  {
    "status": "ok"
    "data": 1000
  }
```

### Response Content

<aside class="notice">The return data contains a single value instead of an object</aside>
Field               | Data Type | Description
---------           | --------- | -----------
status | string | Status 
data                | integer   | Margin order id

## Repay Margin Loan

API Key Permission：Trade

This endpoint repays margin loan with you asset in your margin account.

### HTTP Request

`POST https://api.huobi.pro/v1/margin/orders/{order-id}/repay`

'order-id': the previously returned order id when loan order was created

```shell
curl -X POST -H 'Content-Type: application/json' "https://api.huobi.pro/v1/margin/orders/1000/repay" -d
'{
  "amount": "1.0"
}'
```

### Request Parameters

Parameter  | Data Type | Required | Default | Description
---------  | --------- | -------- | ------- | -----------
amount     | string    | true     | NA      | The amount of currency to repay

> The above command returns JSON structured like this:

```json
  "data": 1000
```

### Response Content

<aside class="notice">The return data contains a single value instead of an object</aside>
Field               | Data Type | Description
---------           | --------- | -----------
data                | integer   | Margin order id

## Search Past Margin Orders

API Key Permission：Read

This endpoint returns margin orders based on a specific searching criteria.

### HTTP Request

`GET https://api.huobi.pro/v1/margin/loan-orders`

```shell
curl "https://api.huobi.pro/v1/margin/load-orders?symbol=ethusdt"
```

### Request Parameters

Parameter  | Data Type | Required | Default | Description                                   | Value Range
---------  | --------- | -------- | ------- | -----------                                   | ----------
symbol     | string    | true     | NA      | The trading symbol to trade                   | The trading symbol, e.g. btcusdt, bccbtc
states     | string    | false    | NA      | Order status  | created,accrual,cleared,invalid
start-date | string    | false    | -61d    | Search starts date, in format yyyy-mm-dd      | NA
end-date   | string    | false    | today   | Search ends date, in format yyyy-mm-dd        | NA
from       | string    | false    | NA      | Search order id to begin with                 | NA
direct     | string    | false    | both    | Search direction when 'from' is used          | next, prev
size       | int       | false    | 100     | The number of orders to return                | [1, 100]
sub-uid       | int       | false    | If not entered, by default it returns margin orders of current user     | Sub user ID (mandatory field while parent user querying sub user’s orders)                |

> The above command returns JSON structured like this:

```json
  "data": [
    {
      "loan-balance": "0.100000000000000000",
      "interest-balance": "0.000200000000000000",
      "interest-rate": "0.002000000000000000",
      "loan-amount": "0.100000000000000000",
      "accrued-at": 1511169724531,
      "interest-amount": "0.000200000000000000",
      "symbol": "ethbtc",
      "currency": "btc",
      "id": 394,
      "state": "accrual",
      "account-id": 17747,
      "user-id": 119913,
      "created-at": 1511169724531
    }
  ]
```

### Response Content

Field               | Data Type | Description
---------           | --------- | -----------
id                  | integer   | Order id
account-id          | integer   | Account id
user-id             | integer   | User id
symbol              | string    | The margin loan pair to trade, e.g. btcusdt, bccbtc
currency            | string    | The currency in the loan
created-at          | int       | The timestamp in milliseconds when the order was created
accrued-at          | int       | The timestamp in milliseconds when the last accure happened
loan-amount         | string    | The amount of the origin loan
loan-balance        | string    | The amount of the loan left
interest-rate       | string    | The loan interest rate
interest-amount     | string    | The accumulated loan interest
interest-balance    | string    | The amount of loan interest left
state               | string    | Loan state, possible values: created, accrual, cleared, invalid

## Get the Balance of the Margin Loan Account

API Key Permission：Read

This endpoint returns the balance of the margin loan account.

### HTTP Request

`GET https://api.huobi.pro/v1/margin/accounts/balance`

```shell
curl "https://api.huobi.pro/v1/margin/accounts/balance?symbol=btcusdt"
```

### Request Parameters

Parameter  | Data Type | Required | Default | Description
---------  | --------- | -------- | ------- | -----------
symbol     | string    | true     | NA      | The trading symbol, e.g. btcusdt, bccbtc
sub-uid     | int    | false     | If not entered, by default it returns margin account details of current user      | Sub user ID (mandatory field while parent user querying sub user’s margin account details)

> The above command returns JSON structured like this:

```json
"data": [
        {
            "id": 18264,
            "type": "margin",
            "state": "working",
            "symbol": "btcusdt",
            "fl-price": "0",
            "fl-type": "safe",
            "risk-rate": "475.952571086994250554",
            "list": [
                {
                    "currency": "btc",
                    "type": "trade",
                    "balance": "1168.533000000000000000"
                },
                {
                    "currency": "btc",
                    "type": "frozen",
                    "balance": "0.000000000000000000"
                },
                {
                    "currency": "btc",
                    "type": "loan",
                    "balance": "-2.433000000000000000"
                },
                {
                    "currency": "btc",
                    "type": "interest",
                    "balance": "-0.000533000000000000"
                },
                {
                    "currency": "btc",
                    "type": "transfer-out-available",//可转btc
                    "balance": "1163.872174670000000000"
                },
                {
                    "currency": "btc",
                    "type": "loan-available",//可借btc
                    "balance": "8161.876538350676000000"
                }
            ]
        }
]
```

### Response Content

Field               | Data Type     | Description
---------           | ---------     | -----------
symbol              | string        | The margin loan pair, e.g. btcusdt, bccbtc
state               | string        | Loan state, possible values: created, accrual, cleared, invalid
risk-rate           | string        | The risk rate
fl-price            | string        | The price which triggers closeout
list                | array         | The list of margin accounts and their details



# Margin Loan (cross margin mode)

<aside class="notice">All endpoints in this section require authentication</aside>
<aside class="notice">Currently loan only supports base currency of USDT and BTC</aside>
<aside class="notice">Once completed a margin loan or transfer, please wait for 10 seconds before requesting for next margin loan or transfer.</aside>
## Transfer Asset from Spot Trading Account to Cross Margin Account

API Key Permission：Trade

This endpoint transfer specific asset from spot trading account to cross margin account.

### HTTP Request

`POST https://api.huobi.pro/v1/cross-margin/transfer-in`

```shell
curl -X POST -H 'Content-Type: application/json' "https://api.huobi.pro/v1/cross-margin/transfer-in" -d
'{
  "currency": "eth",
  "amount": "1.0"
}'
```

### Request Parameters

Parameter  | Data Type | Required | Default | Description
---------  | --------- | -------- | ------- | -----------
currency     | string    | true     | NA      | Currency
amount     | string    | true     | NA      | Transfer amount

> The above command returns JSON structured like this:

```json
{  
  "status": "ok",
  "data": 1000
}
```

### Response Content

<aside class="notice">The return data contains a single value instead of an object</aside>
Field               | Data Type | Description
---------           | --------- | -----------
data                | integer   | Transfer id

## Transfer Asset from Cross Margin Account to Spot Trading Account

API Key Permission：Trade

This endpoint transfer specific asset from cross margin account to spot trading account.

### HTTP Request

`POST https://api.huobi.pro/v1/cross-margin/transfer-out`

```shell
curl -X POST -H 'Content-Type: application/json' "https://api.huobi.pro/v1/cross-margin/transfer-out" -d
'{
  "currency": "eth",
  "amount": "1.0"
}'
```

### Request Parameters

Parameter  | Data Type | Required | Default | Description
---------  | --------- | -------- | ------- | -----------
currency   | string    | true     | NA      | Currency
amount     | string    | true     | NA      | Transfer amount

> The above command returns JSON structured like this:

```json
{  
  "status": "ok",
  "data": 1000
}
```

### Response Content

<aside class="notice">The return data contains a single value instead of an object</aside>
Field               | Data Type | Description
---------           | --------- | -----------
data                | integer   | Transfer id

## Get Loan Interest Rate and Quota

API Key Permission: Read

This endpoint returns loan interest rates and loan quota applied on the user.

### HTTP Request

- GET ` /v1/cross-margin/loan-info`

```shell
curl "https://api.huobi.pro/v1/cross-margin/loan-info"
```

### Request Parameters

Null

> Response:

```json
{
    "status": "ok",
    "data": [
        {
            "currency": "bch",
            "interest-rate": "0.00098",
            "min-loan-amt": "0.35",
            "max-loan-amt": "3500",
            "loanable-amt": "0.70405181",
            "actual-rate": "0.000343"
        },
        {
            "currency": "btc",
            "interest-rate": "0.00098",
            "min-loan-amt": "0.01",
            "max-loan-amt": "100",
            "loanable-amt": "0.02281914",
            "actual-rate": "0.000343"
        },
        {
            "currency": "eos",
            "interest-rate": "0.00098",
            "min-loan-amt": "30",
            "max-loan-amt": "300000",
            "loanable-amt": "57.69175296",
            "actual-rate": "0.000343"
        },
        {
            "currency": "eth",
            "interest-rate": "0.00098",
            "min-loan-amt": "0.5",
            "max-loan-amt": "6000",
            "loanable-amt": "1.06712197",
            "actual-rate": "0.000343"
        },
        {
            "currency": "ltc",
            "interest-rate": "0.00098",
            "min-loan-amt": "1.5",
            "max-loan-amt": "15000",
            "loanable-amt": "3.28947368",
            "actual-rate": "0.000343"
        },
        {
            "currency": "usdt",
            "interest-rate": "0.00098",
            "min-loan-amt": "100",
            "max-loan-amt": "1500000",
            "loanable-amt": "200.00000000",
            "actual-rate": "0.000343"
        },
        {
            "currency": "xrp",
            "interest-rate": "0.00098",
            "min-loan-amt": "380",
            "max-loan-amt": "4000000",
            "loanable-amt": "734.21439060",
            "actual-rate": "0.000343"
        }
    ]
}
```

### Response Content

Field | Data Type | Description
------ | ------- | -----
{ currency   | string | Currency
interest-rate|string|Basic daily interest rate
min-loan-amt|string|Minimal loanable amount
max-loan-amt|string|Maximum loanable amount
loanable-amt |string|Remaining loanable amount
actual-rate }|string|Actual interest rate post deduction (if deduction is inapplicable or disabled, return basic daily interest rate)

## Request a Margin Loan

API Key Permission：Trade

This endpoint place an order to apply a margin loan.

### HTTP Request

`POST https://api.huobi.pro/v1/cross-margin/orders`

```shell
curl -X POST -H 'Content-Type: application/json' "https://api.huobi.pro/v1/cross-margin/orders" -d
'{
  "currency": "eth",
  "amount": "1.0"
}'
```

### Request Parameters

Parameter  | Data Type | Required | Default | Description
---------  | --------- | -------- | ------- | -----------
currency   | string    | true     | NA      | The currency to borrow
amount     | string    | true     | NA      | The amount of currency to borrow (precision: 3 decimal places)

> The above command returns JSON structured like this:

```json
{  
  "status": "ok",
  "data": 1000
}
```

### Response Content

<aside class="notice">The return data contains a single value instead of an object</aside>
Field               | Data Type | Description
---------           | --------- | -----------
data                | integer   | Margin order id

## Repay Margin Loan

API Key Permission：Trade

This endpoint repays margin loan with you asset in your margin account.

### HTTP Request

`POST https://api.huobi.pro/v1/cross-margin/orders/{order-id}/repay`

'order-id': the previously returned order id when loan order was created

```shell
curl -X POST -H 'Content-Type: application/json' "https://api.huobi.pro/v1/cross-margin/orders/1000/repay" -d
'{
  "amount": "1.0"
}'
```

### Request Parameters

Parameter  | Data Type | Required | Default | Description
---------  | --------- | -------- | ------- | -----------
amount     | string    | true     | NA      | The amount of currency to repay

> The above command returns JSON structured like this:

```json
{  
  "status": "ok",
  "data": null
}
```

### Response Content

<aside class="notice">The return data contains a single value instead of an object</aside>
Field               | Data Type | Description
---------           | --------- | -----------
data                | null   | NA

## Search Past Margin Orders

API Key Permission：Read

This endpoint returns margin orders based on a specific searching criteria.

### HTTP Request

`GET https://api.huobi.pro/v1/cross-margin/loan-orders`

```shell
curl "https://api.huobi.pro/v1/cross-margin/loan-orders?symbol=ethusdt"
```

### Request Parameters

Parameter  | Data Type | Required | Default | Description                                   | Value Range
---------  | --------- | -------- | ------- | -----------                                   | ----------
start-date | string    | false    | -61d    | Search starts date, in format yyyy-mm-dd      | NA
end-date   | string    | false    | today   | Search ends date, in format yyyy-mm-dd        | NA
currency   | string    | false    | NA   | Currency        | NA
state   | string    | false    | all   | Order status        | created,accrual,cleared,invalid
from       | string    | false    | 0     | Search order id to begin with                 | NA
direct     | string    | false    | next    | Search direction when 'from' is used          | next, prev
size       | string       | false    | 10     | The number of orders to return                | [10,100]

> The above command returns JSON structured like this:

```json
{  
  "status": "ok",
  "data": [
    {
      "loan-balance": "0.100000000000000000",
      "interest-balance": "0.000200000000000000",
      "loan-amount": "0.100000000000000000",
      "accrued-at": 1511169724531,
      "interest-amount": "0.000200000000000000",
      "filled-points" : "0.2",
      "filled-ht" : "0.2",
      "currency": "btc",
      "id": 394,
      "state": "accrual",
      "account-id": 17747,
      "user-id": 119913,
      "created-at": 1511169724531
    }
  ]
}
```

### Response Content

Field               | Data Type | Description
---------           | --------- | -----------
id                  | integer   | Order id
account-id          | integer   | Account id
user-id             | integer   | User id
currency            | string    | The currency in the loan
filled-points            | string    | Point deduction amount
filled-ht            | string    | HT deduction amount
created-at          | int       | The timestamp in milliseconds when the order was created
accrued-at          | int       | The timestamp in milliseconds when the last accure happened
loan-amount         | string    | The amount of the origin loan
loan-balance        | string    | The amount of the loan left
interest-amount     | string    | The accumulated loan interest
interest-balance    | string    | The amount of loan interest left
state               | string    | Loan state, possible values: created, accrual, cleared, invalid

## Get the Balance of the Margin Loan Account

API Key Permission：Read

This endpoint returns the balance of the margin loan account.

### HTTP Request

`GET https://api.huobi.pro/v1/cross-margin/accounts/balance`

```shell
curl "https://api.huobi.pro/v1/cross-margin/accounts/balance?symbol=btcusdt"
```

### Request Parameters

Null

> The above command returns JSON structured like this:

```json
{  
  "status": "ok",
  "data": 
    {
      "id": 18264,
      "type": "cross-margin",
      "state": "working",
      "risk-rate": "1000",
      "acct-balance-sum": "12312.123123",
      "debt-balance-sum": "1231.2123123",
      "list": [
          {
              "currency": "btc",
              "type": "trade",
              "balance": "1168.533000000000000000"
          },
          {
              "currency": "btc",
              "type": "frozen",
              "balance": "0.000000000000000000"
          },
          {
              "currency": "btc",
              "type": "loan",
              "balance": "-2.433000000000000000"
          },
          {
              "currency": "btc",
              "type": "interest",
              "balance": "-0.000533000000000000"
          },
          {
              "currency": "btc",
              "type": "transfer-out-available",//可转btc
              "balance": "1163.872174670000000000"
          },
          {
              "currency": "btc",
              "type": "loan-available",//可借btc
              "balance": "8161.876538350676000000"
          }
      ]
    }
}
```

### Response Content

Field               | Data Type     | Description
---------           | ---------     | -----------
 id | true | integer | Account ID  | |
 type | true | integer | Account type (margin or cross-margin) |cross-margin |
 state  |  true  |  string  |  Account status | working,fl-sys,fl-end,fl-negative |
 risk-rate | true | string | Risk rate| |
 acct-balance-sum | true | string | Account balance totaled in USDT | |
 debt-balance-sum | true | string | Debt balance totaled in USDT | |
 list | true | array | Account layout by individual currency | |
 { currency | true | string | Currency| |
   type | true | string | Account type| trade,frozen,loan,interest,transfer-out-available,loan-available|
   balance } | true | string | Balance (note: while type=transfer-out-available, if balance=-1, it implicates that all balance can be transferred out.)| |


# Websocket Market Data

## General

### Websocket URL

**Websocket Market Feed**

**`wss://api.huobi.pro/ws`**
or
**`wss://api-aws.huobi.pro/ws`**


### Data Format

All return data of websocket APIs are compressed with GZIP so they need to be unzipped.

### Heartbeat and Connection

After connected to Huobi's Websocket server, the server will send heartbeat periodically (currently at 5s interval). The heartbeat message will have an integer in it, e.g.

> {"ping": 1492420473027} (market data)

When client receives this heartbeat message, it should response with a matching "pong" message which has the same integer in it, e.g.

> {"pong": 1492420473027} (market data)

<aside class="warning">After the server sent two consecutive heartbeat messages without receiving at least one matching "pong" response from a client, then right before server sends the next "ping" heartbeat, the server will disconnect this client</aside>
### Subscribe to Topic

To receive data you have to send a "sub" message first.

```json
{
  "sub": "market.btcusdt.kline.1min",
  "id": "id1"
}
```

{
  "sub": "topic to sub",
  "id": "id generate by client"
}

After successfully subscribed, you will receive a response to confirm subscription

```json
{
  "id": "id1",
  "status": "ok",
  "subbed": "market.btcusdt.kline.1min",
  "ts": 1489474081631
}
```

Then, you will received message when there is update in this topic

```json
{
  "ch": "market.btcusdt.kline.1min",
  "ts": 1489474082831,
  "tick": {
    "id": 1489464480,
    "amount": 0.0,
    "count": 0,
    "open": 7962.62,
    "close": 7962.62,
    "low": 7962.62,
    "high": 7962.62,
    "vol": 0.0
  }
}
```

### Unsubscribe

To unsubscribe, you need to send below message

```json
{
  "unsub": "market.btcusdt.trade.detail",
  "id": "id4"
}
```

{
  "unsub": "topic to unsub",
  "id": "id generate by client"
}

And you will receive a message to confirm the unsubscribe

```json
{
  "id": "id4",
  "status": "ok",
  "unsubbed": "market.btcusdt.trade.detail",
  "ts": 1494326028889
}
```

### Pull Data

While connected to websocket, you can also use it in pull style by sending message to the server.

To request pull style data, you send below message

```json
{
  "req": "market.ethbtc.kline.1min",
  "id": "id10"
}
```

{
  "req": "topic to req",
  "id": "id generate by client"
}

You will receive a response accordingly and immediately

```json
{
  "status": "ok",
  "rep": "market.btcusdt.kline.1min",
  "data": [
    {
      "amount": 1.6206,
      "count":  3,
      "id":     1494465840,
      "open":   9887.00,
      "close":  9885.00,
      "low":    9885.00,
      "high":   9887.00,
      "vol":    16021.632026
    },
    {
      "amount": 2.2124,
      "count":  6,
      "id":     1494465900,
      "open":   9885.00,
      "close":  9880.00,
      "low":    9880.00,
      "high":   9885.00,
      "vol":    21859.023500
    }
  ]
}
```

## Market Candlestick

This topic sends a new candlestick whenever it is available.

### Topic

`market.$symbol$.kline.$period$`

> Subscribe request

```json
{
  "sub": "market.ethbtc.kline.1min",
  "id": "id1"
}
```

### Topic Parameter

Parameter | Data Type | Required | Description                      | Value Range
--------- | --------- | -------- | -----------                      | -----------
symbol    | string    | true     | Trading symbol     | All supported trading symbol, e.g. btcusdt, bccbtc.Refer to `GET /v1/common/symbols`
period     | string    | true     | Candlestick interval   | 1min, 5min, 15min, 30min, 60min, 4hour, 1day, 1mon, 1week, 1year

> Response

```json
{
  "id": "id1",
  "status": "ok",
  "subbed": "market.ethbtc.kline.1min",
  "ts": 1489474081631
}
```

> Update example

```json
{
  "ch": "market.ethbtc.kline.1min",
  "ts": 1489474082831,
  "tick": {
    "id": 1489464480,
    "amount": 0.0,
    "count": 0,
    "open": 7962.62,
    "close": 7962.62,
    "low": 7962.62,
    "high": 7962.62,
    "vol": 0.0
  }
}
```

### Update Content

Field     | Data Type | Description
--------- | --------- | -----------
id        | integer   | UNIX epoch timestamp in second as response id
amount    | float     | Aggregated trading volume during the interval (in base currency)
count     | integer   | Number of trades during the interval
open      | float     | Opening price during the interval
close     | float     | Closing price during the interval
low       | float     | Low price during the interval
high      | float     | High price during the interval
vol       | float     | Aggregated trading value during the interval (in quote currency)

<aside class="notice">When symbol is set to "hb10" or "huobi10", amount, count, and vol will always have the value of 0</aside>
### Pull Request

Pull request is supported with extra parameters to define the range. The maximum number of ticks in each response is 300.

```json
{
  "req": "market.$symbol.kline.$period",
  "id": "id generated by client",
  "from": "from time in epoch seconds",
  "to": "to time in epoch seconds"
}
```

Parameter | Data Type | Required | Default Value                          | Description      | Value Range
--------- | --------- | -------- | -------------                          | -----------      | -----------
from      | integer   | false    | 1501174800(2017-07-28T00:00:00+08:00)  | "From" time (epoch time in second)   | [1501174800, 2556115200]
to        | integer   | false    | 2556115200(2050-01-01T00:00:00+08:00)  | "To" time (epoch time in second)      | [1501174800, 2556115200] or ($from, 2556115200] if "from" is set

## Market Depth

This topic sends the latest market by price order book in snapshot mode at 1-second interval.

### Topic

`market.$symbol.depth.$type`

> Subscribe request

```json
{
  "sub": "market.btcusdt.depth.step0",
  "id": "id1"
}
```

### Topic Parameter

Parameter | Data Type | Required | Default Value         | Description                                       | Value Range
--------- | --------- | -------- | -------------         | -----------                                       | -----------
symbol    | string    | true     | NA                    | Trading symbol                   | Refer to `GET /v1/common/symbols`
type      | string    | true     | step0                 | Market depth aggregation level, details below     | step0, step1, step2, step3, step4, step5

**"type" Details**

Value     | Description
--------- | ---------
step0     | No market depth aggregation
step1     | Aggregation level = precision*10
step2     | Aggregation level = precision*100
step3     | Aggregation level = precision*1000
step4     | Aggregation level = precision*10000
step5     | Aggregation level = precision*100000

While type is set as ‘step0’, the market depth data supports up to 150 levels.
While type is set as ‘step1’, ‘step2’, ‘step3’, ‘step4’, or ‘step5’, the market depth data supports up to 20 levels.

> Response

```json
{
  "id": "id1",
  "status": "ok",
  "subbed": "market.btcusdt.depth.step0",
  "ts": 1489474081631
}
```

> Update example

```json
{
  "ch": "market.htusdt.depth.step0",
  "ts": 1572362902027,
  "tick": {
    "bids": [
      [3.7721, 344.86],// [price, quote volume]
      [3.7709, 46.66]
    ],
    "asks": [
      [3.7745, 15.44],
      [3.7746, 70.52]
    ],
    "version": 100434317651,
    "ts": 1572362902012
  }
}
```

### Update Content

<aside class="notice">Under 'tick' object there is a list of bids and a list of asks</aside>
Field     | Data Type | Description
--------- | --------- | -----------
bids      | object    | The current all bids in format [price, quote volume]
asks      | object    | The current all asks in format [price, quote volume]
version   | integer   | Internal data
ts        | integer   | The UNIX timestamp in milliseconds adjusted to Singapore time

<aside class="notice">When symbol is set to "hb10" amount, count, and vol will always have the value of 0</aside>
### Pull Request

Pull request is supported.

```json
{
  "req": "market.btcusdt.depth.step0",
  "id": "id10"
}
```

## Market By Price (MBP)

User could subscribe to this channel to receive incremental update of Market By Price order book. Refresh message, the full image of the order book, is acquirable from the same channel, upon "req" request.

Suggested downstream data processing:<br>
1)	Subscribe incremental updates and start to cache them;<br>
2)	Request refresh message (with same number of levels), and base on its “seqNum” to align it with the cached incremental message which having a same “prevSeqNum”;<br>
3)	Start to continuously process incremental messages to build up MBP book;<br>
4)	The “prevSeqNum” of current incremental message must be same with “seqNum” of previous message, otherwise it implicates message loss which should require another round refresh message retrieval and alignment;<br>
5)	Once receiving a new price level from incremental message, that price level should be inserted into appropriate position of existing MBP book;<br>
6)	Once receiving an updated “size” at existing price level from incremental message, the level size should be replaced directly by the new value;<br>
7)	Once receiving a “size=0” at existing price level from incremental message, that price level should be removed from MBP book;<br>
8)	If one incremental message includes updates of multiple price levels, all of those levels should be updated simultaneously in MBP book.<br>

Currently Huobi Global only supports the incremental update at 100ms interval. Shorter interval even full tick MBP data is not acquirable at this point of time.

### Subscribe incremntal updates

`market.$symbol.mbp.$levels`

> Sub request

```json
{
  "sub": "market.btcusdt.mbp.150",
  "id": "id1"
}
```

### Request refresh update

`market.$symbol.mbp.$levels`

> Req request

```json
{
  "req": "market.btcusdt.mbp.150",
  "id": "id2"
}
```

### Parameters

Field Name | Data Type | Mandatory | Default Value         | Description                                       | Value Range
--------- | --------- | -------- | -------------         | -----------                                       | -----------
symbol    | string    | true     | NA                    | Trading symbol (wildcard inacceptable)| Only support 19 currency pairs at this point of time - btcusdt, ethusdt, eosusdt, bchusdt, ltcusdt, xrpusdt, htusdt, bsvusdt, etcusdt, zecusdt, ethbtc, eosbtc, bchbtc, ltcbtc, xrpbtc, htbtc, bsvbtc, etcbtc, zecbtc.
levels      | integer    | true     | NA                 | Number of price levels (Valid value: 150)     | Only support the number of price levels at 150 at this point of time.

> Response (Incremental update subscription)

```json
{
  "id": "id1",
  "status": "ok",
  "subbed": "market.btcusdt.mbp.150",
  "ts": 1489474081631
}
```

> Incremental Update (Incremental update subscription)

```json
{
	"ch": "market.btcusdt.mbp.150",
	"ts": 1573199608679,
	"tick": {
		"seqNum": 100020146795,
		"prevSeqNum": 100020146794,
		"bids": [],
		"asks": [
			[645.140000000000000000, 26.755973959140651643] // [price, size]
		]
	}
}
```

> Response (Refresh update acquisition)

```json
{
	"id": "id2",
	"rep": "market.btcusdt.mbp.150",
	"status": "ok",
	"data": {
		"seqNum": 100020142010,
		"bids": [
			[618.37, 71.594], // [price, size]
			[423.33, 77.726],
			[223.18, 47.997],
			[219.34, 24.82],
			[210.34, 94.463], ... // Rest 145 levels ignored here
    ],
		"asks": [
			[650.59, 14.909733438479636],
			[650.63, 97.996],
			[650.77, 97.465],
			[651.23, 83.973],
			[651.42, 34.465], ... // Rest 145 levels ignored here
		]
	}
}
```

### Update Content

Field Name     | Data Type | Description
--------- | --------- | -----------
seqNum   | integer   | Sequence number of the message
prevSeqNum        | integer   | Sequence number of previous message 
bids      | string[]    | Bid side, (in descending order of “price”), ["price","size"]
asks      | string[]    | Ask side, (in ascending order of “price”), ["price","size"]

## Best Bid/Offer

While any of best bid, best ask, best bid size, best ask size is changing, subscriber can receive BBO (Best Bid/Offer) update in tick by tick mode.

### Topic

`market.$symbol.bbo`

> Subscribe request

```json
{
  "sub": "market.btcusdt.bbo",
  "id": "id1"
}
```

### Topic parameter

Parameter | Data Type | Required | Default Value         | Description                                       | Value Range
--------- | --------- | -------- | -------------         | -----------                                       | -----------
symbol    | string    | true     | NA                    | Trading symbol                   | Refer to `GET /v1/common/symbols`

> Response

```json
{
  "id": "id1",
  "status": "ok",
  "subbed": "market.btcusdt.bbo",
  "ts": 1489474081631
}
```

> Update example

```json
{
  "ch": "market.btcusdt.bbo",
  "ts": 1489474082831,
  "tick": {
    "symbol": "btcusdt",
    "quoteTime": "1489474082811",
    "bid": "10008.31",
    "bidSize": "0.01",
    "ask": "10009.54",
    "askSize": "0.3"
  }
}
```

### Update Content

Field     | Data Type | Description
--------- | --------- | -----------
symbol     | string    | Trading symbol
quoteTime      | long    | Quote time
bid      | float    | Best bid
bidSize      | float    | Best bid size
ask      | float    | Best ask
askSize      | float    | Best ask size


## Trade Detail

This topic sends the latest completed trade. It updates in tick by tick mode.

### Topic

`market.$symbol.trade.detail`

> Subscribe request

```json
{
  "sub": "market.btcusdt.trade.detail",
  "id": "id1"
}
```

### Topic Parameter

Parameter | Data Type | Required | Default Value         | Description                                       | Value Range
--------- | --------- | -------- | -------------         | -----------                                       | -----------
symbol    | string    | true     | NA                    | Trading symbol                     | Refer to `GET /v1/common/symbols`

> Response

```json
{
  "id": "id1",
  "status": "ok",
  "subbed": "market.btcusdt.trade.detail",
  "ts": 1489474081631
}
```

> Update example

```json
{
  "ch": "market.btcusdt.trade.detail",
  "ts": 1489474082831,
  "tick": {
        "id": 14650745135,
        "ts": 1533265950234,
        "data": [
            {
                "amount": 0.0099,
                "ts": 1533265950234,
                "id": 146507451359183894799,
                "tradeId": 102043495674,
                "price": 401.74,
                "direction": "buy"
            }
            // more Trade Detail data here
        ]
  }
}
```

### Update Content

Field     | Data Type | Description
--------- | --------- | -----------
id        | integer   | Unique trade id (to be obsoleted)
tradeId|integer| Unique trade id (NEW)
amount    | float     | Last trade volume
price     | float     | Last trade price
ts        | integer   | Last trade time (UNIX epoch time in millisecond)
direction | string    | Aggressive order side (taker's order side) of the trade: 'buy' or 'sell'

### Pull Request

Pull request (of maximum latest 300 trade records) is supported.

```json
{
  "req": "market.btcusdt.trade.detail",
  "id": "id11"
}
```

## Market Details

This topic sends the latest market stats with 24h summary. It updates in snapshot mode, in frequency of no more than 10 times per second.

### Topic

`market.$symbol.detail`

> Subscribe request

```json
{
  "sub": "market.btcusdt.detail",
  "id": "id1"
}
```

### Topic Parameter

Parameter | Data Type | Required | Default Value         | Description                                       | Value Range
--------- | --------- | -------- | -------------         | -----------                                       | -----------
symbol    | string    | true     | NA                    | Trading symbol                     | Refer to `GET /v1/common/symbols`

> Response

```json
{
  "id": "id1",
  "status": "ok",
  "subbed": "market.btcusdt.detail",
  "ts": 1489474081631
}
```

> Update example

```json
  "tick": {
    "amount": 12224.2922,
    "open":   9790.52,
    "close":  10195.00,
    "high":   10300.00,
    "ts":     1494496390000,
    "id":     1494496390,
    "count":  15195,
    "low":    9657.00,
    "vol":    121906001.754751
  }
```

### Update Content

Field     | Data Type | Description
--------- | --------- | -----------
id        | integer   | UNIX epoch timestamp in second as response id
ts        | integer   | UNIX epoch timestamp in millisecond of this tick
amount    | float     | Aggregated trading volume in past 24H (in base currency)
count     | integer   | Number of trades in past 24H
open      | float     | Opening price in past 24H
close     | float     | Last price
low       | float     | Low price in past 24H
high      | float     | High price in past 24H
vol       | float     | Aggregated trading value in past 24H (in quote currency)

### Pull Request

Pull request is supported.

```json
{
  "req": "market.btcusdt.detail",
  "id": "id11"
}
```

# Websocket Asset and Order

## General

### Websocket URL

**Websocket Asset and Order**

**`wss://api.huobi.pro/ws/v1`**
or
**`wss://api-aws.huobi.pro/ws/v1`**


### Data Format

All return data of websocket APIs are compressed with GZIP so they need to be unzipped.

### Heartbeat and Connection

**After 2019/07/08**

After connected to Huobi's Websocket server, the server will send heartbeat periodically (at 20s interval). The heartbeat message will have an integer in it, e.g.

> {
    "op":"ping",
    "ts":1492420473027
}

When client receives this heartbeat message, it should response with a matching "pong" message which has the same integer in it, e.g.

> {
    "op":"pong",
    "ts":1492420473027
}

<aside class="warning">After the server sent THREE consective heartbeat messages without receiving at least one matching "pong" response from a client, then right before server sends the next "ping" heartbeat, the server will disconnect this client</aside>
**Prior to 2019/07/08**

After connected to Huobi's Websocket server, the server will send heartbeat periodically (at 30s interval). The heartbeat message will have an integer in it, e.g.

> {
    "op":"ping",
    "ts":1492420473027
}

When client receives this heartbeat message, it should response with a matching "pong" message which has the same integer in it, e.g.

> {
    "op":"pong",
    "ts":1492420473027
}

<aside class="warning">After the server sent two consective heartbeat message without receiving at least one matching "pong" response from a client, then right before server sends the next "ping" heartbeat, the server will disconnect this client</aside>
### Subscribe to Topic

To receive data you have to send a "sub" message first.

```json
{
  "op": "operation type, 'sub' for subscription, 'unsub' for unsubscription",
  "topic": "topic to sub",
  "cid": "id generate by client"
}
```

After successfully subscribed, you will receied a response to confirm subscription

```json
{
  "op": "operation type, refer to the operation which triggers this response",
  "cid": "id1",
  "error-code": 0, // 0 for no error
  "topic": "topic to sub if the op is sub",
  "ts": 1489474081631
}
```

Then, you will received message when there is update in this topic

```json
{
  "op": "notify",
  "topic": "topic of this notify",
  "ts": 1489474082831,
  "data": {
    // data of specific topic update
  }
}
```

### Unsubscribe

To unsubscribe, you need to send below message

```json
{
  "op": "unsub",
  "topic": "accounts",
  "cid": "client generated id"
}
```

And you will receive a message to confirm the unsubscribe

```json
{
  "op": "unsub",
  "topic": "accounts",
  "cid": "id generated by client",
  "err-code": 0,
  "ts": 1489474081631
}
```

### Pull Data

After successfully establishing a connection with the WebSocket API. There are 3 topics which are designed particularly for pull style data query. Those are

* accounts.list
* orders.list
* orders.detail

The details of how to user those three topic will be explain later in this documents.

### Rate Limit

**Rate limt of Subscription for a connection**

The limit is count againt per API key not per connection. When you reached the limit you will receive error with "too many request".

For a given single connection, 
1. maximum of 50 'sub' and 50‘unsub’ in one second. 
2. maximum of 100 sub allowed in total, and every 'unsub' would be deduct from total count of 'sub'. For example, there are 30 sub counts already, if 'unsub' once, then the total count of sub would be 29 for this given connection. When the limit of 100 'sub' reached, no more 'sub' would be allowed. 

**Rate limt of pull style query (req)**

The limit is count againt per API key not per connection. When you reached the limit you will receive error with "too many request".

* accounts.list: once every 2 seconds
* orders.list AND orders.detail: once every 5 seconds

### Authentication

Asset and Order topics require authentication. To authenticate yourself, send below message

```json
{
  "op": "auth",
  "AccessKeyId": "e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx",
  "SignatureMethod": "HmacSHA256",
  "SignatureVersion": "2",
  "Timestamp": "2017-05-11T15:19:30",
  "Signature": "4F65x5A2bLyMWVQj3Aqp+B4w+ivaA7n5Oi2SuYtCJ9o=",
}
```

**The format of Authentication data instruction**

  filed              |type   |  instruction|
  ------------------ |----   |  -----------------------------------------------------
  op                 |string | required; the type of requested operator is auth
  cid                |string | optional; the ID of Client request
  AccessKeyId        |string | required; API access key , AccessKey is in APIKEY you applied
  SignatureMethod    |string | required; the method of sign, user computes signature basing on the protocol of hash ,the api uses HmacSHA256
  SignatureVersion   |string | required; the version of signature's protocol, the api uses 2
  Timestamp          |string | required; timestamp, the time is you requests (UTC timezone), this value is to avoid that another people intercepts your request. for example ：2017-05-11T16:22:06 (UTC timezone)|
  Signature          |string |required; signature, the value is computed to make sure that the Authentication is valid and not tampered|

> **Notice：**
> - Refer to the Authentication[https://huobiapi.github.io/docs/spot/v1/en/#authentication] section to generate the signature
> - The request method in signature's method is `GET`

## Subscribe to Account Updates

API Key Permission：Read

This topic publishes all balance updates of the current account.

### Topic

`accounts`

> Subscribe request

```json
{
  "op": "sub",
  "cid": "40sG903yz80oDFWr",
  "topic": "accounts",
  "model": "0"
}
```

### Topic Parameter

Parameter | Data Type | Required | Default Value         | Description                                       | Value Range
--------- | --------- | -------- | -------------         | -----------                                       | -----------
model     | string    | false    | 0                     | Whether to include frozen balance                 | 1 to include frozen balance, 0 to not

<aside class="notice">You may subscribe to this topic with different model to get updates in both models</aside>
> Response

```json
{
  "op": "sub",
  "cid": "40sG903yz80oDFWr",
  "err-code": 0,
  "ts": 1489474081631,
  "topic": "accounts"
}
```

> Update example

```json
{
  "op": "notify",
  "ts": 1522856623232,
  "topic": "accounts",
  "data": {
    "event": "order.place",
    "list": [
      {
        "account-id": 419013,
        "currency": "usdt",
        "type": "trade",
        "balance": "500009195917.4362872650"
      }
    ]
  }
}

```

### Update Content

Field     | Data Type | Description
--------- | --------- | -----------
event     | string    | The event type which triggers this balance updates, including oder.place, order.match, order.refund, order.cancel, order.fee-refund, and other balance transfer event types
account-id| integer   | The account id of this individual balance
currency  | string    | The crypto currency of this balance
type      | string    | The type of this account, including trade, loan, interest
balance   | string    | The balance of this account, include frozen balance if "model" was set to 1 in subscription

## Subscribe to Order Updates

API Key Permission：Read

This topic publishes all order updates of the current account.

### Topic

`orders.$symbol`

> Subscribe request

```json
{
  "op": "sub",
  "cid": "40sG903yz80oDFWr",
  "topic": "orders.htusdt",
}
```

### Topic Parameter

Parameter | Data Type | Required | Default Value         | Description                                       | Value Range
--------- | --------- | -------- | -------------         | -----------                                       | -----------
symbol    | string    | true     | NA                    | Trading symbol                       | All supported trading symbols, e.g. btcusdt, bccbtc.Refer to `GET /v1/common/symbols`.support wildcard "*".

> Response

```json
{
  "op": "sub",
  "cid": "40sG903yz80oDFWr",
  "err-code": 0,
  "ts": 1489474081631,
  "topic": "orders.htusdt"
}
```

> Update example

```json
{
  "op": "notify",
  "topic": "orders.htusdt",
  "ts": 1522856623232,
  "data": {
    "seq-id": 94984,
    "order-id": 2039498445,
    "symbol": "htusdt",
    "account-id": 100077,
    "order-amount": "5000.000000000000000000",
    "order-price": "1.662100000000000000",
    "created-at": 1522858623622,
    "order-type": "buy-limit",
    "order-source": "api",
    "order-state": "filled",
    "role": "taker|maker",
    "price": "1.662100000000000000",
    "filled-amount": "5000.000000000000000000",
    "unfilled-amount": "0.000000000000000000",
    "filled-cash-amount": "8301.357280000000000000",
    "filled-fees": "8.000000000000000000"
  }
}
```

### Update Content

Field               | Data Type | Description
---------           | --------- | -----------
seq-id              | integer   | Sequence id
order-id            | integer   | Order id
symbol              | string    | Trading symbol
account-id          | string    | Account id
order-amount        | string    | Order amount (in base currency)
order-price         | string    | Order price
created-at          | int       | Order creation time (UNIX epoch time in millisecond)
order-type          | string    | Order type, possible values: buy-market, sell-market, buy-limit, sell-limit, buy-ioc, sell-ioc, buy-limit-maker, sell-limit-maker,buy-stop-limit,sell-stop-limit
order-source        | string    | Order source, possible values: sys, web, api, app
order-state         | string    | Order state, possible values: submitted, partial-filled, filled, canceled, partial-canceled
role                | string    | Order role in the trade: taker or maker
price               | string    | Order execution price
filled-amount       | string    | Order execution quantity (in base currency)
filled-cash-amount  | string    | Order execution value (in quote currency)
filled-fees         | string    | Transaction fee paid so far
unfilled-amount     | string    | Remaining order quantity

## Subscribe to Order Updates (NEW)

API Key Permission：Read

This topic publishes all order updates of the current account. By comparing with above subscription topic “orders.$symbol”, the new topic “orders.$symbol.update” should have lower latency but more sequential updates. API users are encouraged to subscribe to this new topic for getting order update ticks, instead of above topic “orders.$symbol”. (The current subscription topic “orders.$symbol” will be still kept in Websocket API service till further notice.)

### Topic

`orders.$symbol.update`

> Subscribe request

```json
{
  "op": "sub",
  "cid": "40sG903yz80oDFWr",
  "topic": "orders.htusdt.update"
}
```

### Topic Parameter

Parameter | Data Type | Required | Default Value         | Description                                       | Value Range
--------- | --------- | -------- | -------------         | -----------                                       | -----------
symbol    | string    | true     | NA                    | Trading symbol                       | Refer to `GET /v1/common/symbols`. wild card (\*) is supported 



> Response

```json
{
  "op": "sub",
  "ts": 1489474081631,
  "topic": "orders.htusdt.update",
  "err-code": 0,
  "cid": "40sG903yz80oDFWr"  
}
```

> Update example

```json
{
  "op": "notify",
  "ts": 1522856623232,
  "topic": "orders.htusdt.update",  
  "data": {
    "unfilled-amount": "0.000000000000000000",
    "filled-amount": "5000.000000000000000000",
    "price": "1.662100000000000000",
    "order-id": 2039498445,
    "symbol": "htusdt",
    "match-id": 94984,
    "filled-cash-amount": "8301.357280000000000000",
    "role": "taker|maker",
    "order-state": "filled",
    "client-order-id": "a0001",
    "order-type": "buy-limit"
  }
}
```

### Update Content

Field               | Data Type | Description
---------           | --------- | -----------
match-id              | integer   | Match id (While order-state = submitted, canceled, partial-canceled,match-id refers to sequence number; While order-state = filled, partial-filled, match-id refers to last match ID.)
order-id            | integer   | Order id
symbol              | string    | Trading symbol
order-state         | string    | Order state, possible values: submitted, partial-filled, filled, canceled, partial-canceled
role                | string    | Order role in the trade: taker or maker (While order-state = submitted, canceled, partialcanceled, a default value “taker” is given to this field; While order-state = filled, partial-filled, role can be either taker or maker.)
price               | string    | Last price (While order-state = submitted, price refers to order price; While order-state = canceled, partial-canceled, price is zero; While order-state = filled, partial-filled, price reflects the last execution price.)
filled-amount       | string    | Last execution quantity (in base currency)
filled-cash-amount  | string    | Last execution value (in quote currency)
unfilled-amount     | string    | Remaining order quantity (While order-state = submitted, unfilled-amount contains the original order size; While order-state = canceled OR partial-canceled, unfilled-amount contains the remaining order quantity; While order-state = filled, if order-type = buymarket, unfilled-amount could possibly contain a minimal value; if order-type <> buy-market, unfilled-amount is zero; While order-state = partial-filled AND role = taker, unfilled-amount is the remaining order quantity; While order-state = partial-filled AND role = maker, unfilled-amount is remaining order quantity.)
client-order-id | string | Client order ID
order-type | string | order type, including buy-market, sell-market, buy-limit, sell-limit, buy-ioc, sell-ioc, buy-limit-maker, sell-limit-maker,buy-stop-limit,sell-stop-limit


## Request Account Details

API Key Permission：Read

Query all account data of the current user.

### Query Topic

`accounts.list`

> Query request

```json
{
  "op": "req",
  "cid": "40sG903yz80oDFWr",
  "topic": "accounts.list",
}
```

Parameter  | Data Type  |  Description|
----------| --------| -------------------------------------------------------|
op         |string  | Mandatory parameter; operation type "req"|
cid        |string  | optional parameter; id generate by client|
topic      |string   |mandatory parameter; topic to request "accounts.list"|

### Response

> Successful

```json
    {
      "op": "req",
      "topic": "accounts.list",
      "cid": "40sG903yz80oDFWr",
      "err-code": 0,
      "ts": 1489474082831,
      "data": [
        {
          "id": 419013,
          "type": "spot",
          "state": "working",
          "list": [
            {
              "currency": "usdt",
              "type": "trade",
              "balance": "500009195917.4362872650"
            },
            {
              "currency": "usdt",
              "type": "frozen",
              "balance": "9786.6783000000"
            }
          ]
        },
        {
          "id": 35535,
          "type": "point",
          "state": "working",
          "list": [
            {
              "currency": "eth",
              "type": "trade",
              "balance": "499999894616.1302471000"
            },
            {
              "currency": "eth",
              "type": "frozen",
              "balance": "9786.6783000000"
            }
          ]
        }
      ]
    }
```

> Failed

```json
    {
      "op": "req",
      "topic": "foo.bar",
      "cid": "40sG903yz80oDFWr",
      "err-code": 12001, //Response codes,0  represent success;others value  is error,the list of Response codes is in appendix
      "err-msg": "detail of error message",
      "ts": 1489474081631
    }
```

Field                |Data Type |    Description|
-------------------- |--------| ------------------------------------|
{ id                   |long    | account ID|
type              |string   |account type|
state           |string     |account status|
list               |string   |account list|
{currency                |string   |sub-account currency|
type           |string     |sub-account type|
balance }}           |string     |sub-account balance|

## Search Past Orders

API Key Permission：Read

Search past and open orders based on searching criteria.

### Query Topic

`order.list`

> Query request

```json
{
  "op": "req",
  "topic": "orders.list",
  "cid": "40sG903yz80oDFWr",
  "symbol": "htusdt",
  "states": "submitted,partial-filled"
}
```

### Request Parameters

Parameter  | Data Type | Required | Default | Description                                   | Value Range
---------  | --------- | -------- | ------- | -----------                                   | ----------
account-id | int       | true     | NA      | Account id                        | NA
symbol     | string    | true     | NA      | Trading symbol                | Refer to `GET /v1/common/symbols`
types      | string    | false    | NA      | Order type   | buy-market, sell-market, buy-limit, sell-limit, buy-ioc, sell-ioc, buy-limit-maker, sell-limit-maker, buy-stop-limit, sell-stop-limit
states     | string    | true    | NA      | Order state  | submitted, partial-filled, partial-canceled, filled, canceled, created
start-date | string    | false    | -61d    | Start date, in format yyyy-mm-dd      | NA
end-date   | string    | false    | today   | End date, in format yyyy-mm-dd        | NA
from       | string    | false    | NA      | Order id to begin with                 | NA
direct     | string    | false    | next    | Searching direction when 'from' is given          | next, prev
size       | string       | false    | 100     | Number of items in each return               | [1, 100]

### Response

> Successful

```json
{
  "op": "req",
  "topic": "orders.list",
  "cid": "40sG903yz80oDFWr",
  "err-code": 0,
  "ts": 1522856623232,
  "data": [
    {
      "id": 2039498445,
      "symbol": "htusdt",
      "account-id": 100077,
      "amount": "5000.000000000000000000",
      "price": "1.662100000000000000",
      "created-at": 1522858623622,
      "type": "buy-limit",
      "filled-amount": "5000.000000000000000000",
      "filled-cash-amount": "8301.357280000000000000",
      "filled-fees": "8.000000000000000000",
      "finished-at": 1522858624796,
      "source": "api",
      "state": "filled",
      "canceled-at": 0
    }
  ]
}
```
Field                |Data Type |    Description|
-------------------- |--------| ------------------------------------|
id                   |long    | order ID|
symbol               |string   |trading symbol|
account-id           |long     |account ID|
amount               |string   |order size|
price                |string   |order price|
created-at           |long     |order creation time|
type                 |string   |order type, possible values: buy-market, sell-market, buy-limit, sell-limit, buy-ioc, sell-ioc, buy-limit-maker, sell-limit-maker, buy-stop-limit, sell-stop-limit|
filled-amount        |string   |filled amount|
filled-cash-amount   |string   |filled value|
filled-fees          |string   |transaction fee|
finished-at          |string   |trade time|
source               |string   |order source, possible values: sys, web, api, app|
state                |string   |order state, possible values: submitted, partial-filled, filled, canceled, partial-canceled|
cancel-at            |long     |order cancellation time|
stop-price|string|trigger price of stop limit order|
operator|string|opration character of stop price|


## Query Order by Order ID

API Key Permission：Read

Get order details by a given order ID.

### Query Topic

`orders.detail`

> Query request

```json
{
  "op": "req",
  "topic": "orders.detail",
  "order-id": "2039498445",
  "cid": "40sG903yz80oDFWr"
}
```

### Request Parameters

Parameter  | Required | Data Type | Description |      Default              | Value Range
---------  | --------- | -------- | ------- | -----------                                   | ----------
op         |true       |string   |operation type "req"    |||                                
cid        |true       |string   |id generate by client        |||                                
topic      |false      |string   |topic to request "orders.detail"  |||          
order-id   |true       |string   |order ID    ||| 

### Response

> Successful

```json
{
  "op": "req",
  "topic": "orders.detail",
  "cid": "40sG903yz80oDFWr",
  "err-code": 0,
  "ts": 1522856623232,
  "data": {
    "id": 2039498445,
    "symbol": "htusdt",
    "account-id": 100077,
    "amount": "5000.000000000000000000",
    "price": "1.662100000000000000",
    "created-at": 1522858623622,
    "type": "buy-limit",
    "filled-amount": "5000.000000000000000000",
    "filled-cash-amount": "8301.357280000000000000",
    "filled-fees": "8.000000000000000000",
    "finished-at": 1522858624796,
    "source": "api",
    "state": "filled",
    "canceled-at": 0
  }
}
```
Field                |Data Type |    Description|
-------------------- |--------| ------------------------------------|
id                   |long    | order ID|
symbol               |string   |trading symbol|
account-id           |long     |account ID|
amount               |string   |order size|
price                |string   |order price|
created-at           |long     |order creation time|
type                 |string   |order type, possible values: buy-market, sell-market, buy-limit, sell-limit, buy-ioc, sell-ioc, buy-limit-maker, sell-limit-maker, buy-stop-limit, sell-stop-limit|
filled-amount        |string   |filled amount|
filled-cash-amount   |string   |filled value|
filled-fees          |string   |transaction fee|
finished-at          |string   |trade time|
source               |string   |order source, possible values: sys, web, api, app|
state                |string   |order state, possible values: submitted, partial-filled, filled, canceled, partial-canceled|
cancel-at            |long     |order cancellation time|
stop-price|string|trigger price of stop limit order|
operator|string|opration character of stop price|

# Websocket Asset and Order (v2)

## Genral

### Access URL

**Websocket Asset and Order (v2)**

**`wss://api.huobi.pro/ws/v2`**  

**`wss://api-aws.huobi.pro/ws/v2`**   

Note: 
By comparing to api.huobi.pro, the network latency to api-aws.huobi.pro is lower, for those client's servers locating at AWS.

### Message Compression

None.

### Heartbeat

Once the Websocket connection is established, Huobi server will periodically send "ping" message at 20s interval, with an integer inside.

```json
{
	"action": "ping",
	"data": {
		"ts": 1575537778295
	}
}
```

Once client's server receives "ping", it should respond "pong" message back with the same integer.

```json
{
    "action": "ping",
    "data": {
          "ts": 1575537778295 // the same integer from "ping" message
    }
}
```

### Valid Values of `action`

| Valid Values| Description|
| -----| -----|
| sub | Subscribe|
| req | Request|
|ping,pong| Heartbeat|
|push| Push (from Huobi server to client's server)|

### Authentication

Authentication request:

```json
{
    "action": "req", 
    "ch": "auth",
    "params": { 
        "authType":"api",
        "accessKey": "sffd-ddfd-dfdsaf-dfdsafsd",
        "signatureMethod": "HmacSHA256",
        "signatureVersion": "2.1",
        "timestamp": "2019-09-01T18:16:16",
        "signature": "safsfdsjfljljdfsjfsjfsdfhsdkjfhklhsdlkfjhlksdfh"
    }
}

```

The response of success

```json
{
	"action": "req",
	"code": 200,
	"ch": "auth",
	"data": {}
}
```

Authentication request field list

|Field| Mandatory|Data Type| Description
|----| ----|--------| ----
|action|true| string| Action type, valid value: "req"
|ch|true|string|Channel, valid value: "auth"
|authType| true|string|Authentication type, valid value: "api"
|accessKey|true|string|Access key
|signatureMethod| true| string| Signature method, valid value: "HmacSHA256"
|signatureVersion| true|string|Signature version, valid value: "2.1"
|timestamp|true|string|Timestamp in UTC in format like 2017-05-11T16:22:06
|signature| true| string| Signature

### Generating Signature 

The signature generation method v2.1 is similar with v2.0, with only following differences:

1. The request method should be "GET", to URL "/ws/v2".
2. The involved field names in v2 signature generation are: accessKey，signatureMethod，signatureVersion，timestamp
3. The valid value of signatureVersion is 2.1.

Please refer to detailed signature generation steps from: [https://huobiapi.github.io/docs/spot/v1/cn/#c64cd15fdc]

The final string involved in signature generation should be like below:

```
GET\n
api.huobi.pro\n
/ws/v2\n
accessKey=0664b695-rfhfg2mkl3-abbf6c5d-49810&signatureMethod=HmacSHA256&signatureVersion=2.1&timestamp=2019-12-05T11%3A53%3A03
```

### Subscribe a Topic to Continuously Receive Updates

Once the Websocket connection is established, Websocket client could send following request to subscribe a topic:

```json
{
	"action": "sub",
	"ch": "accounts.update"
}
```

Upon success, Websocket client should receive a response below:

```json
{
	"action": "sub",
	"code": 200,
	"ch": "accounts.update#0",
	"data": {}
}
```

### Request an Update

Once the Websocket connection is established, Websocket client could send following request to acquire an update:

```json
{
    "action": "req", 
    "ch": "topic",
}
```

Upon success, Websocket client should receive a response below:

```json
{
    "action": "req",
    "ch": "topic",
    "code": 200,
    "data": {} // update contents
}
```

## Subscribe Trade Details post Clearing

API Key Permission: Read

The topic updates trade details including transaction fee and transaction fee deduction etc. It only updates when transaction occurs.

### Topic

`trade.clearing#${symbol}`

### Subscription Field

|Field | Data Type | Description |
|--------- | --------- | -------- |
|symbol     | string    | Trading symbol (wildcard * is allowed) |

> Subscribe request

```json
{
	"action": "sub",
	"ch": "trade.clearing#btcusdt"
}

```

> Response

```json
{
	"action": "sub",
	"code": 200,
	"ch": "trade.clearing#btcusdt",
	"data": {}
}
```

> Update example

```json
{
    "ch": "trade.clearing#btcusdt",
    "data": {
         "symbol": "btcusdt",
         "orderId": 99998888,
         "tradePrice": "9999.99",
         "tradeVolume": "0.96",
         "orderSide": "buy",
         "aggressor": true,
         "tradeId": 919219323232,
         "tradeTime": 998787897878,
         "transactFee": "19.88",
         " feeDeduct ": "0",
         " feeDeductType": ""
    }
}
```

### Update Contents

|Field     | Data Type | Description|
|--------- | --------- | -----------|
|	symbol	|	string	|	Trading symbol|
|	orderId	|	long	|	 Order ID|
| tradePrice	|	string	|	Trade price|
|	tradeVolume	|	string	|	Trade volume|
|	orderSide	|	string	|	Order side, valid value: buy,sell|
|	orderType	|	string	|	Order type, valid value: buy-market, sell-market,buy-limit,sell-limit,buy-ioc,sell-ioc,buy-limit-maker,sell-limit-maker,buy-stop-limit,sell-stop-limit|
|	aggressor	|	bool	|	Aggressor or not, valid value: true, false|
| tradeId	|	long	|	Trade ID|
| tradeTime	|	long	|	Trade time, unix time in millisecond|
|	transactFee	|	string	|	Transaction fee|
|	feeDeduct	|	string	|	Transaction fee deduction|
|	feeDeductType	|	string	|		Transaction fee deduction type, valid value: ht,point|

## Subscribe Account Change

API Key Permission: Read

The topic updates account change details.

### Topic

`accounts.update#${mode}`

Upon subscription field value specified, the update can be triggered by either of following events:

1、Whenever account balance is changed.

2、Whenever account balance or available balance is changed. (Update separately.)

### Subscription Field

| Field | Data Type |  Description |
| --------- | --------- | --------- |
| mode    | integer   | Trigger mode, valid value: 0, 1, default value: 0|

Samples  
1、Not specifying "mode":  
accounts.update  
Only update when account balance changed;  
2、Specify "mode" as 0:  
accounts.update#0  
Only update when account balance changed;  
3、Specify "mode" as 1:  
accounts.update#1  
Update when either account balance changed or available balance changed.  

> Subscribe request

```json
{
	"action": "sub",
	"ch": "accounts.update"
}
```

> Response

```json
{
	"action": "sub",
	"code": 200,
	"ch": "accounts.update#0",
	"data": {}
}
```

> Update example

```json
accounts.update#0：
{
	"action": "push",
	"ch": "accounts.update#0",
	"data": {
		"currency": "btc",
		"accountId": 123456,
		"balance": "23.111",
		"changeType": "transfer",
           	"accountType":"trade",
		"changeTime": 1568601800000
	}
}

accounts.update#1：
{
	"action": "push",
	"ch": "accounts.update#1",
	"data": {
		"currency": "btc",
		"accountId": 33385,
		"available": "2028.699426619837209087",
		"changeType": "order.match",
         		"accountType":"trade",
		"changeTime": 1574393385167
	}
}
{
	"action": "push",
	"ch": "accounts.update#1",
	"data": {
		"currency": "btc",
		"accountId": 33385,
		"balance": "2065.100267619837209301",
		"changeType": "order.match",
           	"accountType":"trade",
		"changeTime": 1574393385122
	}
}
```

### Update Contents

|Field               | Data Type | Description|
|---------           | --------- | -----------|
|	currency	|	string	|	Currency|
|	accountId	|	long	|	Account ID|
|	balance	|	string	|	Account balance (only exists when account balance changed)|
|	available	|	string	|	Available balance (only exists when available balance changed)|
|	changeType	|	string	| Change type, valid value: order-place,order-match,order-refund,order-cancel,order-fee-refund,margin-transfer,margin-loan,margin-interest,margin-repay,other, |
|	accountType	|	string	|	account type, valid value: trade, frozen, loan, interest|
|	changeTime	|	long	|	Change time, unix time in millisecond|


# Stable Coin Exchange

## Get Exchange Rate

API Key Permission：Read

### HTTP Request

`GET https://api.huobi.pro/v1/stable-coin/quote`

### Request Parameters

Parameter  | Data Type | Required | Default | Description
---------  | --------- | -------- | ------- | -----------
currency    | string    | true     | NA      | Stable coin name (USDT/PAX/USDC/TUSD).Refer to `GET /v1/common/currencys`
amount     | string    | true     | NA      | Amount of stable coin to exchange (the value must be an intger.)
type        | string    | true    | NA      | Type of the exchange (buy/sell)

### Response Content

Field               | Data Type | Description
---------           | --------- | -----------
currency    | string    | Stable coin name (USDT/PAX/USDC/TUSD)
amount     | string    | Amount of stable coin to exchange (Due to factors such as the amount of the exchange account, the amount returned may be smaller than the amount requested.)
type        | string   | Type of the exchange (buy/sell)
exchangeAmount       | string   | Amount of HUSD to exchange in or out
quoteId       | string   | Stable currency quoteID
expiration|string|Term of validity

### Error Code

Error Code               | Description
---------           | --------- 
invalid-currency    | invalid currency    
invalid-amount     | amount<100，000 or amount>the max     
invalid-type        | type not 'buy' or 'sell'
quote-failure|other errors

## Exchange Stable Coin

API Key Permission：Trade

### HTTP Request

`POST https://api.huobi.pro/v1/stable-coin/exchange`

### Request Parameters

Parameter  | Data Type | Required | Default | Description
---------  | --------- | -------- | ------- | -----------
quote-id    | string    | true     | NA      | stable currency quoteID

### Response Content

Field               | Data Type | Description
---------           | --------- | -----------
transact-id    | long    | Exchange record id
currency    | string    | Stable coin name (USDT/PAX/USDC/TUSD)
amount     | string   |  Amount of stable coin to exchange
type        | string   | Type of the exchange (buy/sell)
exchange-amount       | string   | Amount of HUSD to exchange in or out
time       | long   | Timestampe

### Error Code

Error Code               | Description
---------           | --------- 
invalid-quote-id    | Paramemter ‘quote-id’ is invalid    
insufficient-balance     | insufficient balance to buy or sell stable coins     
insufficient-quota        | the quota is exceeded
exchange-failure|other errors
Base-user-request-exceed-limit|Operation is too frequent

# ETF (HB10)

Huobi's platform allows clients to create ETF holdings with their matching assets, and also allows clients to redempt ETF to comprised assets.

## Creation and Redemption Configuration

This endpoint will return the basic information of ETF creation and redemption, as well as ETF constituents, including max amount of creation, min amount of creation, max amount of redemption, min amount of redemption, creation fee rate, redemption fee rate, eft create/redeem status.

### HTTP Request

- GET `/etf/swap/config`

```shell
curl "https://api.huobi.pro/etf/swap/config?etf_name=hb10"
```

### Request Parameter

Parameter   | Data Type | Required | Description
-----       |-----      |-----     |------
etf_name    | string    | true     | The name of the ETF, currently only support hb10

> Response:

```json
{
  "code": 200,
  "data": {
    "purchase_min_amount": 10000,
    "purchase_max_amount": 100000,
    "redemption_min_amount": 10000,
    "redemption_max_amount": 10000,
    "purchase_fee_rate": 0.001,
    "redemption_fee_rate": 0.002,
    "etf_status":1,
    "unit_price":
    [
      {
        "currency": "eth",
        "amount": 19.9
      },
      {
        "currency": "btc",
        "amount": 9.9
      }
    ]
  },
  "message": null,
  "success": true
}
```

### Response Content

Field                 | Data Type  | Description |
-----------           |------------|-----------  |
purchase_min_amount   | integer    | Minimum creation amounts per request |
purchase_max_amount   | integer    | Max creation amounts per request |
redemption_min_amount | integer    | Minimum redemption amounts per request |
redemption_max_amount | integer    | Max redemption amounts per request |
purchase_fee_rate     | decimal    | Creation fee rate |
redemption_fee_rate   | decimal    | Redemption fee rate |
etf_status            | integer    | status of the ETF: Normal(1), Rebalancing Start(2), Creation and Redemption Suspended(3), Creation Suspended(4), Redemption Suspended(5)  |
unit_price            | array      | ETF constitution in format of {amount, currency}

## Order Creation/Redemption

API Key Permission：Trade

This endpoint allow clients to order creation or redemption of ETF.

### HTTP Request

- POST `/etf/swap/in`

- POST `/etf/swap/out`

```shell
curl -X POST -H 'Content-Type: application/json' "https://api.huobi.pro/etf/swap/in" -d
'{"etf_name": "hb10", "amount": 10000}'

curl -X POST -H 'Content-Type: application/json' "https://api.huobi.pro/etf/swap/out" -d
'{"etf_name": "hb10", "amount": 10000}'
```

### Request Parameter

Parameter  | Required | Data Type |  Description
---------  |--------- |-----------|------------  
etf_name   | true     | string    | ETF name, currently only support hb10
amount     | true     | integer   | The amount to create or redemption

> Response:

```json
{
    "code": 200,
    "data": null,
    "message": null,
    "success": true
}
```

### Response Content

Field      | Data Type | Description
-----------|-----------|-----------
code       | integer   | The overall status of the order, please find details in below table
data       | object    | The data content if available
message    | string    | The message of the order result
success    | boolean   | If the order is successful

**Response code details**

Code  | Description
--    |--
200   | Successful
10404 | Invalid ETF name
13403 | Insufficient asset to create ETF
13404 | Create and redemption disabled due to system setup
13405 | Create and redemption disabled due to configuration issue
13406 | Invalid API call
13410 | API authentication fails
13500 | System error
13601 | Create and redemption disabled during rebalance
13603 | Create and redemption disabled due to other reason
13604 | Create suspended
13605 | Redemption suspended
13606 | Amount incorrect. For the cases when creation amount or redemption amount is not in the range of min/max amount, this code will be returned.

## Show Past Creation/Redemption

API Key Permission：Read

This endpoints allows clients to get past creation and redemption.(up to 100 records)

### HTTP Request

- GET `/etf/swap/list `

```shell
curl "https://api.huobi.pro/etf/swap/list"
```

### Request Parameter

Parameter  | Required | Data Type |  Description |
---------  |--------- |-----------|------------  |
etf_name   | true     | string    | ETF name, currently only support hb10
offset     | true     | integer   | The offset of the records, set to 0 for the latest records
limit      | true     | integer   | The number of records to return, max is 100  

> Response:

```json
{
  "code": 200,
  "data": [
    {
      "id": 112222,
      "gmt_created": 1528855872323,
      "currency": "hb10",
      "amount": 11.5,
      "type": 1,
      "status": 2,
      "detail":
      {
        "used_ currency_list":
        [
          {
            "currency": "btc",
            "amount": 0.666
          },
          {
            "currency": "eth",
            "amount": 0.666
          }
        ],
        "rate": 0.002,
        "fee": 100.11,
        "point_card_amount":1.0,
        "obtain_ currency_list":
        [
          {
            "currency": "hb10",
            "amount": 1000
          }
        ]
      }
    }
  ],
  "message": null,
  "success": true
}
```

### Response Content

Field       | Data Type | Description
----------- |-----------|-----------
id          | integer   | Creation/Redemption id
gmt_created | integer   | Operation timestamp
currency    | string    | ETF name
amount      | decimal   | Creation/Redmption amount
type        | integer   | Creation(1), Redemption(2)
status      | integer   | Operation result
detail      | array     | Please find details below

**Fields under "Detail"**

Field                 | Data Type | Description |
-----                 |-----      |-----        |
used_currency_list    | array     | For creation this is the list and amount of underlying assets used for ETF creation. For redemption this is the amount of ETF used for redemption.
rate                  | decimal   | Fee rate
fee                   | decimal   | The actual fee amount
point_card_amount     | decimal   | Discount from point card
obtain_currency_list  | array     | For creation this is the amount for ETF created. For redemption this is the list and amount of underlying assets obtained.
