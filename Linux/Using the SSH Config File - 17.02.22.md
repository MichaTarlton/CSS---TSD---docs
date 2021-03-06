![SSH Config File](https://linuxize.com/post/using-the-ssh-config-file/featured_hu757e4498ed063c11153af0c1eb864796_18241_768x0_resize_q75_lanczos.jpg)

If you are regularly connecting to multiple remote systems over SSH, you’ll find that remembering all of the remote IP addresses, different usernames, non-standard ports, and various command-line options is difficult, if not impossible.

One option would be to [create a bash alias](https://linuxize.com/post/how-to-create-bash-aliases/) for each remote server connection. However, there is another, much better, and more straightforward solution to this problem. OpenSSH allows you to set up a per-user configuration file where you can store different SSH options for each remote machine you connect to.

This article covers the basics of the SSH client configuration file and explains some of the most common configuration options.

## Prerequisites

We are assuming that you are using a Linux or a macOS system with an OpenSSH client installed.

## SSH Config File Location

OpenSSH client-side configuration file is named `config`, and it is stored in the `.ssh` directory under the user’s home directory.

The `~/.ssh` directory is automatically created when the user runs the [`ssh`](https://linuxize.com/post/ssh-command-in-linux/) command for the first time. If the directory doesn’t exist on your system, create it using the command below:

```
mkdir -p ~/.ssh && chmod 700 ~/.ssh
```

By default, the SSH configuration file may not exist, so you may need to create it using the [`touch` command](https://linuxize.com/post/linux-touch-command/) :

```
touch ~/.ssh/config
```

This file must be readable and writable only by the user and not accessible by others:

```
chmod 600 ~/.ssh/config
```

## SSH Config File Structure and Patterns

The SSH Config File takes the following structure:

```
Host hostname1
    SSH_OPTION value
    SSH_OPTION value

Host hostname2
    SSH_OPTION value

Host *
    SSH_OPTION value
```

The contents of the SSH client config file is organized into stanzas (sections). Each stanza starts with the `Host` directive and contains specific SSH options used when establishing a connection with the remote SSH server.

Indentation is not required but is recommended since it makes the file easier to read.

The `Host` directive can contain one pattern or a whitespace-separated list of patterns. Each pattern can contain zero or more non-whitespace character or one of the following pattern specifiers:

-   `*` - Matches zero or more characters. For example, `Host *` matches all hosts, while `192.168.0.*` matches hosts in the `192.168.0.0/24` subnet.
-   `?` - Matches exactly one character. The pattern, `Host 10.10.0.?` matches all hosts in `10.10.0.[0-9]` range.
-   `!` - When used at the start of a pattern, it negates the match. For example, `Host 10.10.0.* !10.10.0.5` matches any host in the `10.10.0.0/24` subnet except `10.10.0.5`.

The SSH client reads the configuration file stanza by stanza, and if more than one patterns match, the options from the first matching stanza take precedence. Therefore more host-specific declarations should be given at the beginning of the file, and more general overrides at the end of the file.

You can find a full list of available ssh options by typing `man ssh_config` in your terminal or visiting the [ssh\_config man page](https://man.openbsd.org/OpenBSD-current/man5/ssh_config.5) .

The SSH config file is also read by other programs such as [`scp`](https://linuxize.com/post/how-to-use-scp-command-to-securely-transfer-files/) , [`sftp`](https://linuxize.com/post/how-to-use-linux-sftp-command-to-transfer-files/) , and [`rsync`](https://linuxize.com/post/how-to-use-rsync-for-local-and-remote-data-transfer-and-synchronization/) .

## SSH Config File Example

Now that we’ve covered the basics of the SSH configuration file let’s look at the following example.

Typically, when connecting to a remote server via SSH, you would specify the remote user name, hostname, and port. For example, to log in as a user named `john` to a host called `dev.example.com` on port `2322` from the command line, you would type:

```
ssh john@dev.example.com -p 2322
```

To connect to the server using the same options as provided in the command above, simply by typing `ssh dev`, put the following lines to your `"~/.ssh/config` file:

~/.ssh/config

```
Host dev
    HostName dev.example.com
    User john
    Port 2322
```

Now when you type `ssh dev`, the ssh client will read the configuration file and use the connection details that are specified for the `dev` host:

```
ssh dev
```

This example gives more detailed information about the host patterns and option precedence.

Let’s take the following example file:

```
Host targaryen
    HostName 192.168.1.10
    User daenerys
    Port 7654
    IdentityFile ~/.ssh/targaryen.key

Host tyrell
    HostName 192.168.10.20

Host martell
    HostName 192.168.10.50

Host *ell
    user oberyn

Host * !martell
    LogLevel INFO

Host *
    User root
    Compression yes
```

-   When you type `ssh targaryen`, the ssh client reads the file and apply the options from the first match, which is `Host targaryen`. Then it checks the next stanzas one by one for a matching pattern. The next matching one is `Host * !martell` (meaning all hosts except `martell`), and it will apply the connection option from this stanza. The last definition `Host *` also matches, but the ssh client will take only the `Compression` option because the `User` option is already defined in the `Host targaryen` stanza.
    
    The full list of options used when you type `ssh targaryen` is as follows:
    
    ```
    HostName 192.168.1.10
    User daenerys
    Port 7654
    IdentityFile ~/.ssh/targaryen.key
    LogLevel INFO
    Compression yes
    ```
    
-   When running `ssh tyrell` the matching host patterns are: `Host tyrell`, `Host *ell`, `Host * !martell` and `Host *`. The options used in this case are:
    
    ```
    HostName 192.168.10.20
    User oberyn
    LogLevel INFO
    Compression yes
    ```
    
-   If you run `ssh martell`, the matching host patterns are: `Host martell`, `Host *ell` and `Host *`. The options used in this case are:
    
    ```
    HostName 192.168.10.50
    User oberyn
    Compression yes
    ```
    
-   For all other connections, the ssh client will use the options specified in the `Host * !martell` and `Host *` sections.
    

## Override SSH Config File Option

The ssh client reads its configuration in the following precedence order:

1.  Options specified from the command line.
2.  Options defined in the `~/.ssh/config`.
3.  Options defined in the `/etc/ssh/ssh_config`.

If you want to override a single option, you can specify it on the command line. For example, if you have the following definition:

```
Host dev
    HostName dev.example.com
    User john
    Port 2322
```

and you want to use all other options but to connect as user `root` instead of `john` simply specify the user on the command line:

```
ssh -o "User=root" dev
```

The `-F` (`configfile`) option allows you to specify an alternative per-user configuration file.

To tell the `ssh` client to ignore all of the options specified in the ssh configuration file, use:

```
ssh -F /dev/null user@example.com
```

## Conclusion

We’ve shown you how to how to configure your user ssh config file. You may also want to set up an [SSH key-based authentication](https://linuxize.com/post/how-to-setup-passwordless-ssh-login/) and connect to your Linux servers without entering a password.

By default, SSH listens on port 22. [Changing the default SSH port](https://linuxize.com/post/how-to-change-ssh-port-in-linux/) adds an extra layer of security to your server by reducing the risk of automated attacks.

If you have any questions, please leave a comment below.