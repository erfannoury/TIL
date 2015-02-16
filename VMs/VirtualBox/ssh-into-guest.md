#SSH into VirtualBox guest OS
SSH-ing into guest OS inside VirtualBox isn't as straight-forward as it is in VMware. I used NAT for networking between the host and guest OS. In VMware I could simply then find the IP address in the guest OS and SSH into that IP address. But in VirtualBox, you can't simply do that.

To SSH into guest OS in VirtualBox, you have to configure Port Forwarding.

* Turn of the guest OS.
* Go to _Network_ tab of VM settings.
* Make sure first network adapter is set to NAT. There you will find the _Port Forwarding_ section (actually a button to a new page).
* Set Host IP address to an address which you have access to, e.g. localhost (`127.0.0.1`)
* Make sure that guest IP address is the same as the IP address you get inside the guest OS (use `ifconfig` or on debian, if you don't have root acess, use `ap addr show [scope local]`)
* You will use the IP address of the host OS and its port number for subsequent steps.
* Make sure that ssh-server is running in the guest OS and the user you are trying to login with has SSH login access (e.g. for root access over SSH, you should set `PermitRootLogin` to `yes` in `/etc/ssh/sshd_config`; then restart the ssh server using `$/etc/init.d/ssh restart` (_on Debian_))
* You can now successfully ssh into the guest OS using `$ssh -p <port number> <user name>@<ip address>`

And you are set to go.
