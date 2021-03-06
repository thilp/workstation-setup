Instead of upgrading "in place" my operating system for each new major version,
I prefer wiping it clean and having a fresh start.
I've found that this also encourages a good backup hygiene.

However, I'm used to certain tools and consider them necessary to be productive
in my work. Reinstalling them at the same time as the OS is tedious because
many cannot be immediately installed via the OS' package manager.
At first I automated the process of installing these tools with a shell script.
The many usual weaknesses of shell scripting (I don't want to maintain 300+
lines of shell to ensure proper error reporting, idempotence, and absence of
quoting bugs) later drove me to Ansible for this task.

- `duplicity.yaml` restores everything I need from my
  [Duplicity](http://duplicity.nongnu.org) backups (mostly config files, git
  repos and documents — no software of course).
- `fedora.yaml` installs all the software I need, or updates it if it is
  already installed.

With [ansible-pull](https://docs.ansible.com/ansible/latest/cli/ansible-pull.html):
```
ansible-pull -KU https://github.com/thilp/workstation-setup.git fedora.yml
```

TODO:
  - Configure Gnome:
      - wallpaper
      - keymap
