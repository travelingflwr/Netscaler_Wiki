## NSCONMSG Queries from the field
[Back to Netscaler](netscaler.md)

[Link to the Citrix Support nsconmsg cheatsheet](https://docs.citrix.com/en-us/tech-zone/learn/diagrams-posters/cheat-sheet-adc-nsconmsg.html)

### Display newnslog start and end time information for a given newnslog
	nsconmsg -K newnslog -d setime

### Get the NSIP from a newnslog
	nsconmsg -K newnslog -d devname | grep 'NetScaler_IP'

### Used for looping through all ns.conf files to find when a change has been made:
	for i in ns.conf*; do echo ----$i----; diff -y $i ns_running_config.conf | grep -i "add lb monitor loopback_keep_alive_http_https" ;done 

### Detect a nsm router reset
	nsconmsg -K newnslog -s disptime=1 -g ha_cur_hasync_pcb -g ha_tot_sync_connects -d current
	nsconmsg -K newnslog -d event

### Loop through all open newnslogs to interface errors
	for i in $(ls -d /var/nslog/newnslog*[!tar.gz]) ; do echo ---$i ; nsconmsg -K $i -s disptime=1 -g nic_err -d current | more; done

### Command to get the setime from new ncore newnslog files in directories and to exclude the tar.gz files
	for i in $(ls -d newnslog.*[!tar.gz]); do echo "==================$i===================";nsconmsg -K $i -d setime; echo ""; done

### Command to look at VPN/ICA user details
	nsconmsg -K newnslog -g curAaaUsersPerVserver -g si_curaaausers -g maxsslvpnusers -g svpn_lic_failed -g svpn_maxusers_lic_failed -g ica_license_failure -g tot_lic_shared_ica_vpn -g total_ica_connections -s disptime-1 -d current | more

### Command to look at total ICA users and ICA license failures:
	nsconmsg -K newnslog -g ica_license -g total_ica_connections -s disptime=1 -d current | more

### Command to look for monitor stats, print current time, and print 8 lines after monitor match:
	nsconmsg9 -K newnslog -s ConMon=3 -d oldconmsg | nawk '/current time/ {print $0} /172.29.189.217:3306/ {print;n=8;next}n{print;n--}' > mysql_mon.log