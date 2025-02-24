<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### Table of Contents

*   [MarketType][1]
*   [findMarketPda][2]
    *   [Parameters][3]
    *   [Examples][4]
*   [getMarket][5]
    *   [Parameters][6]
    *   [Examples][7]
*   [getMintInfo][8]
    *   [Parameters][9]
    *   [Examples][10]
*   [findEscrowPda][11]
    *   [Parameters][12]
    *   [Examples][13]
*   [findCommissionPaymentsQueuePda][14]
    *   [Parameters][15]
    *   [Examples][16]
*   [MarketOutcomes][17]
    *   [Parameters][18]
    *   [Examples][19]
*   [getMarketOutcomesByMarket][20]
    *   [Parameters][21]
    *   [Examples][22]
*   [getMarketOutcomeTitlesByMarket][23]
    *   [Parameters][24]
    *   [Examples][25]

## MarketType

## findMarketPda

For the provided event publicKey, market type and mint publicKey return a Program Derived Address (PDA). This PDA is used for market creation.

### Parameters

*   `program` **Program** {program} anchor program initialized by the consuming client
*   `eventPk` **PublicKey** {PublicKey} publicKey of an event
*   `marketType` **[MarketType][1]** {MarketType} type of the market
*   `mintPk` **PublicKey** {PublicKey} publicKey of the currency token

### Examples

```javascript
const eventPk = new PublicKey('7o1PXyYZtBBDFZf9cEhHopn2C9R4G6GaPwFAxaNWM33D')
const marketType = "MatchResult"
const mintPk = new PublicKey('5BZWY6XWPxuWFxs2jagkmUkCoBWmJ6c4YEArr83hYBWk')
const marketPda = await findMarketPda(program, eventPk, marketType, mintPk)
```

Returns **FindPdaResponse** publicKey (PDA) and the seed used to generate it

## getMarket

For the provided market publicKey, get the market account details.

### Parameters

*   `program` **Program** {program} anchor program initialized by the consuming client
*   `marketPk` **PublicKey** {PublicKey} publicKey of the market

### Examples

```javascript
const marketPk = new PublicKey('7o1PXyYZtBBDFZf9cEhHopn2C9R4G6GaPwFAxaNWM33D')
const market = await getMarket(program, marketPK)
```

Returns **MarketAccount** market account details

## getMintInfo

For the provided spl-token, get the mint info for that token.

### Parameters

*   `program` **Program** {program} anchor program initialized by the consuming client
*   `mintPK` **PublicKey** {PublicKey} publicKey of an spl-token

### Examples

```javascript
const mintPk = new PublicKey('7xKXtg2CW87d97TXJSDpbD5jBkheTqA83TZRuJosgAsU')
const mintInfo = await getMintInfo(program, mintPk)
```

Returns **MintInfo** mint information including mint authority and decimals

## findEscrowPda

For the provided market publicKey, return the escrow account PDA (publicKey) for that market.

### Parameters

*   `program` **Program** {program} anchor program initialized by the consuming client
*   `marketPk` **PublicKey** {PublicKey} publicKey of a market

### Examples

```javascript
const marketPk = new PublicKey('7o1PXyYZtBBDFZf9cEhHopn2C9R4G6GaPwFAxaNWM33D')
const escrowPda = await findEscrowPda(program, marketPK)
```

Returns **FindPdaResponse** PDA of the escrow account

## findCommissionPaymentsQueuePda

For the provided market publicKey, return the commission payments queue account PDA (publicKey) for that market.

### Parameters

*   `program` **Program** {program} anchor program initialized by the consuming client
*   `marketPk` **PublicKey** {PublicKey} publicKey of a market

### Examples

```javascript
const marketPk = new PublicKey('7o1PXyYZtBBDFZf9cEhHopn2C9R4G6GaPwFAxaNWM33D')
const commissionPaymentsQueuePda = await findCommissionPaymentsQueuePda(program, marketPK)
```

Returns **FindPdaResponse** PDA of the payment queue

## MarketOutcomes

Base market outcome query builder allowing to filter by set fields. Returns publicKeys or accounts mapped to those publicKeys; filtered to remove any accounts closed during the query process.

Some preset queries are available for convenience:

*   getMarketOutcomesByMarket
*   getMarketOutcomeTitlesByMarket

### Parameters

*   `program`  {program} anchor program initialized by the consuming client

### Examples

```javascript
const marketPk = new PublicKey('7o1PXyYZtBBDFZf9cEhHopn2C9R4G6GaPwFAxaNWM33D')
const marketOutcomes = await MarketOutcomes.marketOutcomeQuery(program)
     .filterByMarket(marketPk)
     .fetch();

Returns all market outcomes created for the given market.
```

## getMarketOutcomesByMarket

Get all market outcome accounts for the provided market.

### Parameters

*   `program` **Program** {program} anchor program initialized by the consuming client
*   `marketPk` **PublicKey** {PublicKey} publicKey of the market

### Examples

```javascript
const marketPk = new PublicKey('7o1PXyYZtBBDFZf9cEhHopn2C9R4G6GaPwFAxaNWM33D')
const marketOutcomes = await getMarketOutcomesByMarket(program, marketPk)
```

Returns **MarketOutcomeAccounts** fetched market outcome accounts mapped to their publicKey - ordered by index

## getMarketOutcomeTitlesByMarket

Get all market outcome titles for the provided market.

### Parameters

*   `program` **Program** {program} anchor program initialized by the consuming client
*   `marketPk` **PublicKey** {PublicKey} publicKey of the market

### Examples

```javascript
const marketPk = new PublicKey('7o1PXyYZtBBDFZf9cEhHopn2C9R4G6GaPwFAxaNWM33D')
const marketOutcomeTitles = await getMarketOutcomeTitlesByMarket(program, marketPk)
```

Returns **MarketOutcomeTitlesResponse** fetched market outcome titles - ordered by index

[1]: #markettype

[2]: #findmarketpda

[3]: #parameters

[4]: #examples

[5]: #getmarket

[6]: #parameters-1

[7]: #examples-1

[8]: #getmintinfo

[9]: #parameters-2

[10]: #examples-2

[11]: #findescrowpda

[12]: #parameters-3

[13]: #examples-3

[14]: #findcommissionpaymentsqueuepda

[15]: #parameters-4

[16]: #examples-4

[17]: #marketoutcomes

[18]: #parameters-5

[19]: #examples-5

[20]: #getmarketoutcomesbymarket

[21]: #parameters-6

[22]: #examples-6

[23]: #getmarketoutcometitlesbymarket

[24]: #parameters-7

[25]: #examples-7
