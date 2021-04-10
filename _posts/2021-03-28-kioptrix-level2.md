# Kioptrix Level 2

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

