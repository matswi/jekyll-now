---
id: 412
title: Azure VPN with Vyatta
date: 2014-04-29T14:35:25+00:00
author: mats
layout: post
guid: http://www.opsmode.com/?p=412
permalink: /2014/04/azure-vpn-with-vyatta/
categories:
  - Azure
  - Hyper-V
tags:
  - Azure
  - Hyper-V
  - vyatta
---
**Setting up a router for Hyper-V**

<span class="hps">Worth mentioning is</span> <span class="hps">that this only works</span> <span class="hps">with a Static Gateway in Azure!</span>

With the help from this post <a title="Using a virtual router for your lab and test environment" href="http://www.deploymentresearch.com/Research/tabid/62/EntryId/81/Using-a-virtual-router-for-your-lab-and-test-environment.aspx" target="_blank">Using a virtual router for your lab and test environment</a> from Johan Arwidmark, and this post <a title="Vyatta Virtual Router on Hyper-V" href="http://blogs.technet.com/b/stefan_stranger/archive/2008/08/25/vyatta-virtual-router-on-hyper-v.aspx" target="_blank">Vyatta Virtual Router on Hyper-V</a> from Stefan Stranger I managed to set up a virtual machine with Vyatta to act as a router for my lab enviroment.

**Connect lab enviroment to Azure VPN**
  
I created virtual networks and a Gateway in my Azure subscription with the help of this guide <a title="Step-By-Step: Create a Site-to-Site VPN between your network and Azure" href="http://blogs.technet.com/b/canitpro/archive/2013/10/09/step-by-step-create-a-site-to-site-vpn-between-your-network-and-azure.aspx" target="_blank">Step-By-Step: Create a Site-to-Site VPN between your network and Azure</a>
  
And with a couple of blog posts on Vyatta, ipsec, Azure VPN and some &#8220;trial and error&#8221; I came up with the following Vyatta config:
  
`<br />
# Configure IKE group<br />
set vpn ipsec ike-group IKE-POLICY lifetime '28800'<br />
set vpn ipsec ike-group IKE-POLICY proposal 1 encryption 'aes128'<br />
set vpn ipsec ike-group IKE-POLICY proposal 1 hash 'sha1'<br />
set vpn ipsec ike-group IKE-POLICY proposal 1 dh-group '2'`

`# Configure ESP group<br />
set vpn ipsec esp-group ESP-POLICY lifetime '3600'<br />
set vpn ipsec esp-group ESP-POLICY pfs disable<br />
set vpn ipsec esp-group ESP-POLICY proposal 1 encryption 'aes128'<br />
set vpn ipsec esp-group ESP-POLICY proposal 1 hash 'sha1'`

`# Enable VPN on the nic<br />
set vpn ipsec ipsec-interfaces interface 'eth0'`

`# Set up the connction to the Azure gateway<br />
set vpn ipsec site-to-site peer [IP of the Gateway] authentication mode 'pre-shared-secret'<br />
set vpn ipsec site-to-site peer [IP of the Gateway] authentication pre-shared-secret '[your pre-shared-secret]'<br />
set vpn ipsec site-to-site peer [IP of the Gateway] connection-type respond<br />
set vpn ipsec site-to-site peer [IP of the Gateway] default-esp-group 'ESP-POLICY'<br />
set vpn ipsec site-to-site peer [IP of the Gateway] ike-group 'IKE-POLICY'<br />
set vpn ipsec site-to-site peer [IP of the Gateway] local-address '192.168.0.254' # Vyatta external ip<br />
set vpn ipsec site-to-site peer [IP of the Gateway] tunnel 1 local prefix '192.168.78.0/24' # Lab enviroment subnet<br />
set vpn ipsec site-to-site peer [IP of the Gateway] tunnel 1 remote prefix '10.10.0.0/22' # Azure subnet`

`commit`

`save`

`# Exclude the site-to-site VPN from NAT<br />
set nat source rule 5 destination address '10.10.0.0/22'<br />
set nat source rule 5 source address '192.168.78.0/24'<br />
set nat source rule 5 outbound-interface 'eth0'<br />
set nat source rule 5 'exclude'`

`set nat source rule 20 source address '10.10.0.0/22'<br />
set nat source rule 20 destination address '192.168.78.0/24'<br />
set nat source rule 20 outbound-interface 'eth0'<br />
set nat source rule 20 'exclude'`

`commit`

`save`

Used blog posts:
  
<a title="Windows Azure mit VPN (Vyatta) verbinden" href="http://blog.protechnology.de/index.php/2013/01/windows-azure-mit-vpn-vyatta-verbinden/" target="_blank">Windows Azure mit VPN (Vyatta) verbinden</a>
  
<a title="Configure a Site-to-site VPN using the Vyatta Network Appliance" href="http://www.rackspace.com/knowledge_center/article/configure-a-site-to-site-vpn-using-the-vyatta-network-appliance" target="_blank">Configure a Site-to-site VPN using the Vyatta Network Appliance</a>
  
<a title="Troubleshooting a Vyatta Site-to-site VPN connection" href="http://www.rackspace.com/knowledge_center/article/troubleshooting-a-vyatta-site-to-site-vpn-connection" target="_blank">Troubleshooting a Vyatta Site-to-site VPN connection</a>