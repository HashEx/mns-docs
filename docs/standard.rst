MNS Standard v1
========

For blockchain integration into name system we created the MNS Standard.

Domain Registration
--------

To register domain you need to send a transaction with data field in format:::
    R:domain
**domain** - your domain in format *domain.zone*.

Domain Record Update
--------

To update domain record you need to send a transaction with data field in format:
> U:domain:host:type:arg1:arg2[:nonce_to_remove]

**domain** - your domain in format *domain.zone*.
**host** - your host (@ or subdomain) for the record.
**type** - record type (A, TXT, MX, etc).
**arg1** - first argument of the record.
**arg2** - first argument of the record.
**nonce_to_remove** - optional, nonce of transaction with records update which need to be removed. See example below.

Domain Record Delete
--------

To delete domain record you need to send a transaction with data field in format:
> D:domain:nonce_to_remove

**domain** - your domain in format __domain.zone__.
**nonce_to_remove** - nonce of transaction with records update which need to be removed. See example below.

Cryptoaddress Resolve
--------

Our standard for addresses resolving is a DNS record
> TXT v=mns1 A=Mx000 D=Mp000 C=COIN

**mns1** - standard name and version.
**A** - your address.
**D** - your node's public key for delegation.
**C** - your coin's ticker.

Example
--------

1. Domain __testdomain.mnt__ registration. Data field is 
> R:testdomain.mnt
Transaction [HASH]().

2. Adding A record on testdomain.mnt to IP. Data field is
> U:testdomain.mnt:@:A:IP::
Transaction [HASH]().

3. Adding A record on subdomain sd.testdomain.mnt to IP. Data field is
> U:testdomain.mnt:sd:A:IP::
Transaction [HASH]().
or the same
> U:testdomain.mnt:sd.testdomain.mnt.:A:IP::

4. Changing A record on subdomain sd.testdomain.mnt from IP to IP. Data field is
> U:testdomain.mnt:sd:A:IP::
> D:testdomain.mnt:NONCE
Transaction [HASH]() and [HASH]().
or the same, but shorter with __nonce_to_remove__ option
> U:testdomain.mnt:sd:A:IP::NONCE
Transaction [HASH]().

5. Add cryptoaddress, delegation public key and coin ticker record on testdomain.mnt. Data filed is
> U:testdomain.mnt:sd:TXT:v=mns1 A=Mx D=Mp C=COIN::
Transaction [HASH]().
