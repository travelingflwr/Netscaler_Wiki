## NSCONMSG Query Cheatsheet
[Table of contents](toc.md)


### Display start and end time information
time zone is the same as the system running nsconmsg

	nsconmsg -K newnslog -d setime

### Used for looping through all ns.conf files to find when a change has been made:

	for i in ns.conf*; do echo ----$i----; diff -y $i ns_running_config.conf | grep -i "add lb monitor loopback_keep_alive_http_https" ;done 

