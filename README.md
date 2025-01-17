<h1>Palo Alto Remote Access VPN</h1>


<h2>TLDR Description</h2>
Configuring a Remote Access VPN on a Palo Alto Firewall.
<br />

<h2>Purpose</h2>
The purpose of this lab is to configure and access a Remote Access VPN through Palo Alto’s Global Protect on a PC on the outside of the firewall.
<br />

<h2>Background Info</h2>
A remote access vpn (virtual private network) allows for users who are not physically at the location where a network is situated to remotely connect into the network. For example if someone is attempting to work from home and needs access to a file server within the organizations network they would have to utilize a remote access vpn to gain access. It also encrypts the traffic so no malicious actors can intercept the data that might be sensitive for the organization.
<br />

<h2>Lab Summary</h2>
I started this lab out by generating a certificate which contained root authority so I was able to bypass the firewall settings that I configured later on in the lab. After that I configured the local database for the authentication profile, for the firewall to draw from when attempting to access global protect. I then configured global protect portal which in itself created a tunnel interface through the firewall to the users computer which we are trying to connect into. After I configured the global protect client I imported the root certificate into the pc that was on the outside of my firewall, which I then used to identify myself as a valid user to gain access into the remote machine within the firewall.
<br />

<h2>Network Diagram</h2>
<p align="center">
  <img src="https://i.imgur.com/WzgVTWE.png" height="30%" width="30%" alt="Network Diagram"/>
</p>
<br />

<h2>Walk-Through:</h2>

<p align="center">
While booting, enter configuration mode<br/>
<img src="https://i.imgur.com/XRVO4Ow.png" height="80%" width="80%" alt="Palo Alto Firewall Factory Reset Steps"/>
<br />
<br />
Change current configuration to a clean slate<br/>
<img src="https://i.imgur.com/Lk3iENN.png" height="80%" width="80%" alt="Palo Alto Firewall Factory Reset Steps"/>
<br />
<br />
Allow to boot to fresh environment and then implement new configurations<br/>
<img src="https://i.imgur.com/cxzJ5Xr.png" height="80%" width="80%" alt="Palo Alto Firewall Factory Reset Steps"/>
<br />
<br />
</p>

<h2>Problems</h2>
The main issue I had was with my certificates, when I was initially generating the main root certificate that I used to connect into the Global Protect VPN I accidentally did not check the box to give it root authority. It took me a while to finally realize the issue and I found the problem after searching through my entire configuration to see if the certificate was attached in the right places which it was. Once I found that it was not checked as a root certificate, I had to delete the certificate, regenerate it with it configured to be a root certification, and then I replaced it in all of my configs so that it would work.
<br/>
<br/>
The other Issue I encountered was a warning that didn’t necessarily stop me from committing my changes but it did affect the user ID I used to access the VPN.
<p align="center">
<img src="https://i.imgur.com/QCRWXWK.png" height="80%" width="80%" alt="Problem1"/>
</p>
<b>Fix: within the trust-L3 zone enabling the user identification to allow access.</b>
<br/>

<h2>Conclusion</h2>
In this lab I generated certificates to very legitimate user access through the global protect remote access VPN I configured through the Palo Alto 220 firewall. There were a lot of new concepts in this lab that I had to research to find out more information about, I think the biggest concepts that I faced were the certificate creation, use of them, and the configuration of the global protect gateway which was finally configured after extensive research and collaboration with the other members in the lab.
<br />

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
