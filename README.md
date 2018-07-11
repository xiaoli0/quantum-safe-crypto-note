### What

This is the reference code for [quantum-safe-crypto-note](https://github.com/quantum-safe-blockchain-project/quantum-safe-crypto-note) blockchain protocol.

* It is a platform based on [CryptoNote](https://github.com/cryptonotefoundation/cryptonote); with a goal of providing privacy against quantum computers.

* It aim to enable blockchain developers to work on various projects with minimum exposure of quantum-safe cryptography.

* In a sense it should be called lattice-based blockchain since I am only considering
lattice-based cryptography at the moment. Other quantum-safe crypto, such as
hash-based signatures, may be introduced later.



* It is **NOT** an implementation of any cryptocurrency.

### Why

If you searched for _quantum-safe blockchain_ and have read thus far, I would assume you are already convinced about the
_inevitable_ arrival of general purpose quantum computers. What remains to be
said, is how it is going to affect blockchain technologies.

Blockchain technology may rely on the following cryptographic primitives:

* Level 1  **Basic functionality**:
A basic blockchain only requires cryptographic hash functions for integrity;

* Level 2  **Authenticity**:
Requires digital signature schemes, such as ECDSA: Elliptic Curve Digital Signature Algorithm;

* Level 3  **Anonymity**:
Enabling anonymity and authenticity simultaneously requires ring signatures;

* Level 4  **Linkability**:
In some use cases, such as cryptocurrency, it is desirable to track double spenders via linking two anonymous blocks; this requires one-time linkable ring signatures.

The above techniques, except for hash functions, are vulnerable to quantum computers. That is, if one uses discrete log or pairing based linkable ring signatures, for example [Monero](https://getmonero.org/), then there will be
two threats:

1. when a general purpose quantum computer is available (say, 2025), an attacker will be able to impersonate other users;

2. an attacker may also be able to link all previous transactions (say, between 2017 and 2025) that de-anonymize the whole use base.

The first threat is not so severe as we still have time between now and then to
deploy quantum-safe countermeasures. The second, however, requires us to act right
now.

You may have heard of the terminology _unconditional anonymity_. There are classical linkable ring signatures
that are unconditional anonymous, which makes them vulnerable against threat #1 while robust against threat #2.
Unfortunately, those schemes are not deployed. If we have to transit from existing
linkable ring signatures to another one, we might as well do it once for all - move onto quantum-safe primitives.




### How
##### cryptography
A few schemes are under considerations.
* Key exchange/encapsulation methods - phase I
  * An R-LWE based solution TBD
    * need to consider the IP around reconciliation mechanism
  * Backup plan: [NTRUEncrypt](https://github.com/NTRUOpenSourceProject/NTRUEncrypt)
    * Patent expired 2017
* Digital Signature scheme    - phase I
  * [Falcon](https://falcon-sign.info/)
    * Patent release to public if Falcon is Standardized by NIST
    * Otherwise patent expires 2023
  * [Dilithium](https://pq-crystals.org/dilithium/index.shtml)   
* Linkable Ring signature scheme - phase II
  * [Raptor](https://github.com/NTRUOpenSourceProject/raptor)
* Lattice based zero knowledge proof - phase III
  * no implementable candidate exists
* Leveled homomorphic encryption schemes - phase IV
  * To be decided later
  * Use case: privacy preserving smart contract


##### hybrid mode
  The above quantum-safe cryptography primitives will be added to the underlying CryptoNote's crypto library. It will not replace
  the existing ECDH and ECDSA schemes. Rather, those new primitives will run in parallel, in a so-called hybrid mode, to
  get the best of the two world. In case either ECC or the new primitive fails, the security is still backed by the other
  cryptosystem. To read more on this, here are a few academic papers on hybrid solutions [QSH-TOR](https://eprint.iacr.org/2015/287), [Hyrbid-Cert](https://eprint.iacr.org/2017/460)
  and as well as some Internet Drafts: [QSH-TLS](https://tools.ietf.org/html/draft-whyte-qsh-tls13-06), [QSH-IKE](https://tools.ietf.org/html/draft-tjhai-ipsecme-hybrid-qske-ikev2-01).


### When
This is a spare time project of mine that may or may not change in future. You should expect a very slow development on this project.
**Pull requests are more than welcome.**

## Contacts
* Email: quantum dot safe dot blockchain at gmail dot com
* [Forum / Google group](https://groups.google.com/forum/#!forum/quantum-safe-crypto-note-dev)
