In [Unix](https://kb.iu.edu/d/agat), `ssh-agent` is a background program that handles passwords for [SSH](https://kb.iu.edu/d/aelc) private keys. The `ssh-add` command prompts the user for a private key password and adds it to the list maintained by `ssh-agent`. Once you add a password to `ssh-agent`, you will not be prompted for it when using SSH or [scp](https://kb.iu.edu/d/agye) to connect to hosts with your public key.

The public part of the key loaded into the agent must be put on the target system in `~/.ssh/authorized_keys`; see [Set up SSH public key authentication to connect to a remote system](https://kb.iu.edu/d/aews).

To use `ssh-agent` and `ssh-add`, follow the steps below:

1.  At the Unix prompt, enter:
    
     eval \`ssh-agent\`
    
    Make sure you use the backquote (`` ` ``), located under the tilde (`~`), rather than the single quote (`'`).
    
2.  Enter the command:
    
     ssh-add
    
3.  Enter your private key password.
4.  When you log out, enter the command:
    
     kill $SSH\_AGENT\_PID
    
    To run this command automatically when you log out, place it in your `.logout` file (if you are using `csh` or `tcsh`) or your `.bash_logout` file (if you are using `bash`).

**Note:**

The versions of these programs for [SSH2](https://kb.iu.edu/d/aelc), `ssh-agent2` and `ssh-add2`, are the same as outlined above. To use them, follow the instructions above, replacing all occurrences of `ssh-agent` with `ssh-agent2`, and `ssh-add` with `ssh-add2`. The SSH2 versions will only work if both your computer and the remote host are running SSH2.

*This is document* aeww *in the Knowledge Base.*  
*Last modified on* 2019-06-18 14:44:33*.*