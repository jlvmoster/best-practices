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
