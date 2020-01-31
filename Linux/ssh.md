To connect using a private key file, use the following command
```bash
$ ssh -i privatekeyfile <username>@<address>
```

----
To use ssh as proxy, connect to the ssh server using the following command
```bash
$ ssh -D <proxyport> <username>@<address>
```
After connecting, change the proxy settings in your computer to use a SOCKS proxy with `localhost` as the server and `<proxyport>` as the port.

----
To connect easily using keys and without entering any passwords follow the following steps:

1. Generate a pair of private and public keys on the client machine.
```bash
$ ssh-keygen -t rsa -b 4096
```
2. Add the generated public key to `~/.ssh/authorized_keys` file.
3. Add the following to `~/.ssh/config` on the client machine.
```
Host <hostname>
  Hostname <server address>
  User <username>
  IdentityFile ~/.ssh/<private key file>
  IdentitiesOnly yes
  ForwardAgent yes
  AddKeysToAgent
```
I don't know what the three last options are.

----

## SSH Port Forwarding

You can use the following syntax to forward a remote port to a local port (e.g. for accessing Jupyter Notebook instance running on the remote server):

```bash
$ ssh -L <remote_port>:localhost:<local_port> <remote server>
```

[Source](https://michaelgoerz.net/notes/accessing-a-jupyter-notebook-server-through-reverse-port-forwarding.html)
