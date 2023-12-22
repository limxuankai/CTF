# Which map did bro play on?

**Challenge Type: AES Reversal**  

## Challenge

This one guy had the best map seed ever, I asked him for the seed but he is gatekeeping it super hard. Help me find what map he was playing on and get the flag too pls. Map generated on: 2023-12-02 11:29:28.139245 Encrypted flag: yHfd2SPRbpgpnWbILASrx1ZPrVZvTn6eX5SiNLirlZE=

### Cipher: 
```
from Crypto.Cipher import AES
from random import*
import datetime
import base64
#pip install pycryptodome

flag = b"flag"
iv = b"\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"
block_size = 16
flag = flag.ljust((len(flag) + block_size - 1) // block_size * block_size, b"\0")
time = datetime.datetime.now()
print("Map generated on " + str(time))


map_seed = int(round((time.timestamp() * 10000),0))
seed(map_seed)


key = []
for i in range(24):
    key.append(randint(0,255))

keyBytes = bytes(key)


cipher = AES.new(keyBytes,AES.MODE_CBC, iv)
ciphertext = cipher.encrypt(flag)
encrypted_flag = base64.b64encode(ciphertext).decode('utf-8')

print("Encrypted flag: " + encrypted_flag)

```
## Solution 

1) With the time, we can find the key to the AES
> This is because they used the random.seed(time) and they used the current time, which means we can get the same key to decrypt their nonsense.
2) Now write script that reverses it
```
encrypted_flag = "yHfd2SPRbpgpnWbILASrx1ZPrVZvTn6eX5SiNLirlZE="
iv = b"\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"
block_size = 16

timestamp_str = "2023-12-02 11:29:28.139245"
time = datetime.datetime.strptime(timestamp_str, "%Y-%m-%d %H:%M:%S.%f")

map_seed = int(round((time.timestamp() * 10000), 0))

random.seed(map_seed)

key = [random.randint(0, 255) for _ in range(24)]
keyBytes = bytes(key)

cipher = AES.new(keyBytes, AES.MODE_CBC, iv)

decrypted_flag = cipher.decrypt(base64.b64decode(encrypted_flag)).rstrip(b"\0")

print(f"Decrypted flag: {decrypted_flag.decode('utf-8')}")
```

3) Flag: NYP{G0Od_JoB_l!l_br@}

## P.S

I seen this in Tenable. <br>
YOU CANT TRICK ME AGAIN FOOL! 
<br>
Link is here: [crist075 Writeup](https://cristi075.github.io/TenableCTF-2023-PseudoRandom)
<br>
At least this doesn't need bruteforce, right tenable.