+++
author = "WNO-IQ"
title = "Chapter 21: Security"
date = "2021-12-06"

description = "My A2 Computer Science notes"
tags = [
    "Notes",
    "Study"
]
keywords = ["CIE","Alevel","A2","Computer Science","Notes"]
categories = [
    "A2-CS-notes"
]

+++

# Chapter 21: Security

## Encryption fundamentals

There are three issues that will be considered in this chapter:

- is the encryption algorithm suff iciently `robust(adj.强健的，鲁棒)` to prevent the encrypted data being decrypted by some unauthorised third-party?
- how is it possible to ensure that a secret key remains secret?
- how can the receiver of a communication be sure who sent the communication?

The use of encryption is illustrated in Figure 21.01.The process starts with original data referred to as `plaintext`. The plaintext is encrypted by an encryption algorithm which makes use of a `key`. The product of the encryption is `ciphertext`, which is transmitted to the `recipient`. When the transmission is received it is decrypted using a decryption algorithm and a key to produce the original plaintext.
![](cs-note-img/Pastedimage20211206133458.png)

- **Plaintext**: data before encryption
- **Ciphertext**: the result of applying an encryption algorithm to data
- **Encryption**: the making of cipher text from plain text.

### Security concerns

There are a number of security concerns relating to a transmission.

- **Confidentiality**: Only the intended recipient should be able to decrypt the ciphertext.
  - The confidentiality concern arises because a message could be intercepted during transmission and the contents read by an unauthorised person.
- **Integrity**: The ciphertext must not be modified during transmission.
  - The concern about integrity reflects the fact that the transmission might be interfered with deliberately but also that there might be accidental corruption of the data during transmission.
- **Authenticity**: The receiver must be certain who sent the ciphertext.
- Non-repudiation: Neither sender nor receiver should be able to deny involvement in the transmission.
- Availability: Nothing should happen to prevent the receiver from receiving the transmission.
  _This chapter will consider only confidentiality, authenticity and integrity._

### Encryption methods

- **Public key**: encryption key which is not secret.
- **Private key**: encryption key which is a secret.
- **Symmetric key encryption**: one private key is held by both sender and receiver and is used for both encryption and decryption
  - In symmetric key encryption there is just one key.
  - This key is a secret shared by the sender and the receiver of a message.
  - The sender uses the encryption algorithm together with the key to encrypt some plaintext. The receiver decrypts the ciphertext using the same key.
  - The issue with symmetric key encryption is delivery of the secret key.
- **Asymmetric key encryption**: there is a public key and a private key one of which is used for encryption and the other for decryption - Asymmetric encryption is to be used the process is initiated by someone in possession of two keys. - One of these is a public key which is sent to anyone who is going to partake in an encrypted communication. The other is a secret private key which is never sent to anyone. - Having a private key means of secure transmission of a secret key is no longer an issue.
  <br>

## Digital signatures and digital certificates

Using asymmetric encryption, the decryption–encryption works if the keys are used the other way round.

- An individual can `encrypt a message with a private key and send this to a recipient who has the corresponding public key` and who can then use this to decrypt the received ciphertext. - It could be used if it was important to verify who the sender was. - Only the sender has the private key and the public key only works with that one specific private key. Therefore, if the recipient finds that the decryption is successful, the message has in effect been received with a digital signature identifying the sender.
  <br>

- An alternative is for the sender to use a public cryptographic one-way hash function which creates a number that is uniquely defined for the particular message, called a ‘`digest`’. The process at the sender’s end of the transmission is outlined in Figure 21.02. The `private key` is used to encrypt the `digest`. The encrypted digest is the `digital signature`.
  ![](https://raw.githubusercontent.com/emm-Xe/emm-Xe.github.io/master/static/cs-note-img/Pastedimage2102.png)
  <br>

- The processes that take place at the receiver end are outlined in Figure 21.03. The same public one-way hash function is used to `create a digest from the received message`. Then the encrypted version of the `original digest is decrypted using the public key`.
- If the `two digests are identical` the receiver can be confident that the message is `authentic` and has been transmitted `unaltered`.
- Note that the `digital signature is different each time` this process is used. This is because the digest is uniquely defined by the hash function being applied to that particular message.
  ![](cs-note-img/Pastedimage20211206185322.png)
  <br>

- However, the authenticity only confirms to the receiver that the message was sent from the person who had sent them the public key. It does not consider the fact that someone might create a public key and pretend to be someone else.
- Therefore, a more strict way of ensuring authentication is needed. This can be provided by a `Certification Authority (CA)` as part of a `Public Key Infrastructure (PKI)`.
  ![](cs-note-img/Pastedimage20211206190316.png)
- The steps taken by the would-be receiver to obtain a digital certificate to allow safe public key delivery are illustrated in Figure 21.04.
- The process can be summarised as follows:

1. An individual (person A) who is a would-be receiver and has a public–private key pair contacts a local CA.
2. The CA confirms the identity of person A.
3. Person A’s public key is given to the CA.
4. The CA creates a public-key certificate (a digital certificate) and writes person A’s public key into this document.
5. The CA uses encryption with the CA’s private key to add a digital signature to this document.
6. The digital certificate is given to person A.
7. Person A posts the digital certificate on a website.

The following are a few notes to summarise the options available. - The starting position is someone who has a public–private key pair which are associated with a specific asymmetric key encryption algorithm.

- This person could just make the public key available to anyone who is going to be either a sender or a receiver.
- For optimum security the person instead sends the public key to a Certification Authority. - The Certification Authority creates a digital certificate which contains the public key with proof of the ownership of the public key.
- Anyone wishing to use the public key obtains it from this digital certificate.
- A message encrypted with the public key could be sent to the owner of the private key.
- A message encrypted with the private key could be sent to anyone having the public key.
- The owner of the private key could use it to create a digital signature that could be used to authenticate an email.

## Symmetric key encryption methods

- Data Encryption Standard (DES)

  - Advanced Encryption Standard (AES)
  - Simplified DES (S-DES)

- In S-DES 8-bit blocks are encrypted. A 10-bit key is chosen.
- The first stage is to create two 8-bit keys from the 10-bit key.
- The first step in this first stage is a permutation
- Suppose that the 10-bit key is chosen to be 0101010101 when subjected to a permutation which can be represented by 3 5 2 7 4 10 1 9 8 6 it becomes 0010110011
  > It's not finished yet

<br>

## Public key encryption methods

- RSA (Rivest-Shamir-Adleman) is the usual method for public key encryption.
- The major features of the method are the key generation algorithm and the encryption function.
- The key generation can be summarised as follows:

1. Two very large prime numbers p and q are chosen and their product n is calculated
2. The product (p-1)(q-1) is calculated
3. A prime number e less than (p-1)(q-1) and not a factor of it is chosen (65537 is the usual choice)
4. Another number d is found which satisfies the condition that the product of d times e when divided by (p-1)(q-1) gives a remainder of 1
5. The public key becomes the pair (n,e)
6. The private key becomes the pair (n,d)

- If such a number x is to be encrypted as y then y is calculated so that the following relationship holds:
  $$y = x^e \bmod n$$
- A similar relationship involving d rather than e is used for decryption.
  <br>

## SSL and TLS

- SSL and TLS*(upgraded version of SSL)* encryption protocols are used in client\-server applications.
- Functions:
  - Encryption
  - Compression of data
  - Integrity checking
- Used in online shopping and banking websites
  ![](cs-note-img/Pastedimage20211207082541.png)
  <br>

## Quantum cryptography

- **Photon**: The particles that transmit light are called photons
- **Polarisation**: (physics) the fact of waves of light, etc. vibrating in a single direction 使（光波等）偏振
  The direction each photon vibrates in is called its `polarisation`, and is represented in a diagram as a `double-ended arrow`.
- A photon can be created with a specific polarisation to represent a value for a bit.
  ![](cs-note-img/Pastedimage20211207140945.png)
- This scheme can be used to enable a sender and receiver to create a ‘shared secret’ code consisting of a number of bits.
  ![](cs-note-img/Pastedimage20211207141305.png)
- The first row indicates the bit sent
- The second row shows the basis used for this with
  - - representing vertical and horizontal pair
  - x representing the diagonal pair
- `The sender` chooses the bit pattern at random and also the polarisation basis for each value `at random`.
- The third row shows the `receiver’s` choice for the polarisation basis for each value `at random`.
- Following the transmission the sender informs the receiver about the polarisation basis used for each value. The receiver responds by saying which ones were chosen to match. For these matches there is now a stored value for a bit. In the example shown a ‘shared secret’ code 1001 has been created.

- The above scheme has been incorporated in Quantum Key Distribution (QKD) systems.
- Purpose
  - QKD offers an alternative for the key transfer.
- Benefits
  - The advantage of QKD is that the transfer does not involve defined values just photons.
  - Anyone trying to intercept the flow of photons in an attempt to discover their polarisation will by the laws of quantum mechanics destroy the photons.
  - A photon cannot be detected and measured then sent on again.
- Drawbacks
  - It cannot be implemented using standard communication media.
  - It requires a dedicated, special purpose ‘quantum channel’ between sender and receiver.
  - The costs of providing this are very high so routine use is unlikely.
