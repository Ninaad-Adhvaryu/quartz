I got it working similarly. I did not have to enable https or Magic DNS.

For my situation I was trying to use plexamp.

In Plex, I have remote access set to: "Not available outside your network"

Then under <MyPlexservername>Settings>network

there is a "Custon server access URLs" field

I put my tailscale ip address for my plex server there. "https://<TailscaleIP>:32400"

Example: "[https://123.123.123.123:32400](https://123.123.123.123:32400)"

After that I could connect using plexamp to listen to my music from my phone. Whether on wifi or cell

Here is what the manual says about this field:

Custom server access URLs

A comma-separated list of URLs (either HTTP or HTTPS), which will be published to plex.tv for server discovery. This can be very useful in a few cases: if you’re using a VPN to get back home, if you’re using a reverse proxy in front of the media server, or if your networking configuration is otherwise unique. For instance, if you have your own custom domain with subdomain, you might add:

[https://plex.mycustomdomain.com:32400](https://plex.mycustomdomain.com:32400)

Hope this helps someboby.

similar to what aakoss said, but spelled out exactly what I did.

