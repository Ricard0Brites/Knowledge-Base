---
# Connecting to SSH Server

## With Username and Password
```bash
ssh {Username}{SSH Server IP} -p {Port}
```

## With Keys
```bash
ssh -i {Private Key File Path} {Username}{SSH Server IP} -p {Port}
```



## Example
```bash 

# with username and password 
ssh -p 8022 username@192.168.1.4 
# With Keys 
ssh -i "E:\SSH_Keys\A2_Lite\SSH_Key" u0_a156@192.168.1.4 -p 8022 ssh -i

```