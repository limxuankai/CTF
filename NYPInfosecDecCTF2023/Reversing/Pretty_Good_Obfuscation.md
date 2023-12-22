# Pretty Good Obfuscation

**Challenge Type: Cryptographic Reversal**  

## Challenge

Pretty Good Obfuscation
<br>
Took me a while, but I finally made a pretty good encryption script. Do you want to try reversing it? I've used some obfuscation methods on it to make it harder to read, good luck!

<br>
Encryption Code: 

`const164 = chr(100) + chr(101) + chr(102) + chr(105) + chr(110) + chr(105) + chr(116) + chr(101) + chr(108) + chr(121) + chr(110) + chr(111) + chr(116) + chr(95) + chr(97) + chr(107) + chr(101) + chr(121) + chr(95) + chr(116) + chr(114) + chr(117) + chr(115) + chr(116) + chr(95) + chr(105) + chr(51) + chr(104) + chr(83) + chr(117) + chr(79) + chr(108)`
`const188 = chr(102) + chr(108) + chr(97) + chr(103) + chr(46) + chr(116) + chr(120) + chr(116)`

```def const645():
    return open(const188, "r").read()
def const346(const264):
    return __import__(chr(98) + chr(97) + chr(115) + chr(101) + chr(54) + chr(52)).b64encode(const264.encode()).decode()

def const905(const264, const164):
    return (lambda x, y: ''.join([chr(ord(const153)^ord(const351)) for (const153, const351) in zip(x, y)]))(const264, const164)

const264 = const645()
const923 = const346(const264)
print(const923)
const024 = const905(const923, const164)
with open(const188, "wb") as f:
    f.write(const024.encode())
```

Flag: 

`30,&`
`[LQ6;^-o$X=$K<X`
`"zU`

## Solution 

1) Convert all the chr(numbers) into ascii characters, const character into  ascii and simply it. You should get the following
`import base64 as b64`  
`file_key = "definitelynot_akey_trust_i3hSuOl"`  
`file_extension = "flag.txt"`  

`def read():`
    `return open(file_key + "." + file_extension, "r").read()`

`def base64_encode(content):`
    `return b64.encode(content.encode()).decode()`

`def xor:`
    `return ''.join([chr(ord(char_x) ^ ord(char_y)) for char_x, char_y in zip(x, y)])`

`encoded_content = base64_encode(read())`
`result = xor_strings(encoded_content, file_key)`
`print(result)`
`with open(file_key + "." + file_extension, "wb") as file:`
    `file.write(result.encode())`

> Explaination time: Basically code just base 64 encoded the flag before XOR ing it  
> So the plan is just to reverse the code via converting it into bytes, XOR it with the key and base64 decode it.  
2) Write a script for this: 

`import base64`  

`XOR_Key = b"definitelynot_akey_trust_i3hSuOl"`  
`Path_Flag = "flag"`  

`def encode(file):`  
    `return base64.b64encode(file.encode()).decode()`

`def XOR(original, Key):`
    `result = bytearray()`
    `for x, y in zip(original, Key):`
        `result.append( x ^ y)`
    `return bytes(result)`


`Encoded_File = (open(Path_Flag, "rb").read())`
`XORED_FILE = XOR(Encoded_File, XOR_Key)`
`Ans = base64.b64decode(XORED_FILE).decode("utf-8")`
`with open(Path_Flag, "w") as f:`
    `f.write(Ans)`

3) Run the script
4) Find the flag in the flag file: YBN{o8fu5cA7t1On_1s_fUn}

### P.S 

This challenge rotted my brain by 50%. <br>
There are a moment where I said so what's the problem here? <br>
Turns out being 18 causes dementia