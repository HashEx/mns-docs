MNS Standard v1
========

For blockchain integration into name system we created the MNS Standard.

Domain Registration
--------

To register domain you need to send a transaction with data field in format::
    
  R:domain
**domain** - your domain in format *domain.zone*.

Domain Record Update
--------

To update domain record you need to send a transaction with data field in format::

  U:domain:host:type:arg1:arg2[:nonce_to_remove]

| **domain** - your domain in format *domain.zone*.
| **host** - your host (@ or subdomain) for the record.
| **type** - record type (A, TXT, MX, etc).
| **arg1** - first argument of the record.
| **arg2** - second argument of the record.
| **nonce_to_remove** - optional, nonce of transaction with records update which need to be removed. See example below.

**NB. Now acceptable only A, AAAA and TXT types.**

Domain Record Delete
--------

To delete domain record you need to send a transaction with data field in format::

  D:domain:nonce_to_remove

| **domain** - your domain in format *domain.zone*.
| **nonce_to_remove** - nonce of transaction with records update which need to be removed. See example below.

Cryptoaddress Resolve
--------

Our standard for addresses resolving is a DNS record::

  TXT v=mns1 A=Mx000 P=Mp000 C=COIN

| **mns1** - standard name and version.
| **A** - your address.
| **P** - your node's public key for delegation.
| **C** - your coin's ticker.

Example
--------

1. Domain **testdomain.mnt** registration. Data field is
::

  R:testdomain.mnt
`Transaction <https://explorer.minter.network/transactions/Mt891731866bcb4c69eb59f4af38dc8714fcda6ba9592bcbee55a2228d1f663898>`_.

2. Adding A record on **testdomain.mnt** to **127.0.0.1**. Data field is
::
  
  U:testdomain.mnt:@:A:IP::
`Transaction <https://explorer.minter.network/transactions/Mt582de00b80bef2373ef608bc091cbb98f724e1a194af608675725af64ec592f5>`_.

3. Adding A record on subdomain **sd.testdomain.mnt** to **172.0.0.1**. Data field is
::
  
  U:testdomain.mnt:sd:A:IP::
`Transaction <https://explorer.minter.network/transactions/Mt8eb2fdf2ce122629036d1f94a12a4fc699cec0595bc574ce37b260c0c66e7003>`_ or the same
::

  U:testdomain.mnt:sd.testdomain.mnt.:A:IP::

4. Changing A record on subdomain **sd.testdomain.mnt** from **172.0.0.1** to **162.0.0.1**. Data field is
::
  
  U:testdomain.mnt:sd:A:IP::
  D:testdomain.mnt:NONCE
`Transaction <https://explorer.minter.network/transactions/Mt8eb2fdf2ce122629036d1f94a12a4fc699cec0595bc574ce37b260c0c66e7003>`_ and `transaction <https://explorer.minter.network/transactions/Mt7df2147f45f718eb5eb0042c23146532db7e274a14ca4610c9eac380daa052fb>`_ or the same, but shorter with *nonce_to_remove* option
::

  U:testdomain.mnt:sd:A:IP::NONCE_TO_REMOVE
`Transaction <https://explorer.minter.network/transactions/Mtb15b72583aab117e96021ce704ac858e19fb6d8da307acbcfc772fa818021c3b>`_.

5. Add cryptoaddress, delegation public key and coin ticker record on testdomain.mnt. Data filed is
::

  U:testdomain.mnt:@:TXT:v=mns1 A=Mx P=Mp C=COIN::
`Transaction <https://explorer.minter.network/transactions/Mt2578a7743b54d1edf92972c5b1a45a18403a25132bd68b0bbe8e81d2be05500f>`_.
