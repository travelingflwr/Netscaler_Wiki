## Tips for prepping for a support case
[Back to Netscaler](netscaler.md)

### Here's a one liner for getting a ton of relevant information to provide in a support case
Copy and paste this into the Netscaler CLI (not shell)
	
	show hostname; shell uptime; show version; show hardware; shell /bin/sh -c "sysctl netscaler | grep 'sysid\|serial\|descr\|num_pe_running'"; shell df; show license; shell /bin/sh -c "grep 'avail memory' /var/nslog/dmesg*"; stat system -detail | grep 'Power supply'; shell /bin/sh -c "ipmitool sel elist | tail -10"; shell /bin/sh -c "ipmitool sensor list | grep 'PS_'"; shell ipmitool mc info

This could also be a handy troubleshooting tool for gather output.  Breaking out the commands and their importance.

Supplying the output in a case can help to fast track a support or escalation engineer can get up to speed on your issue.

| Command						| Description 								|
| :---           				| :----   									|
| show hostname  				| Identifies the system that the logs belong to - Useful in the cases where multiple log bundles are being investigated | 
| 	shell uptime 				| Shows the uptime for the system - useful in determining if uptime may be an issue |
| 	show version 				| Shows which Netscaler build is on the system |
| 	show hardware 				| Shows the platform the system is and also the serial number			|
| 	shell /bin/sh -c "sysctl netscaler &#124; grep 'sysid&#92;&#124;serial&#92;&#124;descr&#92;&#124;num_pe_running'" |	Identifies system level details including the number of PE's on the system		|
|	shell df 					|	SHows disk space usage		|
|	show license 				|	SHows what the system is licensed for		|
|	shell /bin/sh -c "grep 'avail memory' /var/nslog/dmesg*"; stat system -detail &#124; grep 'Power supply' | Shows memory status of the system - Quickly useful for determining if the system has dropped a DIMM card		|
|	shell /bin/sh -c "ipmitool sel elist &#124; tail -10" |	System power supply messages		|
|	shell /bin/sh -c "ipmitool sensor list &#124; grep 'PS_'" |	System power supply status		|
|	shell ipmitool mc info 		|	More power supply data		|
	