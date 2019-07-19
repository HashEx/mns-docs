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

To resolve cryptoaddress from DNS you could use our REST API located at https://mns.hashex.org/resolve with a parameter *domain*.

Example
-------
Request::

  GET https://mns.hashex.org/resolve?domain=dm.hashex.org

Reply::

  {"address":"Mx96d8076e6342c5afc71162830c6b35fb1ed1d007",
   "delegate":"Mp0000000000000000",
   "ticker":"TESTCOIN",
   "signature":{"r":"439017adc3b350998fcbf5ae0ca3a3968ca07dbdd1d2ae2afd755568fb9506e3",
                "s":"311441ec3c8e4fdcb2f3bcdf103d8f008a4017da0b670a575aef4b090205ccdb",
                "v":27}}

| **address** - Minter's address.
| **delegate** - Minternode's public key for delegation.
| **ticker** - Minter coin's ticker.
| **signature** - reply's ECDSA signature by our node. You should check it in case of man-in-the-middle attack. Node's public key is **Mp**. 
