 HONEYPOT-PENTBOX
[Install PentBox + Honeypot and Simulate an Attack on Port 23, 22 and 80 from Kali Linux](https://www.youtube.com/watch?v=Km7OZKjTveA&utm_source=chatgpt.com)

Here's a refined and human-friendly summary of how to build a honeypot using PentBox on Kali Linux, broken down into clear, detailed steps:



 1.  Prepare Your Environment

Ensure your Kali system is up to date:

  
  sudo apt update && sudo apt upgrade -y
  


 2.  Install PentBox

1. Clone the repository:

   git clone https://github.com/technicaldada/pentbox.git
   cd pentbox
   
2. Unpack the archive:

   tar -zxvf pentbox.tar.gz
   cd pentbox-1.8
   
3. Run PentBox:
   sudo ./pentbox.rb


 3.  Configure the Honeypot

Once PentBox launches, you'll follow menu options:

Main Menu  type 2 for Network Tools
  Network Tools  type 3 for Honeypot ([medium.com][3], [linkedin.com][4])

You’ll then have two configuration modes:

 A. Fast Auto-Configuration

 Choose 1
 Honeypot will automatically start on port 80 (HTTP)
 You’ll see confirmation:
  HONEYPOT ACTIVATED ON PORT 80` ([steemit.com][5], [medium.com][3], [medium.com][1])

 B. Manual Configuration

 Choose 2
 Input:

  Port number (e.g., `23` for Telnet, `22` for SSH, `80` for HTTP)
    Custom warning message, e.g.:
    "You are not allowed to remotely access my system!"
    Log prefix — press Enter to accept default: `/pentbox/other/log_honeypot.txt`
    Optionally enable **beep alerts**
 Once done:
  HONEYPOT ACTIVATED ON PORT [your port] ([medium.com][3], [github.com][2])



4.  Test & Validate

1. From another system (e.g., Windows VM or another Kali VM), attempt to access:

    HTTP: `http://<honeypot_ip>`
    Telnet: `telnet <honeypot_ip> 23`
2. Watch the pentbox terminal—expect a message like:
   `INTRUSION ATTEMPT DETECTED from <attacker_ip>:<port>` ([github.com][2], [medium.com][3])
3. The attacker sees a denial page or custom warning message.



 5.  Monitor the Logs

 Access the log file:

  
  cat /pentbox/other/log_honeypot.txt
  
 Logs include timestamps, attacker IP, port, protocol, and attack details. ([medium.com][3], [github.com][2])



 6. Extend & Improve

Deploy multiple honeypots: run separate instances for ports 21 (FTP), 22 (SSH), 23 (Telnet), 443 (HTTPS), etc. ([eaglepubs.erau.edu][6])
Customize further:

Unique warning messages per port
   Enable audible beeps or syslog integration
   Integrate alerts: forward logs to SIEM or set up email/SMS alerts.
Isolate: deploy honeypot on a dedicated VM or network segment to prevent it from being used as a pivot point. ([eaglepubs.erau.edu][6], [medium.com][3], [github.com][2], [reddit.com][7])

