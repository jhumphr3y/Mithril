# Data Retention Board

The following is a proposed method for providing more transparency to customers regarding what information about them you have. Let us assume you are using the data dump feature mentioned under BTCPay Server in [The Stack](the-stack.md/#data-dump). You've set it up so that, as soon as the package is marked "delivered", the database erases all information for that order. In this way, if for some reason your server is seized, there is no information out there on customers who have concluded their business with you. But what about customers that have placed orders, but not yet received their items? That information is still available in the database. Yes they used a pseudonym and didn't give their home address (if they followed your instructions as explaine in the section on [Mail and Shipping](mail-shipping.md)), but it doesn't take much to link that PO Box listed to the real owner, especially if your server is seized by some government agency. At this moment, I don't know how much we can do to stop this, but we can at least make our customers aware that their data may have been compromised. 

At some level this is still trust based, but it is a step in the right direction. Here's how it would work in theory, though it is yet untested:

A script on the WordPress/WooCommerce server runs at a set interval, let's say every 24 hours. The script cycles through each order still in the WooCommerce database and pulls only the invoice number of each. The script then posts these invoice numbers as a list to a dedicated PasteBin page or something similar. When customers place an order, the confirmation email that they receive should instruct them on what their invoice number is and where to access this page. You want to pick a page outside of your server and ideally one outside of whatever jurisdiction the agency seizing your server is located, otherwise they will take that down as well. The page would be simple, something like this:


```
**If your order invoice is listed below, your information is still in our servers. Invoice numbers can be found on the confirmation email you received when you placed your order. When your package has been delivered, your information will be deleted from our servers and your invoice number should be removed from this page within 24 hours:**
12345
12346
12349
12350
12351
```

In this way, if your servers are seized, your customers can know if their information was still in your database at the time of seizure and plan accordingly. The benefit of using only invoice numbers is that customers cannot find information out about each other.

This is not foolproof and if attackers gain access to your site without alerting you to this, they may have access to your customer records for an unknown amount of time, rendering this solution unhelpful, but it is a start and hopefully will get others thinking of more robust solutions in the future.