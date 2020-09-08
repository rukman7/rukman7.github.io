---
layout: post
title: Automating OSX applications using applescript and bash
tags:
  - osx
  - bash
---
#### OSX version
```
BruceWayne:[~] $ sw_vers
ProductName:	Mac OS X
ProductVersion:	10.14.6
BuildVersion:	18G5033
```
#### Automating OSX terminal application
Sample script to start running commands & services in new terminal tabs (databases, ui builds, docker, vagrant etc.,). This sample script will come in handy when it's required to start multiple services and applications for development/debugging or anyother purposes in a single command.

```bash
#!/bin/bash

function new_tab() {
  TAB_NAME=$1
  COMMAND=$2
  osascript \
    -e "tell application \"Terminal\"" \
    -e "tell application \"System Events\" to keystroke \"t\" using {command down}" \
    -e "do script \"printf '\\\e]1;$TAB_NAME\\\a'; $COMMAND\" in front window" \
    -e "end tell" > /dev/null
}

#start up elasticsearch
new_tab "elastic search" "cd ~/system/elasticsearch/bin && ./elasticsearch"

#startup  mongodb
new_tab "mongo db" "mongod"

#start up ui
new_tab "UI" "cd ~/system/ui; npm run dev"

#open mongdb cli for debugging
new_tab "mongo cli" "cd ~/Desktop; sleep 6; mongo"

#plain terminal for running curl commands
new_tab "plain terminal"
```

#### Append an alias to bash_profile to call the script from anywhere

```bash
#let's say the file name is development.sh
echo "alias development=\"sh ~/development.sh"\" >> ~/.bash_profile 
```
Source the ~/.bash_profile using command `source ~/.bash_profile`

#### Note
* When running the script for the first time, the system will prompt & request to allow access for the terminal. Upon granting permissions prompting won't happen next time.

### Links
[dan.doezema.com](http://dan.doezema.com/2013/04/programmatically-create-title-tabs-within-the-mac-os-x-terminal-app/)