# cis18 benchmarks ubuntu 22 and debian 11 IG1

Bash script developed for hardening ubuntu 22 and debian 11 according to CIS IG1 remidations only. Not audits.
It's function is only intended for one time use on a new server setup.


## Info regarding hostbased firewall, remote central logserver

**Firewall** this script is using IPtables. Not UFW or NFtables, they are removed according to CIS requirements, because IPtables was chosen as primary.
**Log server** this script is using Wazuh as central log server [What is Wazuh ?](https://documentation.wazuh.com/current/getting-started/architecture.html)

## Prerequisites before running the script

1. Partitions

If you wish having seperate partitions according to CIS 18 IG1, you must create these during installation of server. Pick sizes of your prefered liking:

/var
/var/tmp
/var/log
/var/log/audit
/tmp
/
/home

2. Prepare firewall rules

I have made a iptables_rules.txt file with some default rules for cis recommendations. Correct it to your usecase, but make sure its according to recommendations at the same time.

3. Chosing what benchhmark to run 

At the end of the script there is a main function calling the other functions. You can pick and choice what benchmarks you want according to those. Lets say you do not wish to use to use Wazuh because you dont have a Wazuh server, comment the function call out. Then it will be your own responsibilty to setup this part yourself. Same goes for the rest.

4. Privileges needed to run

Run script as sudo or root

5. Download the benchmakrs pdf from CIS (Ubuntu 22 server & Debian 11 server) before you run

Helps you understand every implemention and why CIS recommend them for security

Run script as sudo or root

## Running the script on your Ubuntu/Debian server

```bash
git clone git@github.com:ulrik-vj/cis18-benchmarks-ubuntu-debian-ig1.git
cd cis18-benchmarks-ubuntu-debian-ig
sudo chmod +x cis_ig1_hardening.sh
./cis_ig1_hardening.sh
```

## Would be nice to implement in the future
- [ ] Make script more userfriendly/readable
- [ ] Make script seperate partitions if possible
- [ ] Make user be able to choice what benchmarks they want from main function to call (all of them or pick and chose), instead of having to comment it out
- [ ] Implement cloud init fix for bootloader interfering from files in the dir /etc/default/grub.d/ when making bootloader changes. If user is using cloud init that is
- [ ] If user wish to only boot into VM using bootlader password, enable so. Right now bootloader PW is only required for entering boot parameters for convenience

## License

[GNU General Public License v3.0](LICENSE)
