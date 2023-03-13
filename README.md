# Wireguard

I think I followed this guide for set up: https://www.digitalocean.com/community/tutorials/how-to-set-up-wireguard-on-ubuntu-20-04

## Generating client keys on the server

```
wg genkey > [name]_private.key
cat [name]_private.key | wg pubkey > [name]_public.key
wg genpsk > [name]_preshared.key
```

Then update the server, config and create a new client peer, use the template.

## Updating the server config

```
sudo wg-quick strip /etc/wireguard/wg0.conf | sudo tee /etc/wireguard/wg0_stripped.conf
sudo wg setconf wg0 /etc/wireguard/wg0_stripped.conf
```
