###### processes
```bash
# finding processes
# list all processes
ps aux
# find process ids for processes named [name]
pgrep [name]
# find process ids for processes containing [query] in the full path
pgrep -f [query]
# show full info for processes matching [query]
pgrep -af [query]
ps aux | grep [query] | grep -v grep
# show process tree
pstree
killing processes
kill a process by id
kill [id]
force kill
kill -9 [id]
# find a process by name and kill it
pkill java
kill all processes with the specified name
killall java
# find a process containing a particular string (in name or argument list) and kill it
pkill -f activemq
ps -ef | grep [query] | grep -v grep | awk '{print $2}' | xargs kill
kill most recently started java process
pkill -n java
# cpu usage
# show cpu usage of currently running processes
htop
top
# memory usage
sort all processes on memory and show largest 25
ps -eo rss,size,user,pid,command | sort -k1 -rn | head -25
ps aux --sort -rss | head -n 25
# memory estimation per process in MB
ps h -eo rss,pid,command | cut -c 1-200 | sort -n | python -c '
import sys; 
for line in sys.stdin:
    split = line.strip().split(" ", 1);
    print(str(float(split[0]) / 1024) + split[1].strip()); 
'
# memory estimation for a group of processes in MB using filter (e.g. postgres or java)
ps h -eo rss,command | grep [filter] | awk '{ sum += $1 } END { print sum / 1024 }'
# accurate and detailed memory usage information on a single process
sudo pmap -d [pid]
# accurate memory usage per application (not process) based on dividing shared pages
smem
# Monitoring
log cpu usage at regular intervals
sar 1 1000 > cpu.log
```
