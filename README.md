# Meshed Network

## Motivation

"What if you could communicate with anyone, anywhere, without going over an inch of corporate or government cable?"

Meshed network vs Internet Service Provider (ISP)
1. Centralised authority control-free
2. Robustness in natural disaster
3. Political free
4. No more spying

## Security

Resources
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

2 types of security

1. A communication channel that the server don't allow outsider to see.
2. A communication channel that the server itself cannot see.

* [Private Socket room]
* [Candy]

[Private Socket room]: https://www.npmjs.com/package/innkeeper-socket.io
[Candy]: https://candy-chat.github.io/candy/

### Settlement

Since we would like the government to have no way to decipher the message, we want that even the server cannot see the content. HTTPS may do the trick, but it is too complex to start working on that. A simpler approach is to find a Node way of encrypting chat messages. And this, has lead us to [Cryptalk]. This is a npm that only allow messaging when all party in the chatroom have the key.

[Cryptalk]: https://www.npmjs.com/package/cryptalk

## Glossary

Ad hoc networking: a system of network elements that combine to form a network requiring little or no planning.
NSA: National Security Agent