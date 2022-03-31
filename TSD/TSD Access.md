# TSD Access
#norment 
Revisiting [[15.12.21]] meeting with Oleksandr

[TSD FAQ - NORMENT WIKI](https://wiki.norment.uiocloud.no/dokuwiki/tsd-faq?s%5B%5D=tsd)
[[TSD FAQ - local copy]]

## How to access TSD
Go to selfservice.tsd.usit.no
Use the HTML access method for now, but you can use the client portal later
- [[how_to_access_tsd_p33.pdf]]
- once inside tsd, login to win machine
- and then use PUTTY to ssh into the system

## Accessing through VMWARE HORIZON
- Use username p33-michaejt
	- or presumably p697- michaejt for the other project
- Log in with Gauth code
- Log in using regular password

## Accessing App node
On windows I was able to use PUTTY to access hostname `p33-appn-norment01` or `p697-appn-norment01` but not sure what to do from here

Not getting any response from slurm

Maybe see what commands are available

## Import and Export data
https://wiki.norment.uiocloud.no/dokuwiki/tsd_import_export
Import and export data using the web portal: https://data.tsd.usit.no
Check the durable data storage in the TSD VMs
### **Locations:**
**Import:**
	Win: `N:\durable\file-import`
	Shell: `/tsd/data/durable/file-import`
Export:
	Win: `N:\durable\file-export`
	Shell: `/tsd/data/durable/file-export`

### TSD IMPORT API ![[TSD Import API]]


TSD  - [https://www.uio.no/english/services/it/research/sensitive-data/help/](https://www.uio.no/english/services/it/research/sensitive-data/help/)

[https://data.tsd.usit.no/](https://data.tsd.usit.no/) - date import & export web portal (no need to VPN)