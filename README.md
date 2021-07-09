# dogecoin-TIGER

```
Transaction
Improvement for
Giphy & 
Emoji
Return
```
a reference for implementing meme support into standard dogecoin transactions
you can find us on discord https://discord.gg/g5NmArGV
and please have a look at the discussion on the dogecoin core github:
https://github.com/dogecoin/dogecoin/discussions/2276

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
0a-0d | <up to 78 Byte> | reserved (contract interaction) | - | -
0e | <hex-representation of an unicode emoji> | emojis | 0e01f42f | 🐯
0f | <giphy shortlink> | giphys | 0f<hex-encoded Q4IN9hDFEwISDujIbe | ![Image giphy](https://media.giphy.com/media/Q4IN9hDFEwISDujIbe/giphy.gif)

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
  
