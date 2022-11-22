## Tips for prepping for a support case
[Back to Netscaler](netscaler.md)

### The number one useful data for your support case!!
Identify and communicate in the submitted case the impact of your problem.  We are all engineers and nearly all engineers forget this but it's the most useful data for priortizing and triaging a case.

If a support engineer knows that "your issue" is impacting 500, 1000, all of your users, they are most likely going to start on your case ahead of others with no or lessa stated impact.  If you open a case via the web portal as a Sev 2 and the support engineer sees a large impact, they are most likeley going to bump your case to a Sev 1 to get some additiona urgency and help on the case.  If you have Priority Support, a Sev 1 case will trigger CritSit which is a really good thing for you.

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
	



	{
	"firstName": "John",
	"lastName": "Smith",
	"age": 25
	}
