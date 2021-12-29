# Digital Forensics & Incident Response Lab Setup
used [this video guide](https://youtu.be/zyjwo8z3PtU) to set up a lab for malware analysis

## install SIFT VM
download .ova file from SANS, imported into virtualbox but no luck.  got a free VMWare trial and it works fine (running inside my windows host rather than a linux VM)

## install Remnux VM
download .ova file from SANS, imported into virtualbox, running inside windows host
in virtualbox, change the network adapter type to `host-only adapter` -> `vbox host only ethernet adapter`

## windows VM
created a win 10 VM and copied over sysinternals.  created a base image and then cloned for testing

### route network traffic to remnux/sift
- in virtualbox, change the network adapter type to `host-only adapter` -> `vbox host only ethernet adapter` [same thing done on remnux]
- remnux/sift boxes need to be on the same network as the win vm
- change the DNS to the IP address of the remnux vm
- use inetsim on Remnux
`sudo vim /etc/inetsim/inetsim.conf`
- find bind address in inetsim.conf
	- change to the IP of the remnux host
- find DNS default IP address
	- change to IP of remnux host
- run inetsim `sudo inetsim`
- confirm by running nslookup and seeing the destination IP returned as the IP of remnux vm

copied over:
- regshot.  registry analysis
- WRR.  windows registry recovery
- PEStudio.  for analysing portable executables for indicators
- didier stevens tools, massive pile of scripts and tools

## improvements
- i would rather have set up a VM to act as the host so I could then clone that and have everything else established already

#DFIR #digitalforensics #malwareanalysis #vm #lab
