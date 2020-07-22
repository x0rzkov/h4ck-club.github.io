###### config
```
# -- feeds ---------------------------------------------------------------------

auto-reload yes
reload-time 120
reload-threads 4
download-retries 4
download-timeout 10
prepopulate-query-feeds yes


# -- display -------------------------------------------------------------------

show-read-feeds no
feed-sort-order unreadarticlecount-asc

#color info default default reverse
#color listnormal_unread yellow default
#color listfocus blue default reverse bold
#color listfocus_unread blue default reverse bold

text-width 80


datetime-format "%F" 
color listnormal cyan default
#color listfocus yellow default
color listfocus white black bold
color listnormal_unread color51 default
color listfocus_unread color46 black bold
#color listfocus_unread yellow default bold
color info magenta default bold
color article cyan default
#browser "firefox %u" 
#color info white cyan bold
#html-renderer "w3m -dump -T text/html" 


# -- navigation ----------------------------------------------------------------

goto-next-feed no

browser "open -g -a 'google-chrome-stable' %u"

bind-key j down feedlist
bind-key k up feedlist
bind-key j next articlelist
bind-key k prev articlelist
bind-key J next-feed articlelist
bind-key K prev-feed articlelist
bind-key j down article
bind-key k up article

# misc ------------------------------------------------
confirm-exit no
cleanup-on-quit no
```
