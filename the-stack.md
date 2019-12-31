# Open Source Stack

To limit dependencies and increase sovereignty of your site, it is highly recommended to use open-source products that you control yourself. This framework recommends the following stack for your website:

- [WordPress](#wordpress) for your actual site
- [WooCommerce](#woocommerce) for the listing of products
- [BTCPay Server](#btcpay-server) for invoicing and payment processing

Each of these has been chosen because they are a open-source, well-documented and do not require depending on a third-party provider that can arbitrarily cut you off.

## WordPress

[Wordpress](https://wordpress.org) is a content management system (CMS) that is likely the most popular platform for building a website on any given day. Originally built for blogging, WordPress has continued to expand and adapt, now so customizable that you could build a website on WordPress to literally look like anything you wanted. Out of the box it comes with themes that are responsive/mobile-ready, is equipped for SEO and has a user-friendly media manager. Your website is only limited by your imagination. 

## WooCommerce

Between customizeable themes and plugins, one could design their own storefront with only WordPress. But [WooCommerce](https://wordpress.org/plugins/woocommerce/) has already done all the hard work for you and it is open source so why spend all of your time on that? If you want to extend your WooCommerce, there are additional plugins (both paid and free), but this project cannot vouch for whether or not those are open source and any time you have to pay for something with fiat, you open yourself to tracking and attack. WooCommerce makes creating individual store items simple and straightforward, with options for pricing, colors or sizes, inventory, categories (like mens vs womens, clothing vs shoes) and more.

## BTCPay Server

The part of this stack that truly differentiates it from other webstores is the use of BTCPay Server to process Bitcoin payments.

### Address creation
[BTCPay](https://btcpayserver.org) server makes use of user-input public keys to create individual addresses for each checkout process. This helps protect your customers from being associated with one another. For more on this see [Blockchain Surveillance](blockchain-surveillance.md). Public keys can be added from your preferred wallet, whether that is software like Samourai or Electrum or hardware like Coldcard or Trezor. BTCPay never has your private keys however, meaning it can generate addresses for you, but your funds are never held on BTCPay and your funds cannot be stolen if your website's security were compromised. Funds are safu. 

### Lightning
BTCPay also works with the Lightning Network which can add additional privacy through a routing network as well as speeding up your transactions. Lightning funds however are by nature a hot-wallet so keep that in mind as part of your security model.

### Data Dump
The combination of Woocommerce and BTCPay has another privacy feature that is probably underutilized, but has powerful potential. You can set how long the database retains customer information. This means you can choose to erase your customer's info after 30 days, after 7 days, or whenever it has arrived if you use order tracking. This means that if some enterprising "hacktavist" or state actor compromises your database, they have only the "in process" orders to work with, not your entire client history. The downside to this is that once the customer's info has been dumped there's not much available in the way of proof for customer support. This is a tradeoff that must be balanced for your business, whether or not retaining customer data is worth the risk. As of yet there is no way to *prove* you have dumped customer data, though the [Data Retention Board](data-retention-board.md) is a good-faith step.

### Set Up
There are several ways of setting up BTCPay server depending on your hosting solution. BTCPay has a wealth of [documentation](https://docs.btcpayserver.org/) and [Pavlenex](https://twitter.com/pavlenex) has created a fantastic guide [here](https://bitcoinshirt.co/how-to-create-store-accept-bitcoin/) for the whole process start to finish, though some of the details may have changed since original publishing.

BTCPay is one of the most actively developed open-source projects in the Bitcoin space and is always looking for more ideas and contributors. As such there are likely new features that are not included in this guide, but this should give the basic ideas of why it is important for sovereignty.


## Warning about fiat

If you are serious about your privacy, do not ever accept fiat. Accepting fiat digitally requires submitting to KYC/AML or other identification procedures and cannot be taken back. Start with Bitcoin only and never look back. 