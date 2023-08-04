# wake on lan systemd

This is a really simple systemd service to enable wake-on-lan on your NIC after
every boot. You may need to edit `enablewakeonlan` to point to your correct
NIC, for me it is `eno1`.

To install, ensure [`ethtool`](https://linux.die.net/man/8/ethtool) is available and:

```
$ chmod +x enablewakeonlan
$ sudo su
# cp enablewakeonlan /usr/local/bin/enablewakeonlan
# cp WakeOnLan.service /etc/systemd/system
# systemctl enable WakeOnLan.service
```

You can verify this has worked after a boot:

```
$ sudo ethtool eno1 | grep Wake-on
```

and looking for: `Wake-on: g`.
