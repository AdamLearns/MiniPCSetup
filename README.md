# MiniPCSetup

This contains some setup scripts for the mini PC that I have.

## Initial setup

I actually do the initial setup via [Ansible in the Abbott repo](https://github.com/AdamLearns/Abbott/tree/180e74617fe6146886ed22af8d5836f8b8889de6/ansible). That provides the following:

- A bunch of command-line tools like `btop`, `git`, `rg`, etc.
- Docker

## Syncthing

- Create the notes directory: `mkdir ~/Obsidian\ Vaults`
- Run Syncthing in Docker: `docker compose -f syncthing-compose.yml up`
- If you want to connect to the web GUI using the computer that you're SSH-ing _from_, tunnel the Syncthing GUI port: `ssh -L 7895:localhost:8384 adam@minipc`. Note that this can be in `~/.ssh/config` as the following:

```
Host minipc
  HostName 192.168.0.212
  User adam
  AddKeysToAgent yes
  UseKeychain yes
  LocalForward 7895 127.0.0.1:8384
  IdentityFile ~/.ssh/github_adamlearns
```
