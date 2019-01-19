---
title: Crypto Fundamentals Workshops
taxonomy:
  category: project
  tag: [ project, crypto, pgp, workshop ]
---

Workshops to explore the fundamental concepts and of cryptography, and its resulting applications.

===

# Public Key Cryptography

"How I learned to stop worrying and love the cypher"

## Symmetric cryptography
- "Secret key cryptography"
- Same key used for encryption+decryption, must be shared by all parties.
- Examples
  - [Shift cipher](https://learncryptography.com/classical-encryption/caesar-cipher) (aka Caeser Cipher)
  - [Vigenere cipher](https://learncryptography.com/classical-encryption/vigenere-cipher)
  - DES (1977) - first attempt at a universal encryption standard
  - AES
  - [One-time pad](https://learncryptography.com/classical-encryption/one-time-pad) (OTP) still considered unbreakable with sufficiently random key

## Asymmetric cryptography
- "Public key cryptography"
- Encrypt with public key, decrypt with private key.
- History
  - First discovered in ~1969 (and multiple times since). Made public in 1997.
  - 1976 Diffie-Hellman (DH) key exchange algorithm ([SE](https://crypto.stackexchange.com/questions/42180/whats-the-difference-between-rsa-and-diffie-hellman))
  - 1978 Rivest, Adelman, Shamir (RSA) public key encryption algorithm
- Relies on a pair of keys instead of a single key. 
  - Private key: two large randomly-generated prime numbers
  - Public key: product of the two prime numbers
- Trapdoor function: easy to calculate in one direction, very difficult in the other direction
  - [Elliptic Curve Multiplication](https://en.wikipedia.org/wiki/Elliptic-curve_cryptography) (ECM)

### Disadvantages of asymmetric encryption
- [less efficient](https://crypto.stackexchange.com/questions/586/why-is-public-key-encryption-so-much-less-efficient-than-secret-key-encryption?noredirect=1&lq=1)

### Digital signatures
- Sign with private key, verify with public key
- [Elliptic Curve Digital Signature Algorithm](https://en.wikipedia.org/wiki/Elliptic_Curve_Digital_Signature_Algorithm) (ECDSA)
- Applications
  - Verifying integrity of source code and binaries
  - Verifying integrity of messages (prevent spoofing)
  - Encrypting sensitive files (passwords, email, backups)
  - Transport Layer Security (TLS/SSL)
  - SSH authentication ([OpenPGP card](https://en.wikipedia.org/wiki/OpenPGP_card))

### Applications to blockchain technology
- Features
  - authentication
  - nonrepudiation
  - authenticity
- Operations
  - wallet creation
  - transaction signing

## Pretty Good Privacy
### PGP functionality 
  - TODO
### PGP history
  - Created in 1991 by Phil Zimmermann
  - Started with custom-made symmetric-key algorithm
  - No license for non-commercial use, source code included w/every copy
  - Distributed across the Internet, violating munitions export controls
### Crypto Wars
  - Feb '93 Zimmerman became target of a criminal investigation for "munitions export without a license"
  - 1995 Published PGP source code as a hardback book in OCR-friendly font, protected by First Amendment
  - US export regulations stopped treating encryption as a non-exportable weapon in TODO
  - 1996 PGP Inc established, acquired the following year

## GNU Privacy Guard
### History
- 1997 release 0.0.0
- 1999 release 1.0.0 (first production version)
- "Modern" v2.2 branch (recommended)
- "Classic" v1.4 branch (embedded & vintage platforms)
### Functionality
- Free-software replacement for PGP (interoperable)
- Complies with RFC 4880 (IETF standards-track spec of OpenPGP)
- Available on Linux, Mac, and Windows platforms (many GUI integrations)
### Supported algorithms
- Public key: RSA, ElGamal, DSA
- Cipher: 3DES, IDEA, CAST5, Blowfish, Twofish, AES-128/192/256, Camellia-128/192/256
- Hash: MD5, SHA-1, RIPEMD-160, SHA-256, SHA-384, SHA-512, SHA-224
- Compression: none, zip, zlib, bzip2
### GPG demo
- Keypair creation
  - gpg --gen-key
  - gpg --output revoke.asc --gen-revoke mykey
- Exchanging & verifying keys
  - gpg --list-keys
  - gpg --output alice.gpg --export
  - gpg --armor --export alice@example.com
  - gpg --import bob.gpg
  - gpg --edit-key bob@example.com
    - fpr, sign, check
- Message encryption & decryption
  - gpg --output doc.gpg --encrypt --recipient bob@example.com doc.txt
  - gpg --output doc.txt --decrypt doc.gpg
- Message signing & verification

## Improving security

### Attack vectors
- Lost/stolen storage device
- Brute force
  - insufficent entropy (key length, source of randomness)
  - easily guessed passrd
- Man in the middle
- Advanced persistent threat
  - Remote access tools
  - Covert observation (screen, PSU, ultrasonic)

### Sensative data handling

### Airgapped operations
1. obtain a sterile computer
2. minimize EM & audio emissions
3. remove/disable all radios, cameras, mic, speakers
4. remove/disable non-volatile storage
5. verify signatures of all boot media and binaries

### Raspberry Pi as airgapped computer
- No on-board wireless (A,A+,B,2B,Zero)
- Easily powered by battery
- Hardware RNG
- Read-only filesystem
- USB HID disabled after startup

## Web of trust
- "a concept used in...OpenPGP-compatible systems to establish the authenticity of the binding between a public key and its owner"
- decentralized trust model is an alternative to public key infrastructure (PKI) run by centralized certification authorities
### Key signing party
- Verification of identity, exchange of public key fingerprints
- Key signing happens after the event. Public keys that correspond to the collected fingerprints are signed and published.
- Computers would be a hindrance (malware, key-logging)
#### Participation requirements
- physical attendance
- positive photo ID (preferably 2 types)
- your key ID, key type, hex fingerprint, and key size from private key
- writing implement & paper
#### Pre-party conduct
1. All attendees send public keys to host, who will create keyrings (RSA, DH/DSS)
2. Host prints list of key ID/type/fingerprint/size to be distributed at party
#### Party conduct
1. Each keyowner reads key ID/type/fingerprint/size and user ID from own printout
2. If key information matches printout, place a checkmark next to the key
3. All attendees form a line, each attendee walks down the line displaying ID
4. For each satisfactory ID, place another checkmark next to the key
#### Post-party conduct
1. Host provides a copy of each public keyring
2. Verify each keyring entry matches the printout, cross out any non-qualified keys (mismatch, or <2 checkmarks)
3. Sign each verified key
4. Send the signed keys to keyservers (sometimes host may collect keys and distribute a master signed ring)
### Keyservers
- [SKS Keyservers Pool](https://sks-keyservers.net/) (includes pgp.mit.edu & keys.gnupg.net)
- [PGP Global Directory](https://keyserver.pgp.com)
- [Keybase.io](https://keybase.io)

## Resources
- [The GNU Privacy Handbook](http://www.gnupg.org/gph/en/manual.html)
- [The Keysigning Party HOWTO](https://www.cryptnet.net/fdp/crypto/keysigning_party/en/keysigning_party.html)
- [LearnCryptography.com](https://learncryptography.com/)
- [The Prehistory of Public Key Cryptography](https://www.cs.columbia.edu/%7Esmb/nsam-160/)
- [ICS 54: History of Public-Key Cryptography](https://www.ics.uci.edu/~ics54/doc/security/pkhistory.html)
- [Cypherpunk Desert Bus: My Role in the 2016 ZCash Trusted Setup Ceremony](https://web.archive.org/web/20171010030051/https://petertodd.org/2016/cypherpunk-desert-bus-zcash-trusted-setup-ceremony) by Peter Todd
### tmp
- [The History of Cryptography](https://cs.stanford.edu/people/eroberts/courses/soco/projects/public-key-cryptography/history.html)
- [GPG/PGP Basics](https://aplawrence.com/Basics/gpg.html)
- [Understanding Public Key Cryptography and History of RSA](https://www.securityweek.com/understanding-public-key-cryptography-and-history-rsa)
- [PGP Setup](https://www.phildev.net/pgp/gpgkeygen.html)
- [Keysigning with the GNU/Linux Terminal](http://www.phillylinux.org/keys/terminal.html) (party attendee guide)
