# .Net Framework/.Net Core Class Library for IBM i - AS/400 Database and Program Access over SSH
SShNetIbmi/IbmiXmlServiceStdSsh is a .Net Standard 2.0 class library for accessing IBM i system services via SSH from .Net Framework 4.6.2 and above as well as .Net Core 2.0 and above.  

.Net applications can access PASE, QShell, bash, SSH and XMLSERVICE functionality using a secure SSH system connection via user/password or SSH private key authentication.

The class library can be used to connect with an IBM i system over SSH. The library can interface to the IBM i database via SQL, program calls, CL commands, service programs and data queues via the PASE based ```xmlservice-cli``` command line program (part of open source package ```itoolkit-utilities```).    

Regular qsh/bash commands can also be run to interface with utilities such as the [IBM i db2util utility](https://github.com/IBM/ibmi-db2util) or programs written in languages such as Java, Python, PHP, Node.js and more.

Query and program call return data is returned in .Net DataTable format, JSON, CSV or you can process the raw XMLSERVICE responses yourself.

The IBMiXmlServiceStdSsh class library can be installed to your .Net project from Nuget. https://www.nuget.org/packages/IbmiXmlserviceStdSsh   

```Commercial .Net development and product support can be purchased through MobiGoGo LLC``` (http://www.mobigogo.net)

# Install from Nuget

https://www.nuget.org/packages/IbmiXmlserviceStdSsh

# IBM i System Requirements:
 ● XMLSERVICE methods require the ```xmlservice-cli``` package installed on the target system via yum packages (/QOpenSys/pkgs.bin/xmlservice-cli). Installs as part of part of the open source ```itoolkit-utilities```.
 
 ● The class library Uses ```SSH.Net``` for SSH connectivity so IBM i SSH server must be running. (V7R2 and above)

 Starting your SSH server   
 ```STRTCPSVR *SSHD```
 
 ● Set up user's SSH shell default to be ```bash```. (See below)
 
 ● The ```XMLSERVICE``` service program library ```QXMLSERV``` must also exist on the system, This library is installed as part of the IBM i operating system.
 
XMLSERVICE is typically packaged on the IBMi in library: ```QXMLSERV``` as part of the operating system, but if you want to play with the code, here's the current Github location as of 1/23/2019    

https://github.com/IBM/xmlservice
 
 ● Make sure the IBM i user you will be using for SSH access has /QOpenSys/pkgs/bin in the user search path. 
 
 ```export PATH=/QOpenSys/pkgs/bin:$PATH```
 
**Note: For appropriate security you should configure your SSH users for appropriate security limitations in the IFS and for libraries and commands that may be accessed over an SSH connection to IBM i.**

# Set default shell to bash for SSH user
Nowadays, the best way to do this is to using QSYS2.SET_PASE_SHELL_INFO() SQL procedure from your favorite SQL tool or STRSQL

```
-- set current user's shell
CALL QSYS2.SET_PASE_SHELL_INFO('*CURRENT', '/QOpenSys/pkgs/bin/bash');

-- set a specific user's shell
-- (requires *SECADM special auth plus *USE and *OBJMGT to the user profile)
CALL QSYS2.SET_PASE_SHELL_INFO('THATUSER', '/QOpenSys/pkgs/bin/bash');

-- set the default shell which is returned for users that do not have
-- (requires *SECADM special auth plus *USE and *OBJMGT to QSYS)
CALL QSYS2.SET_PASE_SHELL_INFO('*DEFAULT', '/QOpenSys/pkgs/bin/bash');
```
https://stackoverflow.com/questions/23913957/set-default-pase-ibm-i-shell-for-individual-user
