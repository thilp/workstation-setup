# Fresh Install Checklist

    $ sudo dnf upgrade

## Restore backup

Copy backups.tar in $HOME.

    $ sudo dnf install duplicity

    $ cd $HOME && tar xf backups.tar

    $ sudo duplicity restore file://$HOME/backups $HOME/restored

    $ rsync -ah $HOME/restored/$HOME/ $HOME  # trailing slash avoids creating redundant directory

    $ sudo rsync -ah $HOME/restored/root/{backup.py,.config} /root/

    $ sudo rsync -ah $HOME/restored/etc/{anacrontab,cron.3days/full-backup,cron.weekly/compact-backups} /etc/

    $ sudo crontab -e

    0 */3 * * *     env PASSPHRASE=*** BACKUP_MODE=incr /root/backup.py >>/var/log/backup.log 2>&1

    $ rm -rf $HOME/restored

## Setup terminal

Download the latest release archive from:
https://github.com/belluzj/fantasque-sans/releases.
Open the archive in Nautilus, go in the OTF directory, double-click on each
font file, click on "Install".

## Install remaining software

    $ ansible-playbook -K $HOME/git/thilp/workstation-setup/fedora.yml 
