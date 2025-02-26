# Analyzing DNS Log Files Using Splunk

## Description
 **In this project i'm showcasing my ability to pre-process a DNS Log File data then analyse it, This process involved:**

- Uploading a compressed [DNS log file](https://www.secrepo.com/maccdc2012/dns.log.gz) into Splunk.
- Manually extracting key data fields.
- Using **Splunk Processing Language (SPL)** to automate log parsing.


---

## Key Features
- **DNS Log Analysis**: Extracted and analyzed DNS logs to identify suspicious activity.
- **Field Extraction**: Isolated key fields such as source IP, domain, and query type for deeper analysis.
- **Threat Detection**: Used **SPL (Search Processing Language)** to detect anomalies and potential threats.

---

## Languages and Utilities Used
- **Splunk Enterprise**: For log ingestion, analysis, and visualization.
- **SPL (Search Processing Language)**: For querying and analyzing DNS logs.
- **Windows 11**: The environment used for running Splunk and performing the analysis



<h2>Program walk-through:</h2>

<p align="center">

<br/>
<br/>
<p align="center" >
Uploading DNS Log File<br/>
<img src="https://imgur.com/MtmDif2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/tBWyQLX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/xB0ujk6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/> 
<br/> 
<p align="center">
Extracting Relevant Fields : <br/>
<img src="https://imgur.com/rzufBGR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/nqYNcUu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p align="center"> Using the Delimiter method to directly split fileds with commas...etc  <br/>
<img src="https://imgur.com/sS1GRVl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <p align="center"> Labeling the destination IP  <br/>
<img src="https://imgur.com/1XkZXKD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <p align="center"> Labeling the destination port <br/>
<img src="https://imgur.com/8boF7eH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <p align="center"> Save & Index the Data (Persisting Preprocessed Logs)<br/>
<img src="https://imgur.com/oYvRk5l.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
<br/> 
<p align="center">
retrieving all DNS logs from Splunk through: <br/>
 index=_* OR index=* sourcetype=dns_logs
<img src="https://imgur.com/b4tSzPz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <br/>

 

 
 <p align="center">
identifying which IPs are making the most DNS queries through: 
  <br/> index=_* OR index=* sourcetype=dns_logs | stats count by src_ip <br/>
<img src="https://imgur.com/D6jKPYw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <p align="center">
identifying the most accessed domains in the network (anomaly detection) through:
   <br/>index=_* OR index=* sourcetype=dns_logs | top limit=20 domain_name<br/>
<img src="https://imgur.com/gEiCxwX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
   <p align="center">
Identifying the most active DNS clients / Compromised machines through : 
    <br/>index=_* OR index=* sourcetype=dns_logs | top limit=10 src_ip<br/>
<img src="https://imgur.com/9lo34PV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>   
<br />

</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
