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
