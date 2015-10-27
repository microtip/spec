Microtip Meta Tag Specification
===============================

Lets say you're a blogger. You would like to earm money from the audience that reads your blogs. One way to do this is to put ads on your site. Ads can be easily blocked, and for users who don't block them, they are annoying to look at. Getting started using the platform is as easy as adding a snippet of code to every page that contains content. Somewhere in the HTML document of your blog's header, you can add a meta take like this:

``` html
<meta name="microtip" content="1HWpyFJ7N6rvFkq3ZCMiFnqM6hviNFmG5X" data-currency='btc' data-recipient="Autotip Giveaway Program">
```

Replace the value of `content` with your actual bitcoin address. To get started with bitcoin, go to bitcoin.org. You can also use altcoin addresses:

```html
<meta name="microtip" content="Lb78JDGxMcih1gs3AirMeRW6jaG5V9hwFZ" data-currency='ltc'>
```

Multiple tipping addresses per page
-----------------------------------

The standard also permits the use of multiple tip addresses. In the case that the extension finds multiple tip addresses, the tip gets split amoung each address equally. Currently, this extension does not support sending tips to altcoin addresses, but support is planned.
Full meta tag specification

The following attributes are associated with the meta tag specification: 

Attribute      | Type     | Description
---------------|----------|-------------
name           | required | always "microtip"
content        | required | The cryptocurrency address of the person who will recieve tips.
data-currency  | optional | The name of the currency. Examples: `BTC`, `LTC`, also you can write the whole name of the curency, such as "dogecoin", and "peercoin". Case insensitive. If left blank, `BTC` is implied.
data-recipient | optional | Human readable name of the person who will revieve the tips. Can be a person's name or just "Development team". The purpose of this field is to be shown to the tipping user at the time of making the tip.
data-ratio     | optional | Only applicable if there are multiple microtip tags on a single page. This attribute tells the tiping extension how much of the tip should go to this address. The value should be a decimal number between 0 and 1.0. All ratio values must add up to less than or equal to 1.0.

Examples
--------

One single Litecoin address, all going to the "Development Team" wallet address.

``` html
<meta name="microtip" content="Lb78JDGxMcih1gs3AirMeRW6jaG5V9hwFZ" data-currency='ltc' data-recipient="Development Team">
```

Two different bitcoin address. Half going to Bob, the other half going to Terry. (Bitcoin currency is implied)

``` html
<meta name="microtip" content="1HWpyFJ7N6rvFkq3ZCMiFnqM6hviNFmG5X" data-recipient="Bob">
<meta name="microtip" content="1DCzzFuW33YJv9RGUMHyvgaoTdcNkwGMeR" data-recipient="Terry">
```

Same as above, but 80% of all tips goes to Terry, 20% goes to Bob.

``` html
<meta name="microtip" content="1HWpyFJ7N6rvFkq3ZCMiFnqM6hviNFmG5X" data-recipient="Bob" data-ratio="0.2">
<meta name="microtip" content="1DCzzFuW33YJv9RGUMHyvgaoTdcNkwGMeR" data-recipient="Terry" data-ratio="0.8">
```
