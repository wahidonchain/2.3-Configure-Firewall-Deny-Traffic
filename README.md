<p align="center">
<img src="https://imgur.com/wYucC7L.png" alt="Microsoft Azure"/>
</p>

<h1>Microsoft Azure Compute and Networking 🪟 - Configure a Firewall (Deny Inbound ICMP Traffic)</h1>
In this section I go through the process of observing continuous ICMP traffic from our Ubuntu Linux VM to our Windows 10 VM. I then manually change inbound security rules (firewall) to block requests reaching the Linux VM, reverse this security rule and once again observe the flow of traffic between the two virtual machines. <br /> (Link Back to Main Project Contents Page is at the Bottom of this Repo)

<h2>Environments and Technologies Used</h2>

- Lenovo Ideapad 5 Pro 16gb AMD Ryzen 7
- Microsoft Azure Resource Group (from [Part 1 - Setting Up Virtual Machines](https://github.com/wahidonchain/2.1-Virtual-Machine-Setup))
- Microsoft Azure Windows 10 Pro version 22H2 - x64 Gen2 Virtual Machine (from [Part 1 - Setting Up Virtual Machines](https://github.com/wahidonchain/2.1-Virtual-Machine-Setup))
- Microsoft Azure Ubuntu Pro 24.04 LTS - x64 Gen2 Virtual Machine (from [Part 1 - Setting Up Virtual Machines](https://github.com/wahidonchain/2.1-Virtual-Machine-Setup))
- Wireshark Network Protocol Analyzer Software
- Windows Powershell

<h2>Operating Systems Used </h2>

- Local Windows 11 Home Version 21H2</b>
- Windows 10 Pro version 22H2 Virtual Machine
- Ubuntu Pro 24.04 LTS - x64 Gen2 Virtual Machine

<h2>List of Prerequisites</h2>

- Microsoft Azure Subscription
- Microsoft Azure Subscription Credit
- Wireshark Installed on Windows 10 Virtual Machine

<h2>Installation, Setup, Resource Setup, Executing Functions</h2>

1. Using the command ping -t 10.0.0.6 I initiated a continuous ping request from the Windows VM to the Linux VM, while filtering for only ICMP traffic.
<p>
<img src="https://imgur.com/yKpVYkA.png" alt="Continuous ping from Windows VM to Linux VM, filtered for ICMP in Wireshark"/>
</p>
<p>
2. Within Azure, I then set a rule to disable inbound ICMP traffic to the Linux VM via the Network Security Group. Priority Value 290, Protocol ICMP, Name "DenyAnyCustomAnyInbound".
</p>
<br />

<p>
<img src="https://imgur.com/Ll6lOYE.png" alt="Creating a deny rule for inbound ICMP in the Azure Network Security Group"/>
</p>
<p>
3. Below we can see, after creating a rule to deny inbound ICMP traffic, the Windows VM is no longer receiving replies from the Linux VM. Requests are timing out.
</p>
<br />

<p>
<img src="https://imgur.com/yJWJz7L.png" alt="Ping requests timing out after the deny rule is applied"/>
</p>
<p>
4. I then went back into the Network Security Group of the Linux VM within Azure, and deleted the rule denying ICMP traffic to the Linux VM.
</p>
<br />

<p>
<img src="https://imgur.com/10GeN5v.png" alt="Deleting the ICMP deny rule from the Network Security Group"/>
</p>
<p>
5. Now we can see the traffic has resumed and the two Virtual Machines are now speaking to each other.
</p>
<br />

<p>
<img src="https://imgur.com/LLnCKlK.png" alt="ICMP replies resuming once the deny rule is removed"/>
</p>
<p>
LINK BACK TO THE MAIN PROJECT CONTENTS PAGE - https://github.com/wahidonchain/Azure-Compute-and-Networking
