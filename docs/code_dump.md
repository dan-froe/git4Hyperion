Instanzen automatisch nach boot starten. 

Als erstes den Autologin einschalten. 

Nun folgende Datei anlegen:



Skript nach Autologin ausgeführt 
sudo nano /etc/Profile.d


#!/bin/bash

sleep 2
sudo /usr/bin/wget --post-file=./instanzen.json --header=Content-Type:application/json localhost:8090/json-rpc & 



wget -O /dev/null --post-data '{"command" : "instance","subcommand" : "startInstance","instance" : 1}' --header=Content-Type:application/json localhost:8090/json-rpc

wget -O /dev/null --post-data '{"command" : "instance","subcommand" : "switchTo","instance" : 1}' --header=Content-Type:application/json localhost:8090/json-rpc

wget -O /dev/null --post-data '{"command":"componentstate","componentstate":{"component":"LEDDEVICE","state":true}}' --header=Content-Type:application/json localhost:8090/json-rpc

curl -X POST -i http://localhost:8090/json-rpc --data '{"command": "serverinfo", "tan":1}'

curl -i -X POST 'http://localhost:8090/json-rpc' --data '{"command" : "instance","subcommand" : "switchTo","instance" : 1}' --next 'http://localhost:8090/json-rpc' --data '{"command":"componentstate","componentstate":{"component":"LEDDEVICE","state":false}}'

curl -i -X POST 'http://localhost:8090/json-rpc' --data '{"command":"effect","effect":{"name":"Rainbow swirl"},"duration":5000,"priority":50,"origin":"My Fancy App"}'

Aus:

sudo hyperion-remote -c black
sudo hyperion-remote -I NameInstanz -c black
exit

An:

sudo hyperion-remote --clearall
sudo hyperion-remote -I NameInstanz --clearall
exit


ls -l1va

netstat -npl | grep
netstat -anp | grep
ps aux | grep
ps - eaf | grep
jobs -l
kill %1

ping -c 1 loccalhost > >(tee -a ok) 2> >(tee -a ok)

nmap -p 80 example.com

raspi-gpio set 20 dl 

Kernel module lsmod

curl https://api.github.com/repos/hyperion-project/hyperion.ng/releases 2>&1 | grep "browser_download_url.*Hyperion-.*armv7l.deb" | head -n1 | cut -d ":" -f 2,3 | tr -d \"  | wget -i -

curl -s https://api.github.com/repos/Hyperion-Project/Hyperion.ng

Interactive Script

bash <(wget -qO- http://website.com/my-script.sh)

Interactive Script root

sudo su -c "bash <(wget -qO- http://website.com/my-script.sh)" root

printf %"$COLUMNS"s |tr " " "-"

find $HOME -name "hyperiond" | grep /build/bin/hyperiond | sed 's/\/build\/bin\/hyperiond//g' && test $(find $HOME -name HyperionConfig.h.in)

wget -O - https://raw.githubusercontent.com/dan-froe/BASH/overhaul/hyperion_auto/installation.sh | bash

bash <(wget -qO - https://raw.githubusercontent.com/dan-froe/BASH/master/script_maker/script_maker_hyper.sh) 

# cut from file
cat mycron | sed -i s/.*instance.sh.*// mycron

# Websocket to file
echo "{"lv":true}" | websocat ws://wled/ws -n --text writefile:ok &
