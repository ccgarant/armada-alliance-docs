```bash
# The Ergo Node Service (part of systemd)
# file: /etc/systemd/system/ergo-node.service

[Unit]
Description         =Ergo Node Service
Wants               =network-online.target
After               =network-online.target

[Service]
User                =pi
Type                =simple

#note path/to/ergo-node in this tutorial is /mnt/hd1/ergo-node but in general =/path/to/ergo-node
WorkingDirectory    =/path/to/ergo-node

                    #update the version!!!
ExecStart           =/usr/bin/java -jar -Xmx2g ergo-<VERSION>.jar --mainnet -c ergo.conf
KillSignal          =SIGINT
RestartKillSignal   =SIGINT
TimeoutStopSec      =10
LimitNOFILE         =32768
Restart             =always
RestartSec          =10
#EnvironmentFile    =

[Install]
WantedBy            =multi-user.target
```