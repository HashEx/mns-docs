Cryptoaddress Resolver
========

It's too complicated to remember your cryptoaddress like *Mx3b22ca335b9f55af452d8c4b117ee06578505282*. When you provide somebody an address or QR code, you could easily make a mistake. So we created a helpful feature which connects your domain (classic or decentralized) with an address, delegation private key and coin ticker.

MNS Standard
--------
Our standard for addresses resolving is a DNS record::

  TXT v=mns1 A=Mx000 P=Mp000 C=COIN

| **mns1** - standard name and version.
| **A** - your address.
| **P** - your node's public key for delegation.
| **C** - your coin's ticker.

Usage
-------

To resolve cryptoaddress from DNS you could use our REST API located at https://mns.hashex.org/resolve with a parameter *domain*.

Example
-------
Request::

  GET https://mns.hashex.org/resolve?domain=testdomain.mnt

Reply::

  {"address":"Mx2958c39ea42b2868218f6058794a772178bfa88b",
 "publickey":"Mp0d29a83e54653a1d5f34e561e0135f1e81cbcae152f1f327ab36857a7e32de4c",
   "ticker":"TESTCOIN",
   "signature":{"r":"439017adc3b350998fcbf5ae0ca3a3968ca07dbdd1d2ae2afd755568fb9506e3",
                "s":"311441ec3c8e4fdcb2f3bcdf103d8f008a4017da0b670a575aef4b090205ccdb",
                "v":27}}

| **address** - Minter's address.
| **publickey** - Minternode's public key for delegation.
| **ticker** - Minter coin's ticker.
| **signature** - reply's ECDSA signature by our node. You should check it in case of man-in-the-middle attack. Node's public key is **Mp**. 
