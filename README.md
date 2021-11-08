# dogecoin-TIGER

```
Transaction
Improvement for
Giphys & 
Emojis in
op_Return
```


a reference for implementing meme support into standard dogecoin transactions
you can find us on discord https://discord.gg/zdUFFdQ2Hq

and please have a look at the discussion on the dogecoin core github:
https://github.com/dogecoin/dogecoin/discussions/2276


here is a running test for the encoding, as the index.html provides:
http://tiger.dogeflipping.info/


# idea

there are many ways to make dogecoin more fun to use and therefore be adapted by more people.
we want to add emojis and giphy links to transactions because we think that would be fun.

the upcoming tx fee reduction leads to new way for new ideas on the reliable doge network.
with a standard for sending memes / emojis, we pave the way for a smart doge protocol running
just in the existing boundaries of the dogecoin-core protocol - no changes needed!

everybody can now already send a doge transaction with a emoji or giphy link inside - an example: 
[db78e674f7ea0517810a3ce9f1002aeb5f65ce5fbe559b8a3c1c8f2cb2064e98](https://chain.so/api/v2/tx/DOGE/db78e674f7ea0517810a3ce9f1002aeb5f65ce5fbe559b8a3c1c8f2cb2064e98)

check the OP_RETURN part:
```
script_asm: "OP_RETURN 804520206",
script_hex: "6a040e01f42f"

0e = TIGER content
01f42f = 🐯
```
# protocol
## overview

Protocol Part | Routing Flag | Content 
------------- | ------------ | -------
OP_RETURN     | <2 Byte>     | <up to 78 Byte> 

## Routing Flags

flag | content | planned use | example | result
---- | ------- | ----------- | ------- | ------
00-09 | <up to 78 Byte> | reserved (other use cases) | - | -
0a | <44 Byte> | Solana NFT | 44zJATRBfYz5B8cG75uXByM4S5qNkf7P71HNjvXtGmgA | -
0b | <42 Byte> | Fantom NFT | 0xdb087e7c1115cff0499d34dd5eabb0453a363f0e | -
0c | <32 Byte> | Tezos NFT | KT1XHwHm57K92XEsE5FNNDbeNk22eHsEwkBc | -
0d | <up to 78 Byte> | Ethereum NFTs from a specific community Contract? | - | -
0e | <hex-representation of an unicode emoji> | emojis | 0e01f42f | 🐯
0f | <giphy shortlink> | giphys | 0f<hex-encoded Q4IN9hDFEwISDujIbe | ![Image giphy](https://media.giphy.com/media/Q4IN9hDFEwISDujIbe/giphy.gif)

## NFT Transactions

decoding OP_RETURN hex values -> NFT_ID -> insert Webviewer of NFT (Whitelisted NFTs only?)                                                 
                                                 
## Emoji Transactions
decoding OP_RETURN hex values -> EMOJI_ID -> insert emoji according to Unicode Emoji
                                               
## Giphy Transactions 
decoding OP_RETURN hex values -> GIPHY_ID -> insert image with https://media.giphy.com/media/<GIPHY_ID>/giphy.gif link

# reference implementations
## upcoming
  as a dogecoin-qt fork
## existing
### sending
  check out https://github.com/fmhc/dogecoin-OP_RETURN
  and do something like python3 send-OP_RETURN.py "nkv6k1wy5pRaZJbY3Buq2PS5s21oJHP78D" 1.0 '0e01f432' 1
### looking at
  clone this repository and open index.html file
  
  
# roadmap

  current short-term main objectives:
  - TIGER protocol definition as part of the official dogecoin-core project
  - working prototype in dogecoin-qt
  
  
  this is somehow a roadmap:
- [x] technical background check
- [x] proof-of-concept
- [x] minimal visualisation prototype
- [ ] get official support from all main core devs (work in progress)
- [ ] discuss why giphy IDs and Emojis are much safu & much wow for future of dogecoin as payment
- [ ] add prototype of safe emoji+giphy send/receive function to dogecoin-qt reference wallet as PR in 1.14.4-dev with optional build flag
- [ ] discussion / agreement to have TIGER emoji / giphy support as optional setting in dogecoin-qt 1.21
- [ ] implement safu emoji+giphy send / receive function in other wallets  
- [ ] get more devs on board to build smart contract addon for doge nodes (smart contract VM)
- [ ] implement animal charity emoji wallet example with sub-routing of funds based on animal emojis (frog shelter and wolf farms, you know)
- [ ] get some designers who can communicate this slightly authistic words in memes
  
# contribute
we're open for contributions and discussions, please check out the links above and get on the team asap!
  
