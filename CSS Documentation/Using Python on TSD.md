# Using Python on TSD
> Local copy of https://wiki.norment.uiocloud.no/dokuwiki/tsd_software

Using Python on TSD is briefly described [https://www.uio.no/english/services/it/research/sensitive-data/help/software/python.html](https://www.uio.no/english/services/it/research/sensitive-data/help/software/python.html "https://www.uio.no/english/services/it/research/sensitive-data/help/software/python.html").

On Windows VMs, python is available through Anaconda (but to the best of my knowledge there is no official mirror of Anaconda packages within TSD - so you have whatever is pre-installed with Anaconda, but everything beyond that you need to install yourself).

On linux VM, you need to load python via `module`. This only works on machines where `/cluster` is mounted (as of now, that's p33-submit and the RHEL7 login node).

If you are using `python3`, it's nice to deploy everything into your custom virtual environment (`venv`, read more here [https://docs.python.org/3/library/venv.html](https://docs.python.org/3/library/venv.html "https://docs.python.org/3/library/venv.html")). Once you `source activate` your environment, install python package with `pip3 install` without `–user`.

ssh -Y p697-appn-norment01   (This command is for thin link users)
module load  Python/3.7.4-GCCcore-8.3.0 (This command is for VM ware Horizon users)


# clean install jupyter in a new environment
`python3 -m venv /cluster/projects/p697/users/<user>/py3`      
- update `<user> `with your TSD username

`source /cluster/projects/p697/users/<user>/py3/bin/activate`  
- best to have this on /cluster

```
pip3 install numpy
pip3 install pandas
pip3 install scipy
pip3 install matplotlib
pip3 install statsmodels
pip3 install numdifftools
pip3 install matplotlib_venn
pip3 install jupyter
```

Note that the above commands MUST NOT include --index-url=file:///shared/pypi/mirror/web/simple; this is an old mirror on TSD that is no longer maintained - only old versions of the packages are available from this mirror, and it's going to be deprecated soon.

When everything is installer, you may use python on a new terminal (and in your Colossus jobs) as follows

```
module load  Python/3.7.4-GCCcore-8.3.0
source /cluster/projects/p33/users/<user>/py3/bin/activate
```

The stuff below is quite advanced - most likely you don't need it. But if you are interested in using jupyter on a remote VM (e.g. p33-submit or p33-appn-norment01), remember to that you connect to it as follows.


```
# on p697-appn-norment01
jupyter notebook --no-browser --port=8888 (This command is for VM ware Horizon users)

# directly on the login node 
ssh -N -f -L localhost:8888:localhost:8888 p697-michaejt@p697-appn-norment01 

#(This command is for thin link users)

# open your browser and connect to
localhost:8888
```

To connect to jupyter session from Windows you need to configure port forwarding in Putty. To enable this, do as on the screenshot below. To clarify: you'll probably need one “usual” session in Putty (i.e. without port forwarding) to establish “ssh” connection to your remote server and start a jupyter notebook. The host name for establish the remote session is “p33-appn-norment01”. Then, you'll need a second session in Putty with port forwarding as on the screenshot below; also note that putty config windows has to be closed for the putty session to work). Some basics are described here: [https://stackoverflow.com/questions/46276612/remote-access-jupyter-notebook-from-windows](https://stackoverflow.com/questions/46276612/remote-access-jupyter-notebook-from-windows "https://stackoverflow.com/questions/46276612/remote-access-jupyter-notebook-from-windows")

UPD: screenshot below shows different ports: 8888 and 8889. It's much less confusing to use the same port, i.e. to start jupyter on 8888, and forward this port to 8888 on Windows machine. This works, there is no conflict here because ports are on different machines.

[![](https://wiki.norment.uiocloud.no/dokuwiki/_media/puttyportforwarding.png?w=300&tok=fda8b0)](https://wiki.norment.uiocloud.no/dokuwiki/_detail/puttyportforwarding.png?id=tsd_software "puttyportforwarding.png")

## Running on the Windows login node
Just open jupyter from the start menu or better yet run it from powershell: 
```
jupyter notebook
```

I’m not sure how to run it from redhat nodes for now.

