# I'm XORRY

**Challenge Type: XOR Decryption**  

## Challenge

Hmmm... Seems we found some kind of password, it could give us access to the developer room :0. I'm xorry, i can't seem to crack it though.

### Cipher: 

```
flag=""
key=""
key_len=4

def encrypt(flag,key):
    key_long=(key * (len(flag)//len(key)))[:len(flag)]
    encrypted=result = list(map(lambda p, k: "{:02x}".format(ord(p) ^ ord(k)), flag, key_long))

    return encrypted
result="".join(encrypt(flag,key))
print(f'Output: {result}') #Cough cough Output: 2c38321e1250030c0c153a4e032103111600010e091c

```

## Solution 

1) First we need key, how we do that is by XOR CT and PT, using their code
> The PT will be the known 'NYP{'
2) 
```
ciphertext = "2c38321e1250030c0c153a4e032103111600010e091c"
key = "NYP{"

ciphertext_bytes = bytes.fromhex(ciphertext)

key_bytes = (key * (len(ciphertext_bytes) // len(key)))[:len(ciphertext_bytes)]

decrypted_result = "".join(chr(b1 ^ b2) for b1, b2 in zip(ciphertext_bytes, key_bytes.encode()))

print(f"Decrypted Output: {decrypted_result}")
```

3) Key will be 'babe' because only first four characters
4) Do it again but this time with the key
5) Flag: NYP{p1aintX+a@attackk}

## P.S

I thought it was cheating to use 'NYP{' to decrypt the key. So I very sh000ck to find out about that you are supposed to do it. 
<br>
I'm not very smart. 