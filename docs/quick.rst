Quick Start Guide
========

Why do I need it?
--------

First, MNS provides you an ability to buy a domain in **.mnt** zone. You can buy any domain, for example, *mydomain.mnt*. Domain will be registred to your minter address via blockchain. You can use it like classic domain to provide access to your website or receive emails.

Second, MNS provides you an ability to associate your cryptoaddress like *Mx3b22ca335b9f55af452d8c4b117ee06578505282* to any domain, for example, *mydomain.mnt* or *mydomain.com*, 
so you could receive funds to pretty domain address, not ugly cryptoaddress.

How to buy .mnt domain?
--------

1. To buy a domain in .mnt zone you need to follow https://mns.hashex.org/buy.
2. Enter a domain name into search field and push "Search" button.
3. If domain is free, green arrow and button "Buy" will appear. If domain is not free, red cross will appear.
4. Push "Buy" button. Buy popup helper will appear.
5. You need to send a transaction to specified address with specified amount of funds and provided message with registration command. **Do not send transaction without message. It will raise error.**
6. Just wait while transaction is complete. And go to https://mns.hashex.org/settings.
7. Here you can enter your domain and manage interface will appear if previous transaction was correct.
8. Congratulations, your are an owner of domain in .mnt zone!

How to update .mnt domain?
-------

1. To update a domain in .mnt zone you need to follow https://mns.hashex.org/settings.
2. Enter a domain name into search field and push "Search" button.
3. If domain exists, managing interface will appear.
4. Push "Add" or "Edit" buttons. Editing popup helper will appear.
5. Create a desired record and get an information for the transaction.
6. To apply changes you need to send a transaction to specified address with specified amount of funds and provided message with registration command. **Do not send transaction without message. It will raise error.**
7. Just wait while transaction is complete. Refresh the page.
8. Your changes are applied if previous transaction was correct.

How to use pretty address insted of ugly cryptoaddress?
--------

For pretty address you can use **any domain: classic or .mnt**. If you are an owner of classic domain, steps are the same.

1. You need to add TXT record to your domain, host @, with data::

  v=mns1 A=YOUR_ADDRESS [D=YOUR_PUB_KEY C=YOUR_COIN]
| **mns1** - standard name and version.
| **A** - your address.
| **D** - your node's public key for delegation, optional.
| **C** - your coin's ticker, optional.

2. After changes are applied, go to https://mns.hashex.org/resolver and try to resolve your address.
3. Congratulations, you have a pretty address!
