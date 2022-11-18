## Tips for prepping for a support case
[Back to Netscaler](netscaler.md)

### Here's a one liner for getting a ton of relevant information to provide in a support case
Copy and paste this into the Netscaler CLI (not shell)
	
	show hostname; shell uptime; show version; show hardware; shell /bin/sh -c "sysctl netscaler | grep 'sysid\|serial\|descr\|num_pe_running'"; shell df; show license; shell /bin/sh -c "grep 'avail memory' /var/nslog/dmesg*"; stat system -detail | grep 'Power supply'; shell /bin/sh -c "ipmitool sel elist | tail -10"; shell /bin/sh -c "ipmitool sensor list | grep 'PS_'"; shell ipmitool mc info

This could also be a handy troubleshooting tool for gather output.  I'll break out the individual commands later on this page

	show hostname
	shell uptime
	show version
	show hardware
	shell /bin/sh -c "sysctl netscaler | grep 'sysid\|serial\|descr\|num_pe_running'"
	shell df
	show license
	shell /bin/sh -c "grep 'avail memory' /var/nslog/dmesg*"; stat system -detail | grep 'Power supply'
	shell /bin/sh -c "ipmitool sel elist | tail -10"
	shell /bin/sh -c "ipmitool sensor list | grep 'PS_'"
	shell ipmitool mc info
	