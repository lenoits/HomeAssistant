# HomeAssistant -- Tips and Tricks

This is a guide that features thing that I had to solve on the way of becoming proficient in HomeAssistant (HA).

## HOW TO SET UP HomeAssistant ON ARCH LINUX

Initially, I tried to access HA in Firefox via 

```bash
http://homeassistant.local:8123/
```

which proved unsuccessful by prompting this error


> Hmm. We’re having trouble finding that site.
>
> We can’t connect to the server at homeassistant.local.
>
> If you entered the right address, you can:
>
> - Try again later
> - Check your network connection
> - Check that Firefox has permission to access the web (you might be connected but behind a firewall)


According to ChatGPT, "Linux does not come with mDNS support out of the box, which is likely why your system cannot resolve the .local address." Thankfully, ChatGPT provided a possible solution.

First, install and configure Avahi, which provides mDNS support on Linux, by

```bash
sudo pacman -S avahi nss-mdns
```

then edit ```/etc/nsswitch.conf``` by 

```bash
sudo nvim /etc/nsswitch.conf
```

and ensure that ```hosts``` line includes

```bash
hosts: files mdns_minimal [NOTFOUND=return] dns myhostname
```

as the original line looked like this

```bash
hosts: mymachines resolve [!UNAVAIL=return] files myhostname dns
```

I updated it to look like this instead

```bash
hosts: files mdns_minimal [NOTFOUND=return] resolve mymachines myhostname dns
```
Now, simply start and enable the Avahi daemon by

```bash
sudo systemctl start avahi-daemon
sudo systemctl enable avahi-daemon
```

and perhaps (not sure if optional) restart the daemon by

```bash
sudo systemctl restart avahi-daemon
```

and voila: it works if you now go back and enter ```http://homeassistant.local/8123/``` in Firefox!
