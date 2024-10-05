# Basic Notes before starting 
### 1. How I accessed my SSH Key
`ssh-agent sh -c 'ssh-add; ssh-add -L'`<br/>
From the above `cmd` line command, I learnt:<br/>
1. `ssh-agent` command is a **key manager** which handles or stores ssh public key and certificates in the memory -- *unencrypted*
2. `ssh-add` allows various cmd line operations like - `-c`,`d` and `D`,etc; In this case `ssh-add -c` causes a confirmation to be asked to the user each time the added identities are used for the authentication.
<br/>
### How I established a server connection

`ssh -i ./key hacker@dojo.pwn.college`
