# FileMaker-LetsEncrypt-Linux, the setup I relate to is described here: [BHYVE Joyent SmartOS w/FileMaker 2023 Server under Ubuntu]([/guides/content/editing-an-existing-page](https://gist.github.com/TyrfingMjolnir/234402499468db36b21f1bf36116a01e))
A bash script for fetching and renewing Let's Encrypt SSL certificates for FileMaker Server running on Linux using certbot.

Setup instructions and an example video can be found at https://bluefeathergroup.com/blog/lets-encrypt-ssl-certificates-for-filemaker-server-for-mac/ the linux alternative will differ.

## How to use:
The script utilizes certbot to get SSL certificates from Let's Encrypt. Install certbot via homebrew:
```
apt-get install certbot
```

Change directory into the cloned repository and run:
```
sudo ./GetSSL.sh
```
*Script requires root privileges for certain functions. Always review the code before running any script as root.*

For help on options, run:
```
./GetSSL.sh --help
```

NginX
```
$ service nginx status
```

FileMaker 2023 Server
```
$ service fmshelper status
$ service fmshelper stop
$ service fmshelper start
```

More FileMaker 2023 Server
```
$ fmsadmin list files
username (admin):admin
password:
filelinux:/opt/FileMaker/FileMaker Server/Data/Databases/Sample/FMServer_Sample.fmp12
filelinux:/opt/FileMaker/FileMaker Server/Data/Databases/Agenda.fmp12
filelinux:/opt/FileMaker/FileMaker Server/Data/Databases/Stellar Winds.fmp12
```

```
$ fmsadmin help commands
fmsadmin commands are:

    AUTORESTART     Get or set auto-restart for the Admin Server or FMSE
    BACKUP          Back up databases
    CANCEL          Cancel the currently running operation
    CERTIFICATE     Manage SSL certificates
    CLEARKEY        Removes saved database encryption passwords
    CLOSE           Close databases
    DISABLE         Disable schedules or detailed statistics logging
    DISCONNECT      Disconnect a client
    ENABLE          Enable schedules or detailed statistics logging
    GET             Retrieve server or CWP configuration settings, or retrieve
                    the start time of a backup schedule or schedules
    HELP            Get help pages
    LIST            List clients, databases, plug-ins, or schedules
    OPEN            Open databases
    PAUSE           Temporarily stop database access
    REMOVE          Move databases out of hosted folder or remove empty folder
    RESETPW         Reset admin user password
    RESTART         Restart a server process
    RESUME          Make paused databases available
    RUN             Run a schedule
    SEND            Send a message
    SET             Change server or CWP configuration settings, or change the
                    start time of a backup schedule
    START           Start a server process
    STATUS          Get status of clients or databases
    STOP            Stop a server process
    VERIFY          Check the consistency of databases
    WPE             Add, remove, and list secondary FileMaker WebDirect machines
```
