# Meshed Network

<div id="table-of-contents" />
## Table of Contents

1. [Introduction](#introduction)
2. [Motivation](#motivation)
3. [Security](#security)
4. [Two types of security](#types)
  1. [Settlement](#settlement)
5. [Cryptalk Reverse Engineering](#cryptalk)
6. [Secure Chat](#secure-chat)
7. [Glossary](#glossary)

<div id="introduction" />
## Introduction

This file is a note of my research into cryptography, which is used at Makers Academy's final project [mesheeChat]. It records the motivation of integrating client side cryptography, and my approach to the problem.

[mesheeChat]: https://github.com/jindai1783/mesheeChat

<div id="motivation" />
## Motivation

"What if you could communicate with anyone, anywhere, without going over an inch of corporate or government cable?"

Meshed network vs Internet Service Provider (ISP)

1. Centralised authority control-free
2. Robustness in natural disaster
3. Political free
4. No more spying

**[back to top](#table-of-contents)**

<div id="security" />
## Security

*Resources*
* [ChatSafe]
* [FireChat]
* [Encrypted Chat]
* [Cryptocat]

[ChatSafe]: https://github.com/DavidTimms/ChatSafe
[FireChat]: https://firechat.firebaseapp.com
[Encrypted Chat]: http://www.pubnub.com/blog/sending-encrypted-chat-messages-tutorial/
[Cryptocat]: https://github.com/cryptocat/cryptocat/

Maybe a chat room structure is better than a p2p encryption?
Chat room only allow people with the key to access.
Other people cannot access the chat room unless they have got the key.

<div id="types" />
## Two types of security

1. A communication channel that the server don't allow outsider to see.
2. A communication channel that the server itself cannot see.

*Resources*
* [Private Socket room]
* [Candy]

[Private Socket room]: https://www.npmjs.com/package/innkeeper-socket.io
[Candy]: https://candy-chat.github.io/candy/

**[back to top](#table-of-contents)**

<div id="settlement" />
### Settlement

Since we would like the government to have no way to decipher the message, we want that even the server cannot see the content. HTTPS may do the trick, but it is too complex to start working on that. A simpler approach is to find a Node way of encrypting chat messages. And this, has lead us to [Cryptalk]. This is a npm that only allow messaging when all party in the chatroom have the key.

[Cryptalk]: https://www.npmjs.com/package/cryptalk

At one stage, we almost used [FreeStep], but then we realised that the code is maintained by only one single developer, and there are parts missing in the documentation (gitignored ssl folder), which forced us to look into other modules and eventually selected Cryptalk as our settlement.

[FreeStep]: https://freestep.net

<div id="cryptalk" />
## Cryptalk Reverse Engineering

The core module in the Cryptalk is [cryptojs]

[cryptojs]: http://cryptojs.altervista.org/api/#.VO4Oy8bHJRE

A glimpse of what this module does can be seen from my [Cryptography] repository.
This uses Advanced Encryption Standard (AES) for encryption, and can be how we implement the security layer of Meshee.

[Cryptography]: https://github.com/jindai1783/Cryptography

**[back to top](#table-of-contents)**

<div id="secure-chat" />
## Secure Chat

A simple integration of Socket.io chat with client-side encryption can be find at the repository [Secure Chat]. It uses AES encrytion, and only when the cipher key and decipher key matches you can see the message, otherwise you will only see 'null'.

[Secure Chat]: https://github.com/jindai1783/Secure_Chat

<div id="glossary" />
## Glossary

* Ad hoc networking: a system of network elements that combine to form a network requiring little or no planning.
* NSA: National Security Agent

**[back to top](#table-of-contents)**