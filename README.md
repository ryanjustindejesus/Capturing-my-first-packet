<h1>Capturing my first packet</h1>



<h2>Description</h2>
In this lab activity, I captured and analyzed live network traffic using tcpdump. I used Linux commands in the Bash shell to complete these steps.
<br />


<h2>Practical experience gained in this Lab</h2>

- <b>Identifying network interfaces</b> 
- <b>Using the tcpdump command to capture network data for inspection</b>
- <b>Interpreting the informaiton that tcpdump outputs regarding a packet</b> 
- <b>Saving and loading a packet data for later analysis</b> 

<h2>Environments Used </h2>

- <b>Qwiklabs</b> 

<h2>Lab walk-through:</h2>

<h2>Task 1: Identify Network interfaces </h2>
In this task, I identified the network interfaces that can be used to capture network packet data.
 <br/> <br />
(1) First, I used the command "sudo ifconfig" to identify the interfaces that are available. <br/> <br/> 
In this lab, I used eth0 as the interface that I captured the network packet data from in the following tasks. <br/> <br/>
(2) Next, I used the command "sudo tcpdump -D" to identify the interface options available for packet capture. 
<br/> <br/> <p align="center">
<img src="https://imgur.com/Yd1eLNQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<br /> <br />

<h2>Task 2: Inspect the network traffic of a network interface with tcpdump </h2>
In this task, I used tcpdump to filter live network packet traffic on an interface.
<br/> <br />
(1) I used the command "sudo tcpdump -i eth0 -v -c5" filter live network packet data from the eth0 interface with tcpdump. <br /> <br />

- `i eth0`: Capture data specifically from the `eth0` interface.
- `v`: Display detailed packet data.
- `c5`: Capture 5 packets of data.
  
<p align="center">
<img src="https://imgur.com/g3zZN5g.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<br /> <br />

<h2>Task 3: Capture network traffic with tcpdump </h2>
In this task, I used tcpdump to save the captured network data to a packet capture file.
 <br/> <br/>
(1) First, I used the command "sudo tcpdump -i eth0 -nn -c9 port 80 -w capture.pcap &" to capture packet data into a file called capture.pcap. <br/> <br/>
(2) Next, I used the command "curl opensource.google.com" to generate some HTTP (port 80) traffic. It generated some HTTP (TCP port 80) traffic that can be captured. <br/> <br/>
(3) Finally, I used the command "ls -l capture.pcap" to verify that packet data has been captured. <br/> <br/> 

- `i eth0`: Capture data from the `eth0` interface.
- `nn`: Do not attempt to resolve IP addresses or ports to names.This is best practice from a security perspective, as the lookup data may not be valid. It also prevents malicious actors from being alerted to an investigation.
- `c9`: Capture 9 packets of data and then exit.
- `port 80`: Filter only port 80 traffic. This is the default HTTP port.
- `w capture.pcap`: Save the captured data to the named file.
- `&`: This is an instruction to the Bash shell to run the command in the background.

<p align="center">
<img src="https://imgur.com/KeSRsqR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<br /> <br />

<h2>Task 4: Filter the captured packet data </h2>
In this task, I used tcpdump to filter data from the packet capture file you saved previously.
 <br/> <br/> 
(1) I used the command "sudo tcpdump -nn -r capture.pcap -v" to filter the packet header data from the capture.pcap capture file. <br/> <br/>  

- `nn`: Disable port and protocol name lookup.
- `r`: Read capture data from the named file.
- `v`: Display detailed packet data.

<p align="center">
<img src="https://imgur.com/nOnVyfc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<br /> <br />
(2) I used the command "sudo tcpdump -nn -r capture.pcap -X" to filter the extended packet data from the capture.pcap capture file. <br/> <br/>  
  
- `nn`: Disable port and protocol name lookup.
- `r`: Read capture data from the named file.
- `X`: Display the hexadecimal and ASCII output format packet data. Security analysts can analyze hexadecimal and ASCII output to detect patterns or anomalies during malware analysis or forensic analysis.
  
<p align="center">
<img src="https://imgur.com/WQU76oS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
