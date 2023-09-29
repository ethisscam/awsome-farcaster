
# awsome-farcaster
A knowledge base for understanding farcaster and its ecosystem. It doesn't aim for a complete resource but some I am personally interested. If you want to dig more go to [a16z/awesome-farcaster](https://github.com/a16z/awesome-farcaster)


## Farcaster
- [Protocol Discussion](https://github.com/farcasterxyz/protocol/discussions/)

### FID
FID is a unique identenfier for the farcaster user. It's generated on Optimism chain when users register on farcaster.
#### Contracts



| Contract | Address|
|  --------  |  -------  |
| IdRegistry | [0x00000000fcaf86937e41ba038b4fa40baa4b780a](https://optimistic.etherscan.io/address/0x00000000fcaf86937e41ba038b4fa40baa4b780a) |

#### Get FID
- Call  Public Farcaster Hub API. Replace name(tian7) below with your own account(@xxx)
[http://nemes.farcaster.xyz:2281/v1/userNameProofByName?name=tian7](http://nemes.farcaster.xyz:2281/v1/userNameProofByName?name=tian7)
```
{
  "timestamp": 1694666002,
  "name": "tian7",
  "owner": "0x3f93eda4296612736c3448354691413d6b32fbb6",
  "signature": "/Tl4uN0lK6kj36GMVsTCJ7bKbtSWws7skS3QH0JtNLBtTer7YqGOWwEoObiCXfcDSc4+OU0o92VXkhQUcS2a5Bs=",
  "fid": 20045,
  "type": "USERNAME_TYPE_FNAME"
}
```
- Call neynar API. You need a secret API Key.
[https://api.neynar.com/v1/farcaster/user-by-username/?api_key={api_key}&username=manan&viewerFid=191
](https://api.neynar.com/v1/farcaster/user-by-username/?api_key={api_key}&username=manan&viewerFid=191)
```
{
  "result": {
    "user": {
      "fid": 191,
      "username": "manan",
      "displayName": "Manan ",
      "pfp": {
        "url": "https://i.imgur.com/nW6pvvm.jpg"
      },
      "profile": {
        "bio": {
          "text": "Building @neynar 🪐 | ex-Coinbase",
          "mentions": []
        }
      },
      "followerCount": 578,
      "followingCount": 222,
      "verifications": [
        "0xe756236ef7fd64ebbb360465c621c7db5a336f4d",
        "0xf15a2f34c52da9464d6890e073e233579dba1501"
      ],
      "activeStatus": "active",
      "viewerContext": {
        "following": true,
        "followedBy": true
      }
    }
  }
}
```

#### Ideas
- A marketplace for trading FID(launch a FID NFT)

### HUB
Hub stores all farcaster datas.  Anyone can run a hub node.
#### Hub Tutorial
Find it at [https://www.thehubble.xyz/intro/hubble.html](https://www.thehubble.xyz/intro/hubble.html)
- Run a Hub
[https://www.thehubble.xyz/intro/install.html](https://www.thehubble.xyz/intro/install.html)
- Choose a cloud provider
[https://warpcast.notion.site/Set-up-Hubble-on-EC2-Public-23b4e81d8f604ca9bf8b68f4bb086042](https://warpcast.notion.site/Set-up-Hubble-on-EC2-Public-23b4e81d8f604ca9bf8b68f4bb086042)
#### Alternative Hub Provider
- [neynar](https://neynar.com/)

### Storage
Users need to rent storage for using Farcaster. There're 200K storage unit available per year right now.  Rented storage cann't be rerented to others.
1 storage unit is used for(expert from [FIP-6](https://github.com/farcasterxyz/protocol/discussions/98)):
>-   5,000 messages for Casts
>-   2,500 for Reactions
>-   2,500 for Links
>-   50 for Verifications
>-   50 for UserData

In general these contents may occupy 100 KB which means the total size of 200K storage unit will be 20GB.
#### Economic
- Payment is handled on Optimism
- There will be diffrent price strategy for storage unit. Here's a proposal from [FIP](https://github.com/farcasterxyz/protocol/discussions/126)
> * The number of storage units is set to 200,000
> * The price increases by $7 for each 50k units rented.
> 
> |Storage Units | Consumed	Yearly Price	| Monthly Price (reference only)
> |----|----|----|
> |0 - 50k|	$7|	$0.58|
> |50k - 100k|	$14	|$1.16|
> |100k - 150k|	$21	|$1.75|
> |150k - 200k|	$28	|$2.33|

In fact every storage unit can store the same size contents. The different price is for limit the sharp increasment of unit.

#### Contracts
| Contract | Address|
|  --------  |  -------  |
| StorageRegistry| [0x00000000fcce7f938e7ae6d3c335bd6a1a7c593d](https://optimistic.etherscan.io/address/0x00000000fcce7f938e7ae6d3c335bd6a1a7c593d) |
