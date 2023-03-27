# SSH Setup

## Setting up GitHub SSH Access with Existing SSH Keys

Create a new file called `id_rsa` (or whatever you want to call it) and copy your private key to the new file:
```
touch ~/.ssh/id_rsa
```

Change the permissions to be more restrictive:
```
sudo chmod 600 ~/.ssh/id_rsa
```

Start the ssh-agent in the background:
```
eval $(ssh-agent -s)
```

Register the newly created private key with the ssh-agent:
```
ssh-add ~/.ssh/id_rsa
```

## Setting up SSH Access on a Raspberry Pi

Use Raspberry Pi Imager and enable ssh access by default with the `authorized_keys` field populated with the desired `ssh-rsa` public key of your local machine.

### Only Use Public Key Authentication for SSH Access

Modify `/etc/ssh/sshd_config` and change the following:
```diff
- #PubkeyAuthentication yes
+ PubkeyAuthentication yes

- PasswordAuthentication yes
+ PasswordAuthentication no
```

### Rename `pi` User to Your Desired Name

Set password for `root` (temporary)
```
sudo passwd
```

Enable SSH root access (temporary) by modifying `/etc/ssh/sshd_config` with the following changes:
```diff
- #PermitRootLogin prohibit-password
+ PermitRootLogin yes
```

Restart ssh service
```
sudo service ssh restart
```
