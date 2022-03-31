open the auth keys file in the .ssh directory in root
￼michealt@comorment:~/.ssh$ nano authorized_keys￼
add my public key to an open lineOn this page:

-   [Before you begin](https://kb.iu.edu/d/aews#before)
-   [Set up public key authentication using SSH on a Linux or macOS computer](https://kb.iu.edu/d/aews#linux)
-   [Set up public key authentication using PuTTY on a Windows 11, Windows 10, or Windows 8.x computer](https://kb.iu.edu/d/aews#putty)

---

## Before you begin

Using [SSH](https://kb.iu.edu/d/aelc) public key [authentication](https://kb.iu.edu/d/alqk) to connect to a remote system is a robust, more secure alternative to logging in with an account password or [passphrase](https://kb.iu.edu/d/acpu). SSH public key authentication relies on asymmetric cryptographic algorithms that generate a pair of separate keys (a key pair), one "private" and the other "public". You keep the private key a secret and store it on the computer you use to connect to the remote system. Conceivably, you can share the public key with anyone without compromising the private key; you store it on the remote system in a `.ssh/authorized_keys` directory.

To use SSH public key authentication:

-   The remote system must have a version of SSH installed. The information in this document assumes the remote system uses OpenSSH. If the remote system is using a different version of SSH (for example, [Tectia SSH](https://www.ssh.com/products/tectia-ssh/) ), the process outlined below may not be correct.
-   The computer you use to connect to the remote server must have a version of SSH installed. This document includes instructions for generating a key pair with command-line SSH on a Linux or macOS computer, and with PuTTY on a Windows computer.
-   You need to be able to transfer your public key to the remote system. Therefore, you must either be able to log into the remote system with an established account username and password/passphrase, or have an administrator on the remote system add the public key to the `~/.ssh/authorized_keys` file in your account.
-   Two-factor authentication using [Two-Step Login (Duo)](https://kb.iu.edu/d/beum) is required for access to the login nodes on IU [research supercomputers](https://kb.iu.edu/d/alde), and for SCP and SFTP file transfers to those systems. SSH public key authentication remains an option for researchers who submit the ["SSH public key authentication to HPS systems" agreement ](https://hpceverywhere.iu.edu/agree#/agree) (log into [HPC everywhere](https://kb.iu.edu/d/aquv) using your [IU username and passphrase](https://kb.iu.edu/d/beml)), in which you agree to set a passphrase on your private key when you generate your key pair. If you have questions about how two-factor authentication may impact your workflows, [contact the UITS Research Applications and Deep Learning team](https://mailform.kb.iu.edu/email.php?cid=1449) . For help, see [Get started with Two-Step Login (Duo) at IU](https://kb.iu.edu/d/bfgm) and [Help for Two-Step Login (Duo)](https://kb.iu.edu/d/aluu).

## Set up public key authentication using SSH on a Linux or macOS computer

To set up public key authentication using SSH on a Linux or macOS computer:

1.  Log into the computer you'll use to access the remote host, and then use command-line SSH to generate a key pair using the RSA algorithm.
    
    To generate RSA keys, on the command line, enter:
    
    ssh-keygen -t rsa
    
2.  You will be prompted to supply a filename (for saving the key pair) and a password (for protecting your private key):
    
    -   **Filename:** To accept the default filename (and location) for your key pair, press `Enter` or `Return` without entering a filename.
        
        Alternatively, you can enter a filename (for example, `my_ssh_key`) at the prompt, and then press `Enter` or `Return`. However, many remote hosts are configured to accept private keys with the default filename and path (`~/.ssh/id_rsa` for RSA keys) by default. Consequently, to authenticate with a private key that has a different filename, or one that is not stored in the default location, you must explicitly invoke it either on the SSH command line or in an SSH client configuration file (`~/.ssh/config`); see [below](https://kb.iu.edu/d/aews#id) for instructions.
        
    -   **Password:** Enter a password that contains at least five characters, and then press `Enter` or `Return`. If you press `Enter` or `Return` without entering a password, your private key will be generated without password-protection.
        
        **Important:**
        
        If you don't password-protect your private key, anyone with access to your computer conceivably can SSH (without being prompted for a password) to your account on any remote system that has the corresponding public key.
        
    
    Your private key will be generated using the default filename (for example, `id_rsa`) or the filename you specified (for example, `my_ssh_key`), and stored on your computer in a `.ssh` directory off your home directory (for example, `~/.ssh/id_rsa` or `~/.ssh/my_ssh_key`).
    
    The corresponding public key will be generated using the same filename (but with a `.pub` extension added) and stored in the same location (for example, `~/.ssh/id_rsa.pub` or `~/.ssh/my_ssh_key.pub`).
    
3.  Use [SFTP](https://kb.iu.edu/d/akqg) or [SCP](https://kb.iu.edu/d/agye) to copy the public key file (for example, `~/.ssh/id_rsa.pub`) to your account on the remote system (for example, `darvader@deathstar.empire.gov`); for example, using command-line SCP:
    
    scp ~/.ssh/id\_rsa.pub darvader@deathstar.empire.gov:
    
    You'll be prompted for your account password. Your public key will be copied to your home directory (and saved with the same filename) on the remote system.
    
4.  Log into the remote system using your account username and password.
    
    **Note:**
    
    If the remote system is not configured to support password-based authentication, you will need to ask system administrators to add your public key to the `~/.ssh/authorized_keys` file in your account (if your account doesn't have `~/.ssh/authorized_keys` file, system administrators can create one for you). Once your public key is added to your `~/.ssh/authorized_keys` file on the remote system, the setup process is complete, and you should now be able to SSH to your account from the computer that has your private key.
    
5.  If your account on the remote system doesn't already contain a `~/.ssh/authorized_keys` file, create one; on the command line, enter the following commands:
    
    mkdir -p ~/.ssh
    touch ~/.ssh/authorized\_keys
    
    **Note:**
    
    If your account on the remote system already has a `~/.ssh/authorized_keys` file, executing these commands will not damage the existing directory or file.
    
6.  On the remote system, add the contents of your public key file (for example, `~/id_rsa.pub`) to a new line in your `~/.ssh/authorized_keys` file; on the command line, enter:
    
    cat ~/id\_rsa.pub >> ~/.ssh/authorized\_keys
    
    You may want to check the contents of `~/.ssh/authorized_keys` to make sure your public key was added properly; on the command line, enter:
    
    more ~/.ssh/authorized\_keys
    
7.  You may now safely delete the public key file (for example, `~/id_rsa.pub`) from your account on the remote system; on the command line, enter:
    
    rm ~/id\_rsa.pub
    
    Alternatively, if you prefer to keep a copy of your public key on the remote system, move it to your `.ssh` directory; on the command line, enter:
    
    mv ~/id\_rsa.pub ~/.ssh/
    
8.  Optionally, repeat steps 3-7 to add your public key to other remote systems that you want to access from the computer that has your private key using SSH public key authentication.
9.  You now should be able to SSH to your account on the remote system (for example, `username@host2.somewhere.edu`) from the computer (for example, `host1`) that has your private key (for example, `~/.ssh/id_rsa`):
    
    -   If your private key is password-protected, the remote system will prompt you for the password or passphrase (your private key password/passphrase is not transmitted to the remote system):
        
        \[username@host1 ~\]$ ssh username@host2.somewhere.edu
        Enter passphrase for key '/username/Host1/.ssh/id\_rsa':
        Last login: Mon Oct 20 09:23:17 2014 from host1.somewhere\_else.edu
        
    -   If your private key is not password-protected, the remote system will place you on the command line in your home directory without prompting you for a password or passphrase:
        
        \[username@host1 ~\]$ ssh username@host2.somewhere.edu
        Last login: Mon Oct 20 09:23:17 2014 from host1.somewhere\_else.edu
        
    
    If the private key you're using does not have the default name, or is not stored in the default path (not `~/.ssh/id_rsa`), you must explicitly invoke it in one of two ways:
    
    -   **On the SSH command line:** Add the `-i` flag and the path to your private key.
        
        For example, to invoke the private key `host2_key`, stored in the `~/.ssh/old_keys` directory, when connecting to your account on a remote host (for example, `username@host2.somewhere.edu`), enter:
        
        ssh -i ~/.ssh/old\_keys/host2\_key username@host2.somewhere.edu
        
    -   **In an SSH client configuration file:** SSH gets configuration data from the following sources (in this order):
        
        1.  From command-line options
        2.  From the user's client configuration file (`~/.ssh/config`), if it exists
        3.  From the system-wide client configuration file (`/etc/ssh/ssh_config`)
        
        The SSH client configuration file is a text file containing keywords and arguments. To specify which private key should be used for connections to a particular remote host, use a text editor to create a `~/.ssh/config` that includes the `Host` and `IdentityFile` keywords.
        
        For example, for connections to `host2.somewhere.edu`, to make SSH automatically invoke the private key `host2_key`, stored in the `~/.ssh/old_keys` directory, create a `~/.ssh/config` file with these lines included:
        
        Host host2.somewhere.edu
        IdentityFile ~/.ssh/old\_keys/host2\_key
        
        Once you save the file, SSH will use the specified private key for future connections to that host.
        
        You can add multiple `Host` and `IdentityFile` directives to specify a different private key for each host listed; for example:
        
        Host host2.somewhere.edu
        IdentityFile ~/.ssh/old\_keys/host2\_key
        
        Host host4.somewhere.edu
        IdentityFile ~/.ssh/old\_keys/host4\_key
        
        Host host6.somewhere.edu
        IdentityFile ~/.ssh/old\_keys/host6\_key
        
        Alternatively, you can use a single asterisk ( `*` ) to provide global defaults for all hosts (specify one private key for several hosts); for example:
        
        Host \*.somewhere.edu
        IdentityFile ~/.ssh/old\_keys/all\_hosts\_key
        
        For more about the SSH client configuration file, see the OpenSSH SSH client configuration file [on the web ](http://man7.org/linux/man-pages/man5/ssh_config.5.html) or from the command line (`man ssh_config`).
        

## Set up public key authentication using PuTTY on a Windows 11, Windows 10, or Windows 8.x computer

The PuTTY command-line SSH client, the PuTTYgen key generation utility, the Pageant SSH authentication agent, and the PuTTY SCP and SFTP utilities are packaged together in a Windows installer available under [The MIT License ](https://opensource.org/licenses/MIT) for [free download ](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) from the PuTTY development team.

After installing PuTTY:

1.  Launch .
2.  In the "PuTTY Key Generator" window, under "Parameters":
    -   For "Type of key to generate", select . (In older versions of PuTTYgen, select .)
    -   For "Number of bits in a generated key", leave the default value (`2048`).
3.  Under "Actions", click .
4.  When prompted, use your mouse (or trackpad) to move your cursor around the blank area under "Key"; this generates randomness that PuTTYgen uses to generate your key pair.
5.  When your key pair is generated, PuTTYgen displays the public key in the area under "Key". In the "Key passphrase" and "Confirm passphrase" text boxes, enter a passphrase to passphrase-protect your private key.
    
    **Note:**
    
    If you don't passphrase-protect your private key, anyone with access to your computer will be able to SSH (without being prompted for a passphrase) to your account on any remote system that has the corresponding public key.
    
6.  Save your public key:
    1.  Under "Actions", next to "Save the generated key", click .
    2.  Give the file a name (for example, `putty_key`), select a location on your computer to store it, and then click .
7.  Save your private key:
    1.  Under "Actions", next to "Save the generated key", click .
        
        **Note:**
        
        If you didn't passphrase-protect your private key, the utility will ask whether you're sure you want to save it without a passphrase. Click to proceed or to go back and create a passphrase for your private key.
        
    2.  Keep "Save as type" set to , give the file a name (for example, `putty_private_key`), select a location on your computer to store it, and then click .
    3.  If you wish to connect to a remote desktop system such as [Research Desktop (RED)](https://kb.iu.edu/d/apum), click , give the file a name (for example, `putty_rsa`), select a location on your computer to store it, and then click .
8.  Log into the remote system using your account username and password.
    
    If the remote system does not support password-based authentication, you will need to ask system administrators to add your public key to the `~/.ssh/authorized_keys` file in your account (if your account doesn't have `~/.ssh/authorized_keys` file, system administrators can create one for you). Once your public key is added to your account's `~/.ssh/authorized_keys` file on the remote system...
    
9.  If your account on the remote system doesn't already contain a `~/.ssh/authorized_keys` file, create one; on the command line, enter the following commands:
    
    mkdir -p ~/.ssh
    touch ~/.ssh/authorized\_keys
    
    If your account on the remote system already has `~/.ssh/authorized_keys`, executing these commands will not damage the existing directory or file.
    
10.  On your computer, in the PuTTYgen utility, copy the contents of the public key (displayed in the area under "Key") onto your Clipboard. Then, on the remote system, use your favorite text editor to paste it onto a new line in your `~/.ssh/authorized_keys` file, and then save and close the file.
11.  On your computer, open the Pageant SSH authentication agent. This utility runs in the background, so when it opens, you should see its icon displayed in the Windows notification area.
12.  In the Windows notification area, right-click on the icon, select , navigate to the location where you saved your private key (for example, `putty_private_key.ppk`), select the file, and then click .
13.  If your private key is passphrase-protected, Pageant will prompt you to enter the passphrase; enter the passphrase for your private key, and then click .
    
    If your private key is not passphrase-protected, Pageant will add your private key without prompting you for a passphrase.
    
    Either way, Pageant stores the unencrypted private key in memory for use by PuTTY when you initiate an SSH session to the remote system that has your public key.
    
14.  On your computer, open the PuTTY SSH client:
    
    1.  On the screen:
        -   Under "Host Name (or IP address)", enter your username coupled with the hostname of the remote server that has your public key; for example:
            
            dsidious@deathstar.empire.gov
            
        -   Under "Connection type", make sure is selected.
    2.  In the "Category" list on the left, navigate to the screen (). On the screen, under "Authentication methods", select .
    3.  Return to the screen, and under "Saved Sessions", enter a name (for example, `Deathstar`), and then click .
    4.  Click to connect to your account on the remote system. With Pageant running in the background, PuTTY will retrieve the unencrypted private key automatically from Pageant and use it to authenticate. Because Pageant has your private key's passphrase saved (if applicable), the remote system will place you on the command line in your account without prompting you for the passphrase.
    
    **Note:**
    
    Technically, at this point, the setup is complete. In the future, whenever you log into your Windows desktop, you can run Pageant, add the private key, and then use PuTTY to SSH to any remote resource that has your public key. Alternatively, you can create a shortcut in your Windows `Startup` folder to launch Pageant and load your private key automatically whenever you log into your desktop. For instructions, finish the rest of the following steps.
    
15.  Open your `Startup` folder. Press `Win-r`, and in the "Open" field, type `shell:startup`, and then press `Enter`.
16.  Right-click inside the `Startup` folder, and then select and .
17.  In the "Type the location of the item" text box, enter the path to the Pageant executable (`pageant.exe`) followed by the path to your private key file (for example, `putty_private_key.ppk`); enclose both paths in double quotes; for example:
    
    "C:\\Program Files (x86)\\PuTTY\\pageant.exe"
    "C:\\Users\\user\_profile\\ssh\_key\\putty\_private.ppk"
    
18.  Click , and then, in the "Type a name for this shortcut" text box, enter a name for the shortcut (for example, `PAGEANT`).
19.  Click .

The next time you log into your Windows desktop, Pageant will start automatically, load your private key, and (if applicable) prompt you for the passphrase.

*This is document* aews *in the Knowledge Base.*  
*Last modified on* 2021-12-01 17:09:53*.*