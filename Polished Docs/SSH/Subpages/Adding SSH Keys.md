---
# Adding SSH Keys

```table-of-contents
```
## Generate SSH key on your PC
```bash
ssh-keygen
```
Should generate
```text
SHA256: ******************************************* {Username}@{PCName}
```
## Copy public key to Linux
[[File Transfering]]
## Create a folder to store the public key (**in the Server Machine**)
```bash
mkdir -p ~/.ssh
```

### Create a file and save the copied key in it
```bash
nano ~/.ssh/authorized_keys
```
### Set the correct access modifiers

```bash
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```

## Removing Password Authentication

- Navigate to
```bash
cd /etc/ssh
```

- Edit `sshd_config`

```bash
PasswordAuthentication no #To disable password authentication
PubkeyAuthentication yes 
AuthorizedKeysFile .ssh/authorized_keys
```

## Restricting To LAN

- Navigate to router management software
- Make sure there’s no port forwarding to the server machine in the SSH port (22).
