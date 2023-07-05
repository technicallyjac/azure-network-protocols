<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (22H2)
- Ubuntu Server 20.04


  <br/>

<h2> Inspecting Traffic: High-Level Steps</h2>

- Step 1 Download Wireshark in VM1 running Windows 10.
- Step 2 Ping VM2 running Linux. 
- Step 3 Filter and inspect traffic
  

<h2>Actions and Observations</h2>
<p>
<img width="956" alt="Screenshot 2023-07-04 at 11 51 12 PM" src="https://github.com/technicallyjac/azure-network-protocols/assets/138219436/ffcc5504-0b14-44b3-a5d4-9c169da08678">
</p>
<p>
Download, install and run Wireshark on VM1 running Windows 10. 
</p>
<br />
<p>
<img width="857" alt="Screenshot 2023-07-04 at 11 56 27 PM" src="https://github.com/technicallyjac/azure-network-protocols/assets/138219436/f677fc63-9f98-4fd7-a431-f02f8c92b2f9">
<img width="857" alt="Screenshot 2023-07-05 at 12 00 22 AM" src="https://github.com/technicallyjac/azure-network-protocols/assets/138219436/c995bb90-3b9a-47e6-b02a-be08bcf916c4">

</p>
<p>
Open Powershell and ping VM2's private IP address. 
</p>
<br />

<p>
<img width="1142" alt="Screenshot 2023-07-05 at 12 02 34 AM" src="https://github.com/technicallyjac/azure-network-protocols/assets/138219436/493f4aa0-4b44-4946-878d-bfab130aed8a">

</p>
<p>
Filter for "icmp" in Wireshark and inspect traffic between VM1 and VM2. 
</p>
<br />

<h2>NSG: High-Level Steps</h2>

- Step 1 Add Inbound Security Rules for VM2. 
- Step 2 Ping VM2 running Linux.
- Step 3 Inspect traffic.

<h2>Actions and Observations</h2>

<p>
<img width="1269" alt="Screenshot 2023-07-05 at 12 15 33 AM" src="https://github.com/technicallyjac/azure-network-protocols/assets/138219436/c7040a69-dae3-444d-8ed7-3daea2484738">
</p>
<p>
In MS Azure navigate to Network Secruity Groups and select VM2. 
</p>
<br />

<p>
<img width="1352" alt="Screenshot 2023-07-05 at 12 24 25 AM" src="https://github.com/technicallyjac/azure-network-protocols/assets/138219436/ae422481-9473-4629-aa05-510064f65729">
</p>
<p>
Select Inbound Security Rules from side panel. Add and update rule to deny any icmp traffic and update priority. 
</p>
<br />

<p>
<img width="1137" alt="Screenshot 2023-07-05 at 12 31 36 AM" src="https://github.com/technicallyjac/azure-network-protocols/assets/138219436/6d75e7f9-0f59-43a2-989e-0904a8972420">
</p>
<p>
Return to VM1 running Windows 10 and ping VM2's private network again. The ping should return a "Request Timed Out" status, indicatinng the secruity rule was added successfully. 
</p>
<br />
