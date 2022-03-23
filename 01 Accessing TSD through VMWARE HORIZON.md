# Accessing TSD through VMWARE HORIZON
[TSD FAQ - NORMENT WIKI](https://wiki.norment.uiocloud.no/dokuwiki/tsd-faq?s%5B%5D=tsd)
[[TSD FAQ - local copy]]

Follow this guide however in our case use p697 instead of p33 [[how_to_access_tsd_p33.pdf]]

## In summary
- Go to selfservice.tsd.usit.no
	- Apply for membership for each project you are on
		- In my case I had to apply for membership in both p33 and p697
	- Once you are given access then use VMware (found on same site), preferably using the client, to access the list VM up nodes
- Log into VMware using the project username, e.g.  p697-michaejt
	- or presumably p697- michaejt for the other project
- Log in with Gauth code
- Log in using regular password
- once inside VMware, log in machine of preference
- Once inside use terminal (redhat) or PUTTY (win) to ssh into the cluster

## SSH-ing to the AppNode
Once you are inside the VM as picked through VMware, you still need to connect to the *appnode* (AppNode, app-node, app node, whichever you like best). 

Currently you are on the *login node* where you can do some things but in order to interact with the cluster you will need to *ssh* into it.

Directions for accessing the p33 cluster is [on the wiki here](???), but essentially they are the same. Open a terminal and type in:
`ssh p697-michaejt@p697-appn-norment01
and then your normal password

### Direction for using putty (win)
**Add details later.** 
Putty is basically a ssh terminal for windows. 
Open PUTTY and add the above details then save the config.


## Should I use redhat or windows?
Both honestly. 
**But for those unfamiliar** with linux environments start with Windows.

You need to use a terminal to interact with the TSD and it is easiest to interact with a terminal from a linux environment. On windows you sometimes even encounter problems using PUTTY which you would not on a regular linux terminal. However, redhat is not as user friendly in other aspects.

Windows, offers more user friendly options for text editing (like vs-code) and file navigation.

**For more advanced users:** Because you can run two VMware instances simultaneously, I suggest using a redhat window to run terminals (especially if you are using multiple terminals at once) and a Windows window (I hate this) to access VS-code and Windows file explorer.

**Advanced users**, are not reading this and are already in using redhat for vim and emacs. The psychos.


## Difference between the *login node* and the *appnode*
The login node is the “virtual computer” that VMware connects you to.
The appnode is the computer you connect to through the login node, so that you can access the cluster.


## Copying and pasting in the VMware session
You can paste into the TSD, ***but you can’t paste out.***
In order to work around this you may take screenshots of something you want to save to your local computer (or share with a coworker).
Or, you can use an OCR program such as ShareX (win) or Crow Translate (linux) to copy text from a screenshot.

