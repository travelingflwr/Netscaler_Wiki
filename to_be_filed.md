

show hostname; shell uptime; show version; show hardware; shell /bin/sh -c "sysctl netscaler | grep 'sysid\|serial\|descr\|num_pe_running'"; shell df; show license; shell /bin/sh -c "grep 'avail memory' /var/nslog/dmesg*"; stat system -detail | grep 'Power supply'; shell /bin/sh -c "ipmitool sel elist | tail -10"; shell /bin/sh -c "ipmitool sensor list | grep 'PS_'"; shell ipmitool mc info; shell ns_hw_err.bash



for i in $(cat qagslb-vip-list.txt); do echo \\n \=\= $i \=\= \\n; grep "$i" */ns.conf | grep 'serviceName'; done > gslbvip-config.txt
for i in $(cat qagslb-vip-list.txt); do echo \\n \=\= $i \=\= \\n; grep "$i" */ns.conf | grep 'serviceName' | awk -F ' ' '{ print $6}'; done > gslbvip-config.txt

for i in $(cat qagslb-vip-list.txt); do grep "$i" */ns.conf | grep 'serviceName' | awk -F ' ' '{ print $6}'; done > gslbvip-config-work.txt

for i in $(cat gslbvip-config-work-in.txt); do grep "$i" */ns.conf | grep 'set ssl service' | grep 'tls12 DISABLED' | grep 'atl-qaern-gslb' | awk -F ' ' '{ print $4}’  ; done 

| grep 'serviceName' | awk -F ' ' '{ print $6}'; done > gslbvip-config-work.txt


for i in $(cat gslbvip-config-work-in.txt); do grep "$i" */ns.conf | grep 'set ssl service' | grep 'tls12 DISABLED' | grep 'atl-qaern-gslb' | awk -F ' ' '{ print "set ssl service", $4, "-tls11 ENABLED -tls12 ENABLED" }'; done > gslb-service-tls-change-atl-qaern.txt



for i in $(ls -d /var/nslog/newnslog*[!tar.gz]); do echo ==$i==; nsconmsg -K $i -g portalloc -d current -s csv=1 -s disptime=1 > /var/nslog/portalloc_gather_$i.csv;done ;fi


nsconmsg -K newnslog -d devname | grep 165.130.1.17

nsconmsg -K newnslog -d devname | grep 165.130.1.17

nsconmsg -K newnslog -d devname | grep 165.130.1.17

nsconmsg -j CVSERVER_NAME -s ConLb=3 -d oldconmsg

 
nsconmsg -K newnslog.177 -j VSERVER_NAME -s ConLb=2 -d oldconmsg | awk '/current time/ {print "\n"; print $0;getline; print $0} /slimit_SO/ {print $0} /S\(/ {print $0} /slimit_maxClient/ {print $0}' | more

nsconmsg -K newnslog.177 -j VSERVER_NAME -s ConLb=2 -d oldconmsg | awk '/current time/ {print "\n"; print $0;getline; print $0} /slimit_SO/ {print $0} /OFS/ {print $0} /slimit_maxClient/ {print $0}' > ofs.txt

nsconmsg -K newnslog.186 -i VSERVER_NAME -s time=21jan2017:13:00 -s ConLb=2 -d oldconmsg | more

nsconmsg93 -K newnslog.125 -g cons_si_tot_mon_time -s disptime=1 -d current | grep ':5043' | less
 
for i in newnslog*;do echo ---$i; nsconmsg93 -K $i -g cur_syshealth_ps -s disptime=2 -d current | less;done
 
nsconmsg93 -K newnslog.126 -g cardin -g CardIn -g ssl_tot_sslServerInRecords -g ssl_tot_cvm_in_decrypt_msg -s disptime=1 -s time=18Dec2015:09:25 -d current | less

nsconmsg93 -K newnslog.96 -g cardin -g CardIn -g ssl_tot_sslServerInRecords -g ssl_tot_cvm_in_decrypt_msg -s disptime=1 -d current | less

nsconmsg93 -K newnslog.96 -g TotalSession -g KeyEx -g ServerIn -g ssl_cur_q -g cardin -s disptime=1 -d current | more
 
for i in newnslog*;do echo ---$i;nsconmsg93 -K $i -s disptime=1 -g ha_cur_hasync_pcb -g ha_tot_sync_connects -d current | more;done

for i in newnslog*;do echo ---$i; nsconmsg -K $i -s disptime=1 -g cc_cpu_use -d current | more;done
 
for file in newnslog*.tar.gz; do tar -zxf $file; done
rm newnslog.*.tar.gz

Detect a nsm router reset
nsconmsg -K newnslog -s disptime=1 -g ha_cur_hasync_pcb -g ha_tot_sync_connects -d current
nsconmsg -K newnslog -d event
 
for i in newnslog*;do echo ---$i; nsconmsg93 -K $i -d event | more;done
 
for i in newnslog*;do echo ---$i;nsconmsg93 -K $i -d stats | grep ssl_cur_q | more;done

for i in newnslog*;do echo ---$i;nsconmsg93 -K $i -g mgmt_cpu_use -s disptime=1 -d current | more;done
for i in newnslog*;do echo ---$i;nsconmsg -K $i -g allnic_tot_rx_mbits -g allnic_tot_tx_mbits -s disptime=1 -d maxrate | more;done
nsconmsg -K newnslog -g mgmt_cpu_use -s disptime=1 -d current | more
 
for i in newnslog*;do echo ---$i;nsconmsg93 -K $i -d stats | grep ssl_tot_sw  | more;done
 
for i in newnslog*;do echo ---$i;nsconmsg93 -K $i -d current -g ssl_cur_q | more;done
 
for i in newnslog*;do echo ---$i;nsconmsg -K $i -s disptime=1 -g TotalSession -g KeyEx -g ServerIn -g ssl_cur_q -g cardin -s disptime=1 -d current | more;done
 
nsconmsg -g TotalSession -g KeyEx -g ServerIn -g ssl_cur_q -g cardin -s disptime=1 -d current
 
for i in newnslog*;do echo ---$i;nsconmsg93 -K $i -d event | grep -I fail | wc -l ;done
 
for i in newnslog*;nsconmsg -K $i -s disptime=1 -g si_tot_svr_busy_err -d current | more;done
 
 
nsconmsg101 -K newnslog.116 -g err -g fail -d statswt0 | grep -v "^Displaying\|^Performance\|^reltime\|Index\|^NetScaler" | awk '{ print $3 "\t" $4 }' | sort -n | grep ssl
nsconmsg -K newnslog.104 -g err -g fail -d statswt0 | grep -v "^Displaying\|^Performance\|^reltime\|Index\|^NetScaler" | awk '{ print $3 "\t" $4 }' | sort -n
 
ZOMBIE COUNTERS:
 
Explanation on counters:
pcb_tot_force_zombie_timeout – Zombie timeout is forced due to some reason (state change in this case)
tcp_tot_clt_zombie_pclose - counter indicates client side connection is being closed because of zombie.
tcp_tot_clnt_flushed_phc/tcp_tot_srvr_flushed_phc – indicates number of connections closed in Zombie by sending RST. 
pcb_tot_zombie_interleave – indicates that Zombie handler was yielded due to 1ms timeout.
pcb_warn_zombieflush_marked_lasttime – indicates number of PCBs marked for cleanup in the last invocation of zombie handler but not freed yet.
 
nsconmsg93 -K newnslog.130 -g flushed_phc -g zombie_pclose -g zombie_called -g zombieflush -g zombie_timeout -g tot_zombie_inter -s disptime=1 -s time=14Mar2016:09:15 -d current | more
 
 
Assembled by  nsconmsg -s disptime=1 -d current | grep <configured item of interest>  and seeing which counters come back:
nsconmsg -s disptime=1 -d current -g hits -g vsvr_tot_Hits -g serv_tot_Hits -G route -g ction -g busy -G trans -g rlt_ -g hc_
 
Get the MAC Addresses from newnslog:
nsconmsg  -K newnslog.104 -g nic_cur_MAC_addr -d stats
 
Command to show the number of times a MAC has moved:
nsconmsg80 -K newnslogPri -g macmove -s disptime=1 -d current | more
 
Show timestamp of file:
nsconmsg -K newnslog.104 -d setime
 
Command to show a list of Netscaler devices:
nsconmsg -d devname
 
Command to show live NIC stats:
nsconmsg -s nsdebug_pe=1 -d oldconmsg
 
Command to show NIC dropped packets:
nsconmsg -K newnslog -g nic_err_dropped_pkts  -s disptime=1 -d current
 
Get time period from newnslog and copy information to log file:
nsconmsg -K newnslog –k newlog.log -s time=17jan2014:06:10 -T 180 -d copy
 
This command will show you the total SNMP requests and the total request dropped. 
nsconmsg -g snmp_tot_traps -g snmp_err_req_dropped -d current
 
Command to display errors for all non-zero counters:
nsconmsg -g err -d statswt0
 
Command to display all current TCP Client connections based on time:
nsconmsg -K newnslog -g tcp_cur_ClientConnEst -s time=21Sep2007:11:00 -d current

Command to display NIC bandwidth based on time:
nsconmsg -K newnslog -g mbits -s time=20Sep2007:14:14 -d current
 
Command to display any port allocation failures:
nsconmsg -K newnslog -g portalloc -s time=20Sep2007:13:05 -s disptime=1 -d current
nsconmsg -K newnslog -g portalloc -s disptime=1 -d current
 
 
Command to display HA errors:
nsconmsg -K newnslog -g ha_err_sw_monitor_fail -d statswt0
nsconmsg -K newnslog.166 -g ha_err_sw_monitor_fail -d statswt0
 
 
Command to display HA packets:
nsconmsg -K newnslog -g ha_tot_pkt -d current | more
 
Command to show server side errors during a connection attempt:
nsconmsg -K newnslog.103 -s disptime=1 -g err -d current | grep 'server'
 
Command to display cpu usage above 20%:
nsconmsg -K newnslog  -s totalcount=200  -g cpu_use -d current
nsconmsg -K newnslog.103 -s disptime=1 -s totalcount=800  -g mgmt_cpu_use -d current
 
Command to show LB specifics for a particular VIP and service as defined by IP with egrep:
 nsconmsg -K newnslog -s ConLb=2  -d oldconmsg | egrep -A 2 '10.192.8.187|10.192.8.146'
 
Command to show LB specifics for a particular VIP and service as defined by IP with awk:
nsconmsg -K newnslog -s ConLb=2 -d oldconmsg | awk '/current time/ {print $0;getline; print $0} /10.53.24.112|10.53.24.113|10.53.25.76/ {print $0;getline; print $0;getline; print$0}'
 
nsconmsg -s ConLb=2 -d oldconmsg | awk '/current time/ {print $0;getline; print $0} /10.233.30.93/ {print $0;getline; print $0;getline; print$0;getline; print$0}'
 
Command to show LB specifics for a VIP and services using awk and regex:
nsconmsg93 -K newnslog -s ConLb=2 -d oldconmsg | awk '/^current time/ {print "\n"$0;getline;print $0} /VIP\(54.239.28.248:443/ {print $0;getline;print $0;getline;print$0} /S\(10.0.2.1[0-2][0-9]:8543/ {print $0;getline;print $0;getline;print$0}' | more
 
nsconmsg93 -K newnslog -s ConLb=2 -d oldconmsg | awk '/^current time/ {print "\n"$0;getline;print $0} /VIP\(54.239.28.248:443/ {print $0;getline;print $0;getline;print$0} /S\(10.91.81.125:8543/ {print $0;getline;print $0;getline;print$0}' | more
 
Command to show NIC details:
nsconmsg -K newnslog -g nic -d current | more
nsconmsg -K newnslog.166 -g nic -d current | grep "nic_cur_link_downtime" | more
nsconmsg -K newnslog.166 -g nic_cur_link_downtime -d current | more
nsconmsg -K newnslog -g nic_cur_link_downtime -d current | more
 
nsconmsg -K newnslog.130 -s ConLb=2 -d oldconmsg | awk '/current time/ {print $0;getline; print $0} /10.208.128.44:8513/ {print $0;getline; print $0;getline; print$0;getline; print$0}' | more
 
 
Command to view open connections for a specific vserver:
nsconmsg –j server_NSSVC_HTTP_192.168.10.36 –d current | grep si_cur_ConnOpenEst
 
Command to view LB statistics from a point in time:
nsconmsg -K newnslog -s time=20Sep2006:15:56 -s ConLb=2 -d oldconmsg
 
Command to display memory usage:
nsconmsg -s ConMEM=1 -d oldconmsg
 
Command to display free memory:
nsconmsg -K newnslog -g mem_cur_freesize_actual -d current
 
Command to restart nsconmsg logging.  Note time is in seconds (48 hours):
/netscaler/nsconmsg -k /var/nslog/newnslog -T 172800 &
 
Command to display debug information SYN counters/Reuse/PCB/NATPCB:
nsconmsg -K newnslog.103 -s ConDebug=2 -d oldconmsg
 
Command to show client/server connections and HTTP requests/responses:
nsconmsg -K newnslog -s ConDebug=1 -d oldconmsg
 
Command to show monitor statistics:
nsconmsg -K newnslog –s ConMon=x -d oldconmsg
 
Command gives SSL stats for front-end connections:
nsconmsg -K newnslog -s ConSSL=1 -d oldconmsg
 
Command gives SSL stats for back-end connections:
nsconmsg -K newnslog -s ConSSL=2 -d oldconmsg
 
Command gives SSL stats for both front-end and back-end connections:
nsconmsg -K newnslog -s ConSSL=3 -d oldconmsg
 
Command to display Content Switching stats:
nsconmsg -K newnslog –s ConCSW=1 -d oldconmsg
 
Command to display Compression stats:
nsconmsg -K newnslog –s ConCMP=x -d oldconmsg
 
Command to display Integrated Caching stats:
nsconmsg -K newnslog -s ConIC=1 -d oldconmsg
 
Command to check for HA failovers:
nsconmsg -k newnslog -g ha_cur_master_state -d stats
 
Command to check for corrupt HA packets:
nsconmsg -K newnslog -g udp_err_badchecksums -d current
 
Command to check for all HTTP counters for stats and current:
nsconmsg -K newnslog –g http_tot -d stats -d current
 
Command to view current memory allocation:
nsconmsg -g mem_cur_allocsize -d statswt0
 
Command to display failed monitor probes and failed probes due to PCB:
nsconmsg –g monitor_tot -d stats –d current
 
Command to show TX NIC packets and ARP totals for a defined time slice:
nsconmsg -K newnslog -s disptime=1 -s time=08JUN2006:13:40:00 -g nic_tot_tx_packets -g arp_tot -d current | more
 
Command to show RX NIC packets and ARP totals for a defined time slice:
nsconmsg -K newnslog -s disptime=1 -s time=08JUN2006:13:40:00 -g nic_tot_rx_packets -g arp_tot -d current | more
 
Command to show start-up state:
nsconmsg -d stats | grep starttime
 
Command to show last transition time:
nsconmsg -d stats | grep sys_cur_last_transition_time
 
Command to show log buffer overruns:
nsconmsg -K newnslog -g tcp_tot_log_bufOverruncount -d stats
 
Command to show AppFW used NSBs:
nsconmsg -K newnslog -g sys_cur_coproc_nsbs -d stats
 
Command to see dropped HTTP requests in AppFW:
nsconmsg -K newnslog -g as_req_hdrs_no_host_error -d (stats|current)
 
Command to see packets sent out over a disabled or error disabled NIC:
nsconmsg -K newnslog -g net_err_disablednic_txpkts -d (stats|current)
 
Command to show how long a system has been Primary:
nsconmsg -d statswt0 | grep sys_cur_activemode_duration
 
Command to show all the AppFW counters:
nsconmsg80 -K newnslog -d stats | awk '$4 ~ /^as_/ {print $4}'  | more
 
Command to show FreeBSD fork system call failures:
nsconmsg -K newnslog -g fbsd_err_forkfail_syslimit -d stats
 
Command to show Netscaler Kernel AppFW dropped messages:
nsconmsg -K newnslog -g as_num_learn_dropped_msgs -d stats
 
Command to show CRL memory limit errors:
nsconmsg –K newnslog -g ssl_err_crl_memlim -d current
 
Command to loop through all AppFW Counters and write stats to a file:
 for counter in $(nsconmsg80 -K b.newnslog.27 -d statswt0 | awk '$4 ~ /^as_/ {print $4}'| sort -u); do nsconmsg80 -K b.newnslog.27 -g ${counter} -s time=18OCT2008:03:15:00 -d statswt0 | nawk "/^reltime|^Index|$counter/"'{print $0}'>> b.newnslog.27_${counter}.log; done
 
Command to look for SYN Cookie Error Resets (SYN Cookie expires after 120s):
nsconmsg -K newnslog -f tcp_err_cookie_signature_reject -f tcp_err_stray_packets -s disptime=1 -d current
 
Command to show disk size and usage statistics:
nsconmsg -g cur_syshealth_disk -d stats
 
Command to show system uptime duration since start:
nsconmsg -K newnslog.64 -g sys_cur_duration_sincestart -s disptime=1 -d past
 
Command to check SSL CRL memory limit errors:
nsconmsg –K newnslog -g ssl_err_crl_memlim -d current
 
Command to display GSLB domain statistics (Doesn't work with large number of objects):
nsconmsg -K newnslog -g dnsrec_tot_queries -d stats
 
Command to display the TCP WTMOFF counter for connections with Authorization header that use private persistence:
nsconmsg -K newnslog -g tcp_tot_wtmoff_force_persist -d stats
 
Command to get connection distribution information from newnslog, match current time, line separator, 1st service IP (to get the VIP since it's 0.0.0.0), and finally to print the 2 service IP lines:
nsconmsg80 -K nc-sils-ns-ign01-newnslog -s ConLb=1 -d distrconmsg | awk '/^current|^-/ {print $0} /162.111.113.221/ {print ll} {ll = $0} /162.111.113.221|162.111.57.141/ {print $0}'
 
Command to print the VIP (3 lines above) from newnslog, match current time, line separator, 1st service IP (to get the VIP since it's 0.0.0.0), and finally to print the 2 service IP lines:
 nsconmsg80 -K newnslog.35 -s ConLb=2 -d oldconmsg | awk '/^current|^-/ {print $0} /162.111.113.221/ {print a[NR%3] RS a[(NR+1)%3] RS a[(NR+2)%3]} {a[NR%3]=$0} /162.111.113.221|162.111.57.141/ {print $0}' | more
 
Command to help determine HW model by CPU and Memory information:
nsconmsg -K newnslog -d stats | egrep -i 'sys_(cpu|nic|mem)'
 
Commands to show Global Session table information (Max is 250K):
nsconmsg -K newnslog -g tcp_max_session_entry -d stats
nsconmsg -K newnslog -g tcp_cur_session_srcip -d current
 
Commands to show current system health:
nsconmsg81 -K newnslog.64 -g cur_syshealth -s disptime=1 -d past | more
 
Commands to show current system health (Temperature only):
nsconmsg81 -K newnslog.64 -g cur_syshealth_t -s disptime=1 -d past | more
 
Command to show the current HA master state:
nsconmsg81 -K newnslog.52 -f ha_cur_master_state -s disptime=1 -d current
 
Command to show Client and BE (Back-end) SSL/TLS renegotiation sessions:
nsconmsg -K newnslog -s ConSSL=3 -d oldconmsg | nawk '/^current time/ {print "\r";print $0} /^Sessions/ {print $0;getline;print $0} /^BE Sessions/ {print $0}' | more
 
Command to show the enabled features:
nsconmsg -g sys_cur_feature -d stats
 
Command to show the enabled modes in the newnslog:
nsconmsg -g sys_cur_swfeature -d stats
 
Command to show if the NS is returning a 404 error:
nsconmsg -K newnslog -g csw_err_404 -d stats
 
Command to show the 500 (Server Busy) error messages:
 nsconmsg -K newnslog -g si_tot_svr_busy_err -s disptime=1 -d stats
 
Commands to show the Cavium SSL card inQ counters (These increment when the chip is saturated):
nsconmsg -K newnslog -g ssl_tot_sslInfo_cardinKeyQ  -d stats   (Total SPCBs waiting in cardinQ for key operations)
nsconmsg -K newnslog -g ssl_tot_sslInfo_cardinBlkQ -d stats    (Total SPCBs waiting in cardinQ for bulk operations)
nsconmsg -K newnslog -g ssl_tot_sslInfo_nsCardInQCount -d stats  (Total SPCBs waiting in cardinQ)
 
Commands to check for HA peer Master conflicts and duplicate IPs:
nsconmsg -K newnslog -g ha_err_master_dispute -d current
nsconmsg -K newnslog -g arp_err_ipaddr_conflicts -d current
 
Command to determine if an MPX platform is doing rate limiting:
Nsconmsg101 –K newnslog.114 -d stats | grep nic_err_rl_pkt_drop
 
Useful nic counters to help determine a problem:
nsconmsg -K newnslog -d stats
net_cur_congested
nic_err_rx_nobufs
nic_err_rx_fifo
nic_err_tx_overflow
nic_cur_txqlen
 
Command to view the number of HTTP GETs and POSTs (System only):
nsconmsg81 -K newnslog.93 -f http_tot_Gets -f http_tot_Posts -s disptime=1 -d current | more
 
User monitor counters to help determine a problem:
nsconmsg -K newnslog -d stats
monitor_err_user_cpu_fail
monitor_err_user_file_limit
monitor_err_user_proc_limit
 
Command to show the minimum memory usage and time stamp:
nsconmsg80 -K newnslog
BSD_6.3 [60575689] $ for a in $(ls newnslog.*); do echo "======================$a========================"; nsconmsg91 -K $a -d setime; echo ""; done
======================newnslog.77========================
Displaying start and end time information
NetScaler V20 Performance Data
NetScaler NS9.1: Build 99.8.cl, Date: Nov  8 2009, 12:20:21
 
start time Mon Jun 13 23:39:20 2011
end   time Wed Jun 15 23:39:20 2011
total duration     02.00:00:00
data size 275,849,216 bytes
 
======================newnslog.78========================
Displaying start and end time information
NetScaler V20 Performance Data
NetScaler NS9.1: Build 99.8.cl, Date: Nov  8 2009, 12:20:21
 
start time Wed Jun 15 23:39:20 2011
end   time Fri Jun 17 23:39:27 2011
total duration     02.00:00:07
data size 275,865,600 bytes
 
======================newnslog.79========================
Displaying start and end time information
NetScaler V20 Performance Data
NetScaler NS9.1: Build 99.8.cl, Date: Nov  8 2009, 12:20:21
 
start time Fri Jun 17 23:39:27 2011
end   time Sun Jun 19 23:39:34 2011
total duration     02.00:00:07
data size 275,857,408 bytes
 
======================newnslog.80========================
Displaying start and end time information
NetScaler V20 Performance Data
NetScaler NS9.1: Build 99.8.cl, Date: Nov  8 2009, 12:20:21
 
start time Sun Jun 19 23:39:34 2011
end   time Tue Jun 21 23:39:41 2011
total duration     02.00:00:07
data size 252,051,456 bytes
 
======================newnslog.81========================
Displaying start and end time information
NetScaler V20 Performance Data
NetScaler NS9.1: Build 99.8.cl, Date: Nov  8 2009, 12:20:21
 
start time Tue Jun 21 23:39:41 2011
end   time Thu Jun 23 23:39:48 2011
total duration     02.00:00:07
data size 248,651,776 bytes
 
======================newnslog.82========================
Displaying start and end time information
NetScaler V20 Performance Data
NetScaler NS9.1: Build 99.8.cl, Date: Nov  8 2009, 12:20:21
 
start time Thu Jun 23 23:39:48 2011
end   time Sat Jun 25 23:39:51 2011
total duration     02.00:00:03
data size 248,848,384 bytes
 
======================newnslog.83========================
Displaying start and end time information
NetScaler V20 Performance Data
NetScaler NS9.1: Build 99.8.cl, Date: Nov  8 2009, 12:20:21
 
start time Sat Jun 25 23:39:52 2011
end   time Mon Jun 27 23:39:58 2011
total duration     02.00:00:06
data size 248,848,384 bytes
 
======================newnslog.84========================
Displaying start and end time information
NetScaler V20 Performance Data
NetScaler NS9.1: Build 99.8.cl, Date: Nov  8 2009, 12:20:21
 
start time Mon Jun 27 23:39:59 2011
end   time Wed Jun 29 23:39:59 2011
total duration     02.00:00:00
data size 248,840,192 bytes
 -d minvalue
 
Command to determine if the AppFW is under memory pressure:
nsconmsg81 -K newnslog -g as_under_memory_pressure -s disptime=1 -d current
 
Command to view Chunked request and invalid body requests starting at a specific time:
 nsconmsg90 -K newnslog -f master_cpu_use -f http_tot_ChunkedRequests -f http_err_InvalidBodyRequests -s disptime=1 -s time=09JUL2010:15:20 -d current | more
 
Command to view LB statistics about an individual vserver at a specific time:
nsconmsg90 -K newnslog.75 -i www.cheaptickets.com.80_fwd -s time=05jul2010:22:07 -s ConLb=2 -d oldconmsg | more
 
Command to view the Reuse Pool counter for each service:
nsconmsg81 -K newnslog -g si_cur_ReusePool -d current
 
Command to check free NSBs per PPE:
nsconmsg -s nsppeid=3 -g sys_cur_nsb -g sys_cur_freensbs -s disptime=1 -d current | more
 
Command to check for NIC errors and stalls:
nsconmsg92 -K newnslog.57 -g nic_err_link_hangs -g nic_err_link_reinits -g nic_err_link_tx_stalls -s disptime=1 -d current
 
Command to check netio, ha packets, and CPU per PE:
nsconmsg92 -K newnslog.48 -g ha_tot_pkt -g ha_cur_master_state  -g netio -g cpu_use -s disptime=1 -s pedist=1  -d current
 
Command to look at a specific time in newnslog and print data if the 3rd columns matches an IF statement:
nsconmsg91 -K newnslog -s disptime=1 -s time=28JAN2011:07:21 -d current | nawk '/Jan 28 07:22/ {if($3 == 465) print $0}'
 
Command to look for NIC errors:
nsconmsg92 -K newnslog -d stats | egrep 'net_cur_congested|nic_err_rx_nobufs|nic_err_rx_fifo|nic_err_tx_overflow|nic_err_rx_overflow|nic_cur_txqlen|nic_err_link_hangs|nic_err_link_reinits|nic_err_link_tx_stalls|netio'
 
Command to check Power Supply failures:
nsconmsg90 -K newnslog.35 -g cur_syshealth_ps -s disptime=1 -d current
 
Command to collect useful data on the NIC per PE:
nsconmsg92 -K newnslog.16 -g nic_err_rx -g Xoff -g Xon -g nic_tot_rx_mbits -g cpu_use -g nic_err_ifInDiscards -s pedist=1 -s disptime=1 -d current
 
Command to loop through the newnslogs and generate a list of CPU over 80% for each:
for list in $(ls newnslog*); do
nsconmsg91 -K $list -g cpu_use -s totalcount=800 -s disptime=1 -d current;
echo "";
echo "---------------------------------------------------------------";
echo "";
done                                      
 
Command to loop through the newnslogs and generate a file for all Server Busy 500 errors:
for i in $(ls newnslog*); do
echo "Parsing SVR Busy for $i";
nsconmsg81 -K $i -g si_tot_svr_busy_err -s disptime=1 -d current >> ${i}_svc_busy.log;
echo "Done with $i";
done
 
Command to display RX NIC errors and remove the allnic duplication:
nsconmsg90 -K newnslog -F allnic_tot_rx_mbits -g nic_err_rx -g nic_tot_rx_mbits -g Xoff -s disptime=1 -d current | more
 
Command to display the SourceIP persistence and cache per core:
nsconmsg92 -s pedist=1 -K newnslog -g tcp_cur_cached_session_inuse -g lb_cur_owned_sessions -g tcp_cur_session  -d statswt0
 
Command to display HA sync information (API failures on Secondary):
nsconmsg92 -K newnslog -f ha_tot_cfgsyncs -f ha_tot_cfgsync_ioctls -f ha_tot_sync_connects -f ha_err_prop_mem_fail -f ha_err_prop_timeout -f ha_err_sync_failure -f ha_err_no_sync_pcb -f ha_cur_sync_time -f ha_dr_cur_sync_time -f ha_cur_last_sync_failure -f ha_cur_lastsync_duration -s disptime=1 -d current | more
 
Command to match and print the timestamp and monitor from the ConMON output.  The second match will include the next 13 lines:
nsconmsg92 -K newnslog.22 -s ConMon=3 -s disptime=1 -s time=17OCT2011:15:46 -d oldconmsg | nawk '/current time|^-/ {print} /Monitor_RSA-AA-Monitor-Radius$/ {c=14} c-->0' >> newnslog.22_RSA_mon.log
 
Command used to skip the first 4 columns and print all remaining columns from input:
nsconmsg92 -K newnslog.25 -d event | egrep 'www.orbitz.com.443_cs_contentcache|www.orbitzforbusiness.net.80_cs_contentcache|www.orbitzforbusiness.net.443_cs_contentcache|www.cheaptickets.com.80_cs_contentcache|www.cheaptickets.com.443_cs_contentcache|www.revresda.com.80_cs_contentcache|www.revresda.com.443_cs_contentcache' | awk '/0.0.0.0:0/ {for (i=3;i<=NF;i++) { printf "%s ",$i};printf "\n"}'
 
nsconmsg command to view user defined logs to newnslog:
nsconmsg -K newnslog.22 -d logfromnfw
 
Command to display the MAC addresses known by the system.  For HA heartbeats, the counter nic_cur_ha_MAC should be valid for each enabled interface:
nsconmsg -K /var/nslog/newnslog -g MAC -d stats
 
Command to match on VIP and print the next 19 lines of the match, and append to a logfile:
nsconmsg93 -K newnslog -s ConLb=2 -d oldconmsg | nawk '/current time|-/ {print $0} /10.56.56.12:21/ {print;n=19;next}n{print;n--}' >> newnslog_conlb.log
 
Command to view the last counter value from a newnslog file (9.3 and newer):
nsconmsg -K /var/nslog/newnslog -g curdynamic_serverinfo -s disptime=1 -d finalstats
 
Command to look for curdynamic_serverinfo and kill the process after 5 seconds:
nsconmsg -K /var/nslog/newnslog -g curdynamic_serverinfo -s disptime=1 -d current | tail -1 & sleep 5; kill $!
 
Command to look for monitor stats, print current time, and print 8 lines after monitor match:
BSD_6.3 [nslog] $ nsconmsg93 -K newnslog -s ConMon=3 -d oldconmsg | nawk '/current time/ {print $0} /172.29.189.217:3306/ {print;n=8;next}n{print;n--}' > mysql_mon.log
 
Command to look at total ICA users and ICA license failures:
BSD_6.3 [nslog] $ nsconmsg92 -K newnslog.81 -g ica_license -g total_ica_connections -s disptime=1 -d current | more
 
Command to look at VPN/ICA user details:
nsconmsg -K newnslog -g curAaaUsersPerVserver -g si_curaaausers -g maxsslvpnusers -g svpn_lic_failed -g svpn_maxusers_lic_failed -g ica_license_failure -g tot_lic_shared_ica_vpn -g total_ica_connections -s disptime-1 -d current | more
 
Command to get the setime from new ncore newnslog files in directories and to exclude the tar.gz files:
for i in $(ls -d newnslog.*[!tar.gz]); do echo "==================$i===================";nsconmsg93 -K $i -d setime; echo ""; done
 
 
pretty:
nsconmsg -K newnslog.44 -s ConLb=1 -s time=25APR2013:04:30 -d oldconmsg | nawk '/current time|^----/ {print $0} /^VIP/ {print $1}' >> newnslog.44_vip_status.log
 
nsconmsg93 -K newnslog -g ssl_tot_sslError_FatalAlertRecdCount -g ssl_tot_sslError_FatalAlertSentCount -g ssl_tot_w_dec_bytes -g ssl_tot_sw_enc_bytes -s csv=1 -s disptime=1 -d current > SSL_errors.csv
 
for i in newnslog* ; do echo ---$i ; nsconmsg -K $i -d stats | grep ssl_cur_sslInfo_nsCardInQCount | more; done
 
for i in newnslog* ; do echo ---$i ; nsconmsg -K $i -s disptime=1 -g nic_err -d current | more; done


nsconmsg -K newnslog -g ssl -d past
