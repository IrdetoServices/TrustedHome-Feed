# Trusted Home Feed
This feed adds Irdeto Trusted-Home Unum agent to OpenWrt builds.


Overview    
Add this feed to an OpenWrt build's `feeds.conf.default` file:

```
# Trusted-Home feed
src-git trustedhome https://github.com/IrdetoServices/TrustedHome-Feed.git
```
Update the local copy of the Trusted-Home feed with the OpenWrt `feeds` script:

```
./scripts/feeds update trustedhome
./scripts/feeds install -a
```

(The `./scripts/feeds install trustedhome` cannot work and it will show this warning message:
`
WARNING: No feed for package 'trustedhome' found
`, since this feed provides no underlying source URL, so please use `./scripts/feeds install -a` instead.)

Enable the Unum agent in `make menuconfig` under *Network*.

Build an Unum agent ipk with `make package/unum/compile`, then use `scp` to copy the ipk onto your router and use `opkg install` to install it.
