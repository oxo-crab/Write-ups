# Baby RSA
## Description
RSA is for babies. So we improved it by taking it to the next dimension.

## Solution
Putting `n` in dcode.fr gives `p` and `q`:
```
p = 142753777417406810805072041989903711850167885799807517849278708651169396646976000865163313860950535511049508198208303464027395072922054180911222963584032655378369512823722235617080276310818723368812500206379762931650041566049091705857347865200497666530004056146401044724048482323535857808462375833056005919409
q = 161374151633887880567835370500866534479212949279686527346042474641768055324964720409600075821784325443977565511087794614167314642076253331252646071422351727785801273964216434051992658005517462757428567737089311219316483995316413254806332369908230656600378302043303884997949582553596892625743238461113701189423
```
<br>
Reference for matrix RSA decryption:
https://www.researchtrend.net/ijet/pdf/13%20%20Matrix%20Modification%20of%20RSA%20Public%20Key%20Cryptosystem%20and%20its%20Variant%20Manju%20Sanghi%203513.pdf <br>

```py
phi = (p**2 -1)*(q**2 - 1)
d = pow(e, -1, phi)

#ct contains the given ciphertext output
c = matrix(Zmod(n), [[ct[0], ct[1]], [ct[2], ct[3]]])
pt = c ^ d

flag = b''
for row in pt:
    for ele in row:
        flag += long_to_bytes(int(ele))
print(flag)
```
## Flag
`BITSCTF{63N3r41_11N34r_6r0UP_C4ND0_4NY7H1N6}`