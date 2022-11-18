## NSCONMSG Queries from the field
[Table of contents](README.md)


### Display newnslog start and end time information
	nsconmsg -K newnslog -d setime

### Used for looping through all ns.conf files to find when a change has been made:
	for i in ns.conf*; do echo ----$i----; diff -y $i ns_running_config.conf | grep -i "add lb monitor loopback_keep_alive_http_https" ;done 

### Detect a nsm router reset
	nsconmsg -K newnslog -s disptime=1 -g ha_cur_hasync_pcb -g ha_tot_sync_connects -d current
	nsconmsg -K newnslog -d event

### Loop through all open newnslogs to interface errors
	for i in newnslog* ; do echo ---$i ; nsconmsg -K $i -s disptime=1 -g nic_err -d current | more; done