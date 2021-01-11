## Week 4 Homework Submission File: Linux Systems Administration

### Step 1: Ensure/Double Check Permissions on Sensitive Files

1. Permissions on `/etc/shadow` should allow only `root` read and write access.

    - Command to inspect permissions: ls -l /etc/shadow

    - Command to set permissions (if needed): sudo chmod /etc/shadow

2. Permissions on `/etc/gshadow` should allow only `root` read and write access.

    - Command to inspect permissions: ls -l /etc/gshadow

    - Command to set permissions (if needed): sudo chmod /etc/gshadow

3. Permissions on `/etc/group` should allow `root` read and write access, and allow everyone else read access only.

    - Command to inspect permissions: ls -l /etc/group

    - Command to set permissions (if needed): sudo chmod /etc/group

4. Permissions on `/etc/passwd` should allow `root` read and write access, and allow everyone else read access only.

    - Command to inspect permissions: ls -l /etc/passwd

    - Command to set permissions (if needed): sudo chmod /etc/passwd

### Step 2: Create User Accounts

1. Add user accounts for `sam`, `joe`, `amy`, `sara`, and `admin`.

    - Command to add each user account (include all five users): sudo useradd sam
                                                                 sudo useradd joe
                                                                 sudo useradd amy
                                                                 sudo useradd sara
                                                                 sudo useradd admin
2. Ensure that only the `admin` has general sudo access.

    - Command to add `admin` to the `sudo` group: sudo usermod -aG sudo admin

### Step 3: Create User Group and Collaborative Folder

1. Add an `engineers` group to the system.

    - Command to add group: sudo addgroup engineers

2. Add users `sam`, `joe`, `amy`, and `sara` to the managed group.

    - Command to add users to `engineers` group (include all four users): sudo usermod -G engineers sam
                                                                          sudo usermod -G engineers joe
                                                                          sudo usermod -G engineers amy
                                                                          sudo usermod -G engineers sara
                                                                          sudo usermod -G engineers admin
3. Create a shared folder for this group at `/home/engineers`.

    - Command to create the shared folder: sudo mkdir -p /home/engineers

4. Change ownership on the new engineers' shared folder to the `engineers` group.

    - Command to change ownership of engineer's shared folder to engineer group: sudo chgrp -R engineers /home/engineers

### Step 4: Lynis Auditing

1. Command to install Lynis: sudo apt-get install lynis

2. Command to see documentation and instructions: man lynis

3. Command to run an audit: sudo lynis audit system

4. Provide a report from the Lynis output on what can be done to harden the system.

  * Consider hardening SSH configuration [SSH-7408] 
    - Details  : AllowTcpForwarding (YES --> NO)
      https://cisofy.com/controls/SSH-7408/

  * Consider hardening SSH configuration [SSH-7408] 
    - Details  : ClientAliveCountMax (3 --> 2)
      https://cisofy.com/controls/SSH-7408/

  * Consider hardening SSH configuration [SSH-7408] 
    - Details  : Compression (YES --> (DELAYED|NO))
      https://cisofy.com/controls/SSH-7408/

  * Consider hardening SSH configuration [SSH-7408] 
    - Details  : LogLevel (INFO --> VERBOSE)
      https://cisofy.com/controls/SSH-7408/

  * Consider hardening SSH configuration [SSH-7408] 
    - Details  : MaxAuthTries (6 --> 2)
      https://cisofy.com/controls/SSH-7408/

  * Consider hardening SSH configuration [SSH-7408] 
    - Details  : MaxSessions (10 --> 2)
      https://cisofy.com/controls/SSH-7408/

  * Consider hardening SSH configuration [SSH-7408] 
    - Details  : PermitRootLogin (WITHOUT-PASSWORD --> NO)
      https://cisofy.com/controls/SSH-7408/

  * Consider hardening SSH configuration [SSH-7408] 
    - Details  : Port (22 --> )
      https://cisofy.com/controls/SSH-7408/

  * Consider hardening SSH configuration [SSH-7408] 
    - Details  : TCPKeepAlive (YES --> NO)
      https://cisofy.com/controls/SSH-7408/

  * Consider hardening SSH configuration [SSH-7408] 
    - Details  : X11Forwarding (YES --> NO)
      https://cisofy.com/controls/SSH-7408/

  * Consider hardening SSH configuration [SSH-7408] 
    - Details  : AllowAgentForwarding (YES --> NO)
      https://cisofy.com/controls/SSH-7408/

   


### Bonus
1. Command to install chkrootkit: sudo apt-get install chkrootkit

2. Command to see documentation and instructions: man chkrootkit

3. Command to run expert mode: sudo chkrootkit -x

4. Provide a report from the chrootkit output on what can be done to harden the system.
    - Screenshot of end of sample output: 
    
! sysadmin     2653 tty2   /usr/lib/gnome-settings-daemon/gsd-xsettings
! sysadmin     2540 tty2   ibus-daemon --xim --panel disable
! sysadmin     2544 tty2   /usr/lib/ibus/ibus-dconf
! sysadmin     2829 tty2   /usr/lib/ibus/ibus-engine-simple
! sysadmin     2548 tty2   /usr/lib/ibus/ibus-x11 --kill-daemon
! sysadmin     2742 tty2   nautilus-desktop
! root        13061 pts/0  /bin/sh /usr/sbin/chkrootkit -x
! root        13494 pts/0  ./chkutmp
! root        13496 pts/0  ps axk tty,ruser,args -o tty,pid,ruser,args
! root        13495 pts/0  sh -c ps axk "tty,ruser,args" -o "tty,pid,ruser,args"
! root        13060 pts/0  sudo chkrootkit -x
! sysadmin    13037 pts/0  bash
chkutmp: nothing deleted
not tested


---
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
