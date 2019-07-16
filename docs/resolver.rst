Cryptoaddresses Resolver
========

It's too complicated to remember your crypto address like Mx0000. When you provide somebody an address or qr code, you could easily get a mistake. 
So we created a helpful feature which connects your domain (classical or decentralized) with an address, delegation private key and coin ticker.

MNS Standard
--------
Our standard for addresses resolving is a DNS record::

  TXT v=mns1 A=Mx000 D=Mp000 C=COIN

| **mns1** - standard name and version.
| **A** - your address.
| **D** - your node's public key for delegation.
| **C** - your coin's ticker.

Usage
-------

To resolve cryptoaddress from DNS you could use our REST API located at 

Example
-------
Request::

  GET

Reply::

  JSON

| **A** - your address.
| **D** - your node's public key for delegation.
| **C** - your coin's ticker.
| **sign** - reply's ECDSA signature by our node. You should check it in case of man-in-the-middle attack. Node's public key is **Mp**. 
