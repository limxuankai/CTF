# Ceaser Is Fun!

**Challenge Type: Reverse Cipher**  

## Challenge

Deep in the game files lies an easter egg, a mini game with some secrets encrypted. Why not have some fun and try it out?

### Cipher
```
CHARACTER_SET = """0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ!"#$%&'()*+,-./:;<=>?@[\\]^_`{|}~ """

def caesar(message: str, key: int):
    """ Caesar Cipher with a custom character set """
    key %= len(CHARACTER_SET)
    return message.translate(str.maketrans(CHARACTER_SET, CHARACTER_SET[key:]+CHARACTER_SET[:key]))

def encrypt(message: str, key: int):
    """ Recursive encryption of caesar """
    if len(message) < 2:
        return caesar(message, key)
    return caesar(message[0] + encrypt(message[1:-1], key+1) + message[-1], key)
```

### Output
```
Output = 'qf=4}[C"cBnDH?kW|h('
```

## Solution 

1) Just swap the position(such as + to -)to write a decryption script:
```
def caesar1(message: str, key: int):
    """ Caesar Cipher with a custom character set """
    key %= len(CHARACTER_SET)
    return message.translate(str.maketrans(CHARACTER_SET[key:] + CHARACTER_SET[:key], CHARACTER_SET))

def decrypt1(message: str, key: int):
    """ Recursive decryption of caesar """
    if len(message) < 2:
        return caesar1(message, -key)  
    return caesar1(message[0] + decrypt1(message[1:-1], key-1) + message[-1], -key)
```
2) Now bruteforce it

```
for key in range(0, 96):
    result = decrypt1(Output,key)
    if 'NYP' in result:
        print(result)
    else:
        print(False)
```

3) Flag: NYP{7h@t_w45_fuN!!} 

## P.S

This should really be in reversing but crypto works here. 
<br>
Chatgpt wrote the code and messed up the +1, luckily I was there to put -1. 
