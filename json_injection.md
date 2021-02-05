Instanzen automatisch nach boot starten. 

Als erstes den Autologin einschalten. 

Nun folgende Datei anlegen:

sudo nano instanzen.json


// Command to start instance 1
{
  "command" : "instance",
  "subcommand" : "startInstance",
  "instance" : 1
}

// Command to stop instance 2
{
  "command" : "instance",
  "subcommand" : "startInstance",
  "instance" : 2
}

// Command to stop instance 3
{
  "command" : "instance",
  "subcommand" : "startInstance",
  "instance" : 3
}

// Command to stop instance 4
{
  "command" : "instance",
  "subcommand" : "startInstance",
  "instance" : 4
}

Nun ein Skript anlegen, dass nach dem Autologin ausgeführt wird. 

sudo nano /etc/Profile.d

#!/bin/bash

sleep 2
sudo /usr/bin/wget --post-file=./instanzen.json --header=Content-Type:application/json localhost:8090/json-rpc & 
