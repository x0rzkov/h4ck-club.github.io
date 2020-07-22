###### cronie
```
Min  Hour Day  Mon  Weekday 	command to be executed
*    *    *    *    *   	
┬    ┬    ┬    ┬    ┬
│    │    │    │    └─   	Weekday  (0=Sun .. 6=Sat)
│    │    │    └──────   	Month    (1..12)
│    │    └───────────   	Day      (1..31)
│    └────────────────   	Hour     (0..23)
└─────────────────────   	Minute   (0..59)

0 */4 * * * /home/untitled/rsyncer > /tmp/rsyncer.log


WTF?! My cronjob doesn't run?!

Here's a checklist guide to debug not running cronjobs:

Is the Cron daemon running?
Run ps ax | grep cron and look for cron.
Debian: service cron start or service cron restart
Is cron working?
* * * * * /bin/echo "cron works" >> /tmp/file
Syntax correct? See below.
You obviously need to have write access to the file you are redirecting the output to. 
A unique file name in /tmp which does not currently exist should always be writable.
Is the command working standalone?
Check if the script has an error, by doing a dry run on the CLI
when testing your command, test as the user whose crontab you are editing, which might not be your login or root
Can cron run your job?
Check /var/log/cron.log or /var/log/messages for errors.
Ubuntu: grep CRON /var/log/syslog
Redhat: /var/log/cron
Check permissions
set executable flag on the command: chmod +x /var/www/app/cron/do-stuff.php
if you redirect the output of your command to a file, verify you have permission to write to that file/directory
Check paths
check she-bangs / hashbangs line
do not rely on environment variables like PATH, as their value will likely not be the same under cron as under an interactive session
Don't suppress output while debugging
commonly used is this suppression: 30 1 * * * command > /dev/null 2>&1
re-enable the standard output or standard error message output
Still not working? Yikes!

Raise the cron debug level
Debian
in /etc/default/cron
set EXTRA_OPTS="-L 2"
service cron restart
tail -f /var/log/syslog to see the scripts executed
Ubuntu
in /etc/rsyslog.d/50-default.conf
add or comment out line cron.crit /var/log/cron.log
reload logger sudo /etc/init.d/rsyslog reload
re-run cron
open /var/log/cron.log and look for detailed error output
Reminder: deactivate log level, when you are done with debugging
Run cron and check log files again
Cronjob Syntax

# Minute  Hour  Day of Month      Month         Day of Week    User Command    
# (0-59) (0-23)   (1-31)    (1-12 or Jan-Dec) (0-6 or Sun-Sat)  

    0       2       *             *                *          root /usr/bin/find
This syntax is only correct for the root user. 
Regular user crontab syntax doesn't have the User field (regular users aren't allowed to run code as any other user);

# Minute  Hour  Day of Month      Month         Day of Week    Command    
# (0-59) (0-23)   (1-31)    (1-12 or Jan-Dec) (0-6 or Sun-Sat)  

    0       2       *             *                *          /usr/bin/find
Crontab Commands

crontab -l
Lists all the user's cron tasks.
crontab -e, for a specific user: crontab -e -u agentsmith
Starts edit session of your crontab file.
When you exit the editor, the modified crontab is installed automatically.
crontab -r
Removes your crontab entry from the cron spooler, but not from crontab file.
```
