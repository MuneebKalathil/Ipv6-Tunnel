# Ipv6-Tunnel
<b>IPv6 tunneling on Windows &amp; Linux Using Hurrican Electric Tunnel Broker</b>

1. First you need to create an account on https://tunnelbroker.net <br>
2. Then, Create a Tunnel point with your WAN IP (Public IP) with a nearest server location to your country.<br>
3. Select Example configuration & Choose Your OS from the drop down list.<br>

<h2> Script for Ubuntu 12.04 or Greater </h2>
<i>
local_ip = Your LAN IP. You can use <i> ifconfig </i> on Terminal<br>
server_ipv4_address = Server IPv4 Address that you revieved from the tunnelbroker.net after creating a tunnel point <br>
client_ipv6_address = Client IPv6 Addres that you revieved from the tunnelbroker.net after creating a tunnel point <br>
server_ipv6_address = Server IPv6 Address that you revieved from the tunnelbroker.net after creating a tunnel point <br
</i>

<b> Replace "...." with your IP Address</b> <br>



modprobe ipv6<br>
ip tunnel add he-ipv6 mode sit remote "server_ipv4_address" local "local_ip" ttl 255<br>
ip link set he-ipv6 up<br>
ip addr add "client_ipv6_address" dev he-ipv6<br>
ip route add ::/0 dev he-ipv6<br>
ip -f inet6 addr<br>


<b> Example </b><br>
modprobe ipv6<br>
ip tunnel add he-ipv6 mode sit remote 216.218.221.6 local 192.168.1.3 ttl 255<br>
ip link set he-ipv6 up<br>
ip addr add 2001:470:18:165::2/64 dev he-ipv6<br>
ip route add ::/0 dev he-ipv6<br>
ip -f inet6 addr<br>
<br>

<b> Run the above the script on cmd as sudo or root user </b> <br>
<b> Allow icmpv6 packets on iptables</b> <br>


ping ipv6.google.com on cmd
If it is success, You will get the reply.


<h2> Script for Windows 7/8/8.1/2008/2012 </h2>
<i>
local_ip = Your LAN IP. You can use <i> ipconfig </i> on cmd (Command Prompt)<br>
server_ipv4_address = Server IPv4 Address that you revieved from the tunnelbroker.net after creating a tunnel point <br>
client_ipv6_address = Client IPv6 Addres that you revieved from the tunnelbroker.net after creating a tunnel point <br>
server_ipv6_address = Server IPv6 Address that you revieved from the tunnelbroker.net after creating a tunnel point <br
</i>

<b> Replace "...." with your IP Address

netsh interface teredo set state disabled <br>
netsh interface ipv6 add v6v4tunnel interface=IP6Tunnel "local_ip" "server_ipv4_address"<br>
netsh interface ipv6 add address IP6Tunnel "client_ipv6_address"<br>
netsh interface ipv6 add route ::/0 IP6Tunnel "server_ipv6_address"<br>

<b> Example </b><br>
netsh interface teredo set state disabled <br>
netsh interface ipv6 add v6v4tunnel interface=IP6Tunnel 192.168.1.3 216.218.221.6<br>
netsh interface ipv6 add address IP6Tunnel 2001:470:18:69::2<br>
netsh interface ipv6 add route ::/0 IP6Tunnel 2001:470:18:69::1<br>
<br>

<b> Run the above the script on cmd as Administrator </b> <br>
<b> Allow icmpv6 packets on firewall</b> <br>
<i> Control Panel -> System Security -> Windows Firewall
Advanced Settings -> Inbound & Outboud Rules <br>
----> File & Printer Sharing (Echo Request - ICMPv6In / ICMPv6Out) -> Right Click -> Enable Rule<br> </i>

ping ipv6.google.com on cmd
If it is success, You will get the reply.


