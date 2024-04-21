# All About Timing

**Challenge Type: Crypto**  

## Challenge

I'm always late for class but my prof told me that time is relative
<br>
Author: jloh02
<br>
[File](dist-All-About-Timing)
<br>
```nc challs.nusgreyhats.org 31111```

## Solution 

1) Let's open the file to discover a time.py
```
import time
import random

random.seed(int(time.time()))
print(time.time())

print("Guess the number I'm thinking of? It's all about the timing")
x = input("Your guess:")

n = random.randint(1000000000000000, 10000000000000000-1)

if int(x) == n:
    with open("flag.txt") as f:
        print(f.readline())
else: 
    print(f"Wrong answer! The number I was thinking of was {n}\nRemember it's all about the timing!")
```
> Very simply the code is taking the current time as the seed for the random function. And we need to guess the number in the remote server. 
2) Of course we can't stop time nor can we force the server to change the timing settings. So we just have to be ahead of time!
3) Replace the time.time() with a future timing (something like a minute into the future) and run it locally
4) It will print out the future timing's number
5) Now run the remote connection in that future timing and key in the future timing's number
6) Flag: grey{t1m3_i5_a_s0c1al_coNstRucT}

### P.S 

I was begging for God to let me stop time. <br>
Then I realize because time moves forward, <br>
If I run it in future time, my local answer will clash eventually <br>