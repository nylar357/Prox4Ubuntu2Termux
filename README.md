Installed ProxyBroker on main laptop & my google pixel 3a.  Specifically on Termux running Kali Linux.

Installation of ProxyBroker & deps

$ pip install aiohttp
$ pip install aiodns
$ pip install maxminddb
$ pip install -U git+https://github.com/constverum/ProxyBroker.git

The only real difference you'll find running one vs the other (Termux distro vs a true Linux distro) is using pip3

First tings first: off with ProxyBroker finding suitable servers with the find or grab command.  The grab option allows for checking a range of things to see if they'll suit your needs.  The find option checks far less or no traits.  

$ proxybroker grab -l <amount> --types <HTTP,HTTPS,SOCKS4,SOCKS5,CONNECT:25,CONNECT:80> --lvl <anon layer> --strict

$ -l 
maximum #/limit of servers you want returned

$ --types 
Protocol types you want returned
$ |HTTP|HTTPS|SOCKS4|SOCKS5|CONNECT:25|CONNECT:80|

$ --lvl 
The the level of anonymity you require when using HTTP proxies ONLY HTTP.
transparent | requests pass thru unchanged, no anon.
anonymous | proxies append their IP's with YOUR IP.
high | proxies will actively spoof IP, multiple proxy layer passthru.

$ -outfile
Results are written here
$ --format 
specifying the format of your outfile, either <default|json>

Grab Example :
$ proxybroker grab -l 100 --countries US --format json --outfile 100socks.js

Find Example :
$ proxybroker find -l 100 --types SOCKS4 SOCKS5 --lvl anonymous --strict

$ --strick
ProxyBroker to look for exact matches for the type and lvl parameters. The option doesn’t take a value.