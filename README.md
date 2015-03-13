# Ipv6-Tunnel
IPv6 tunneling on Windows &amp; Linux Using Hurrican Electric Tunnel Broker

<h2> Script for Windows 7/8/8.1/2008/2012 </h2>

netsh interface teredo set state disabled <br>
netsh interface ipv6 add v6v4tunnel interface=IP6Tunnel "local_ip" "server_ipv4_address"<br>
netsh interface ipv6 add address IP6Tunnel "client_ipv6_address"<br>
netsh interface ipv6 add route ::/0 IP6Tunnel "server_ipv6_address"<br>

<i>
local_ip = Your LAN IP. You can use <i> ipconfig </i> on cmd (Command Prompt)<br>
server_ipv4_address = Server IPv4 Address that you revieved from the tunnelbroker.net after creating a tunnel point <br>
client_ipv6_address = Client IPv6 Addres that you revieved from the tunnelbroker.net after creating a tunnel point <br>
server_ipv6_address = Server IPv6 Address that you revieved from the tunnelbroker.net after creating a tunnel point <br
</i>

<b> Example </b><br>
netsh interface teredo set state disabled <br>
netsh interface ipv6 add v6v4tunnel interface=IP6Tunnel 192.168.1.3 216.218.221.6<br>
netsh interface ipv6 add address IP6Tunnel 2001:470:18:69::2<br>
netsh interface ipv6 add route ::/0 IP6Tunnel 2001:470:18:69::1<br>




