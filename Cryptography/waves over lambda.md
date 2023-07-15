# waves over lambda
Category: Crypto
Points: 300
Author: Kaden Wu
## Problem Description
We made a lot of substitutions to encrypt this. Can you decrypt it? Connect with `nc jupiter.challenges.picoctf.org 39894`.
## Writeup
After using the `netcat` command to connect to the server, we get a bunch of nonsense:
```
-----------------------------------------------------------------------------------------------------------------------------------
ykutqbsr haqa xr wklq vfbt - vqajlauyw_xr_y_knaq_fbidmb_btvfytswla
-----------------------------------------------------------------
daseaau lr shaqa ebr, br x hbna bfqabmw rbxm rkiaehaqa, sha dkum kv sha rab. darxmar hkfmxut klq habqsr sktashaq shqklth fkut paqxkmr kv rapbqbsxku, xs hbm sha avvays kv ibgxut lr skfaqbus kv abyh kshaq'r wbqurbum anau ykunxysxkur. sha fbewaqsha dars kv kfm vaffkerhbm, dayblra kv hxr ibuw wabqr bum ibuw nxqslar, sha kufw ylrhxku ku mayg, bum ebr fwxut ku sha kufw qlt. sha byyklusbus hbm dqklths kls bfqabmw b dkc kv mkixukar, bum ebr skwxut bqyhxsayslqbffw exsh sha dkuar. ibqfke rbs yqkrr-fattam qxths bvs, fabuxut btbxurs sha ixzzau-ibrs. ha hbm rlugau yhaagr, b waffke ykipfacxku, b rsqbxths dbyg, bu bryasxy brpays, bum, exsh hxr bqir mqkppam, sha pbfir kv hbumr klsebqmr, qaraidfam bu xmkf. sha mxqayskq, rbsxrvxam sha buyhkq hbm tkkm hkfm, ibma hxr ebw bvs bum rbs mkeu bikutrs lr. ea acyhbutam b vae ekqmr fbzxfw. bvsaqebqmr shaqa ebr rxfauya ku dkbqm sha wbyhs. vkq rkia qabrku kq kshaq ea mxm uks datxu shbs tbia kv mkixukar. ea vafs iamxsbsxna, bum vxs vkq ukshxut dls pfbyxm rsbqxut. sha mbw ebr aumxut xu b raqauxsw kv rsxff bum acjlxrxsa dqxffxbuya. sha ebsaq rhkua pbyxvxybffw; sha rgw, exshkls b rpayg, ebr b dauxtu xiiaurxsw kv lursbxuam fxths; sha naqw ixrs ku sha arrac ibqrh ebr fxga b tblzw bum qbmxbus vbdqxy, hlut vqki sha ekkmam qxrar xufbum, bum mqbpxut sha fke rhkqar xu mxbphbuklr vkfmr. kufw sha tfkki sk sha ears, dqkkmxut knaq sha lppaq qabyhar, daybia ikqa rkidqa anaqw ixulsa, br xv butaqam dw sha bppqkbyh kv sha rlu. 
```

At first, we don't have a clue at what this could mean. But we could probably guess that this would be a substitution cipher. Monoalphabetic substitution would be a good first choice.

Luckily, after plugging the ciphertext into `DCODE`, we get our answer:
```
------------------------------------------------------------------------------- 
CONGRATS HERE IS YOUR FLAG - FREQUENCY_IS_C_OVER_LAMBDA_AGFLCGTYUE 
------------------------------------------------------------------------------- 
BETWEEN US THERE WAS, AS I HAVE ALREADY SAID SOMEWHERE, THE BOND OF THE SEA. BESIDES HOLDING OUR HEARTS TOGETHER THROUGH LONG PERIODS OF SEPARATION, IT HAD THE EFFECT OF MAKING US TOLERANT OF EACH OTHER'S YARNSAND EVEN CONVICTIONS. THE LAWYERTHE BEST OF OLD FELLOWSHAD, BECAUSE OF HIS MANY YEARS AND MANY VIRTUES, THE ONLY CUSHION ON DECK, AND WAS LYING ON THE ONLY RUG. THE ACCOUNTANT HAD BROUGHT OUT ALREADY A BOJ OF DOMINOES, AND WAS TOYING ARCHITECTURALLY WITH THE BONES. MARLOW SAT CROSS-LEGGED RIGHT AFT, LEANING AGAINST THE MIXXEN-MAST. HE HAD SUNKEN CHEEKS, A YELLOW COMPLEJION, A STRAIGHT BACK, AN ASCETIC ASPECT, AND, WITH HIS ARMS DROPPED, THE PALMS OF HANDS OUTWARDS, RESEMBLED AN IDOL. THE DIRECTOR, SATISFIED THE ANCHOR HAD GOOD HOLD, MADE HIS WAY AFT AND SAT DOWN AMONGST US. WE EJCHANGED A FEW WORDS LAXILY. AFTERWARDS THERE WAS SILENCE ON BOARD THE YACHT. FOR SOME REASON OR OTHER WE DID NOT BEGIN THAT GAME OF DOMINOES. WE FELT MEDITATIVE, AND FIT FOR NOTHING BUT PLACID STARING. THE DAY WAS ENDING IN A SERENITY OF STILL AND EJQUISITE BRILLIANCE. THE WATER SHONE PACIFICALLY; THE SKY, WITHOUT A SPECK, WAS A BENIGN IMMENSITY OF UNSTAINED LIGHT; THE VERY MIST ON THE ESSEJ MARSH WAS LIKE A GAUXY AND RADIANT FABRIC, HUNG FROM THE WOODED RISES INLAND, AND DRAPING THE LOW SHORES IN DIAPHANOUS FOLDS. ONLY THE GLOOM TO THE WEST, BROODING OVER THE UPPER REACHES, BECAME MORE SOMBRE EVERY MINUTE, AS IF ANGERED BY THE APPROACH OF THE SUN.
```
`picoCTF{frequency_is_c_over_lambda_agflcgtyue}`
