# Manjaro/Arch Linux Ansible Provision

This is an Ansible playbook meant to provision a Manjaro or Antergos Linux distribution,
based on Arch Linux. It should run locally after a clean OS install.

## Preamble

1. Refresh the copy of the master package database from the server and install `Ansible` and `Git`
```
sudo pacman -Syy
sudo pacman -S ansible git --noconfirm
```

2. Git clone the current project
```
git clone git@github.com:JuliusTZM/manjaro-playbook.git
```

## Run

### Install everything
```
ansible-playbook playbook.yml --extra-vars="user_name=USERNAME user_email=EMAIL" --ask-become-pass
```

### Install everything with debug turned on
```
ansible-playbook -vvv playbook.yml --extra-vars="user_name=USERNAME user_email=EMAIL" --ask-become-pass
```

## Playbook Tags

Tags supported:

| Tag       | Description                                                                                                      |
|-----------|------------------------------------------------------------------------------------------------------------------|
| base      | Install Linux util libraries, python-pip, xinput, terminator and zsh                                             |
| printers  | Install printer drivers                                                                                          |
| browsers  | Install Chrome and chromedriver                                                                                  |
| dev-tools | Install jq, docker, docker-compose, nodejs, npm, jre8, jre10, maven, clojure, leiningen, sbt, scala, kubernetes, bluemix-cli and hub  |
| editors   | Install vim, atom, emacs, gimp and Intellij                                                                      |
| media     | Install Spotify and Peek (GIF Screen recorder)                                                                   |                                                                           |
| aur       | Install Arch User Repository libraries                                                                           |

Example on how to install only browsers:
```
ansible-playbook playbook.yml --extra-vars="user_name=USERNAME user_email=EMAIL" --ask-become-pass --tags browsers
```

## TODO

Samba AD client setup:
 * Join to AD Domain based on https://bit.ly/2N1Nqzs
