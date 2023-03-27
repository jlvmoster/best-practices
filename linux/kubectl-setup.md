# Best Practices `kubectl` Setup

## Setup `kubectl` for Raspberry Pi

Install gpg keys to the `trusted.gpg.d` directory
```
sudo curl -fsSLo /etc/apt/trusted.gpg.d/kubernetes-archive-keyring.gpg https://packages.cloud.g
oogle.com/apt/doc/apt-key.gpg
```

Add the Kubernetes `apt` repository
```
echo "deb [signed-by=/etc/apt/trusted.gpg.d/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
```
