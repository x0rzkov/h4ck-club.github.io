###### shared session
```bash
tmux -S /opt/tmux/socket new-session -s xCC	# 1st user
tmux new -s meowmeow -t xCC 			# 2nd user
```
###### re attach
```bash
tmux -S /opt/tmux/socket a -t xCC		# 1st user
tmux -S /opt/tmux/socket a -t meowmeow		# 2nd user
```
###### cheat
```bash
# start new:

tmux
# start new with session name:

tmux new -s myname
# attach:

tmux a  #  (or at, or attach)
# attach to named:

tmux a -t myname
# list sessions:

tmux ls
# kill session:

tmux kill-session -t myname
# Kill all the tmux sessions:

# tmux ls | grep : | cut -d. -f1 | awk '{print substr($1, 0, length($1)-1)}' | xargs kill
# In tmux, hit the prefix ctrl+b (my modified prefix is ctrl+a) and then:

# Sessions
:new<CR>  # new session
s  # list sessions
$  # name session

# Windows (tabs)
c  # create window
w  # list windows
n  # next window
p  # previous window
f  # find window
,  # name window
&  # kill window
# # Panes (splits)
%  # vertical split

o  swap panes
q  show pane numbers
x  kill pane
+  break pane into window (e.g. to select text by mouse to copy)
-  restore pane from window
⍽  space - toggle between layouts
<prefix> q (Show pane numbers, when the numbers show up type the key to goto that pane)
<prefix> { (Move the current pane left)
<prefix> } (Move the current pane right)
<prefix> z toggle pane zoom

# Sync Panes
# You can do this by switching to the appropriate window, typing your Tmux prefix (commonly Ctrl-B or Ctrl-A) and then a colon to bring up a Tmux command line, and typing:
:setw synchronize-panes

# You can optionally add on or off to specify which state you want; otherwise the option is simply toggled. This option is specific to one window, so it won’t change the way your other sessions or windows operate. When you’re done, toggle it off again by repeating the command. tip source
# Resizing Panes
# You can also resize panes if you don’t like the layout defaults. I personally rarely need to do this, though it’s handy to know how. Here is the basic syntax to resize panes:

PREFIX : resize-pane -D (Resizes the current pane down)
PREFIX : resize-pane -U (Resizes the current pane upward)
PREFIX : resize-pane -L (Resizes the current pane left)
PREFIX : resize-pane -R (Resizes the current pane right)
PREFIX : resize-pane -D 20 (Resizes the current pane down by 20 cells)
PREFIX : resize-pane -U 20 (Resizes the current pane upward by 20 cells)
PREFIX : resize-pane -L 20 (Resizes the current pane left by 20 cells)
PREFIX : resize-pane -R 20 (Resizes the current pane right by 20 cells)
PREFIX : resize-pane -t 2 20 (Resizes the pane with the id of 2 down by 20 cells)
PREFIX : resize-pane -t -L 20 (Resizes the pane with the id of 2 left by 20 cells)
# Copy mode:
# Pressing PREFIX [ places us in Copy mode. We can then use our movement keys to move our cursor around the screen. By default, the arrow keys work. we set our configuration file to use Vim keys for moving between windows and resizing panes so we wouldn’t have to take our hands off the home row. tmux has a vi mode for working with the buffer as well. To enable it, add this line to .tmux.conf:
setw -g mode-keys vi

# With this option set, we can use h, j, k, and l to move around our buffer.
# To get out of Copy mode, we just press the ENTER key. Moving around one character at a time isn’t very efficient. Since we enabled vi mode, we can also use some other visible shortcuts to move around the buffer.
# For example, we can use "w" to jump to the next word and "b" to jump back one word. And we can use "f", followed by any character, to jump to that character on the same line, and "F" to jump backwards on the line.

#  Function                vi             emacs
   Back to indentation     ^              M-m
   Clear selection         Escape         C-g
   Copy selection          Enter          M-w
   Cursor down             j              Down
   Cursor left             h              Left
   Cursor right            l              Right
   Cursor to bottom line   L
   Cursor to middle line   M              M-r
   Cursor to top line      H              M-R
   Cursor up               k              Up
   Delete entire line      d              C-u
   Delete to end of line   D              C-k
   End of line             $              C-e
   Goto line               :              g
   Half page down          C-d            M-Down
   Half page up            C-u            M-Up
   Next page               C-f            Page down
   Next word               w              M-f
   Paste buffer            p              C-y
   Previous page           C-b            Page up
   Previous word           b              M-b
   Quit mode               q              Escape
   Scroll down             C-Down or J    C-Down
   Scroll up               C-Up or K      C-Up
   Search again            n              n
   Search backward         ?              C-r
   Search forward          /              C-s
   Start of line           0              C-a
   Start selection         Space          C-Space
   Transpose chars                        C-t
   
# Misc
d  # detach
t  # big clock
?  # list shortcuts
:  # prompt

# Configurations Options:
# Mouse support - set to on if you want to use the mouse
* setw -g mode-mouse off
* set -g mouse-select-pane off
* set -g mouse-resize-pane off
* set -g mouse-select-window off

# Set the default terminal mode to 256color mode
set -g default-terminal "screen-256color"

# enable activity alerts
setw -g monitor-activity on
set -g visual-activity on

# Center the window list
set -g status-justify centre

# Maximize and restore a pane
unbind Up bind Up new-window -d -n tmp \; swap-pane -s tmp.1 \; select-window -t tmp
unbind Down
bind Down last-window \; swap-pane -s tmp.1 \; kill-window -t tmp
```
</pre>
###### config
<pre class ="prettyprint lang-bash Doxy">
```bash
set-option -g default-shell /usr/bin/zsh
set -g history-file ~/.tmux_history
set -g mouse on
set-option -g status-interval 1
#set -g history-limit 50000
set-option -g history-limit 50000
#set-option -g status-justify "left"
set -g status-justify centre
set -g status-left-length 75
set -g status-right-length 175
#set -g status-left-length 85
#set -g default-terminal "xterm-256color"
set -g default-terminal "tmux-256color"
#set-option -ga terminal-overrides ",xterm*:Tc"
set -sg escape-time 0
#set-option -ga terminal-overrides ",xterm-terminator:Tc"
#set-option -ga terminal-overrides ",*256*:Tc"
#keybind
unbind C-b
set -g prefix C-a
bind C-a send-prefix
bind - split-window -v -c "#{pane_current_path}"
bind \ split-window -h -c "#{pane_current_path}"

#maximize & restore panes
# Pane resizing 
bind-key -r H resize-pane -L "5"
bind-key -r L resize-pane -R "5"
bind-key -r J resize-pane -D "5"
bind-key -r K resize-pane -U "5"
# 
bind z run tmux-url-select.pl
set-option -g allow-rename off
set -g visual-activity on

## Navigate panes like Vim.
setw -g mode-keys vi
bind h select-pane -L
bind j select-pane -D
bind k select-pane -U
bind l select-pane -R
bind-key -r C-l select-window -t :+
bind-key -r C-h select-window -t :-
bind-key -T copy-mode-vi 'v' send -X begin-selection
bind-key -T copy-mode-vi 'V' send -X select-line
bind-key -T copy-mode-vi 'r' send -X rectangle-toggle
bind-key -T copy-mode-vi 'y' send -X copy-pipe-and-cancel "xclip -in -selection clipboard"
bind-key P run "xsel -o | tmux load-buffer - ; tmux paste-buffer"
setw -g xterm-keys on

# Smart pane switching with awareness of Vim splits.
is_vim="ps -o state= -o comm= -t '#{pane_tty}' \
    | grep -iqE '^[^TXZ ]+ +(\\S+\\/)?g?(view|n?vim?x?)(diff)?$'"
bind-key -n C-h if-shell "$is_vim" "send-keys C-h"  "select-pane -L"
bind-key -n C-j if-shell "$is_vim" "send-keys C-j"  "select-pane -D"
bind-key -n C-k if-shell "$is_vim" "send-keys C-k"  "select-pane -U"
bind-key -n C-l if-shell "$is_vim" "send-keys C-l"  "select-pane -R"
bind-key -n C-\ if-shell "$is_vim" "send-keys C-\\" "select-pane -l"
bind-key -T copy-mode-vi C-h select-pane -L
bind-key -T copy-mode-vi C-j select-pane -D
bind-key -T copy-mode-vi C-k select-pane -U
bind-key -T copy-mode-vi C-l select-pane -R
bind-key -T copy-mode-vi C-\ select-pane -l

### set some pretty colors
#set -g mode-style pane-active-border-fg colour235 #base01
#set -g pane-active-border-style fg=red

set -g pane-border-style fg=green
set -g base-index 0
setw -g pane-base-index 0
#set -g status-bg default #set for transparent background
set-option -g set-titles on
#set-option -g set-titles-string "#W"

set-option -g set-titles-string '#T #{pane_current_path}' # window number,program name,active (or not)
#set-option -g set-titles-string " #W #F #T #{pane_current_command}"
#  modes
setw -g clock-mode-colour colour5
#setw -g mode-attr bold
#setw -g mode-fg colour255
#setw -g mode-bg colour33
#set -g mode-style fg=yellow,bg=colour45,blink,bold
set -g mode-style fg=black,bg=colour45,bold

# PANES
set -g pane-border-style bg=default
set -g pane-border-style fg=colour236
set -g pane-active-border-style bg=default
set -g pane-active-border-style fg=colour237
set -g display-panes-colour black
set -g display-panes-active-colour brightblack

# statusbar
#set -g status-position bottom
#set -g status-justify left
set -g status-bg default
set -g status-fg colour137
#set -g status-attr dim
#set -g status-left ''

set-window-option -g window-status-style bg=default
setw -g window-status-current-style fg=colour1
setw -g window-status-current-style bg=default
#setw -g window-status-current-bg colour236
setw -g window-status-current-style bold
setw -g window-status-current-format '#I#[fg=colour1]: #[fg=colour226]#W#[fg=colour226]#F'
#set status-bg default
#set status-fg red

#setw -g window-status-fg colour9
#setw -g window-status-fg default
#setw -g window-status-bg default
#setw -g window-status-attr none
#setw -g window-status-format '#I#[fg=colour60]:#[fg=colour60]#W#[fg=colour60]#F'
#set -g status-left '#[fg=colour244]#(curl wttr.in?format=1; sleep 600;) #[fg=colour39]'[+%H:%M]' #[fg=colour46]#(uptime -p | sed 's/hours,/H::/' | sed 's/minutes/M/' | sed 's/up//' | tr -d " \t\n\r") #[fg=colour69]#{net_speed}'
setw -g window-status-format '#I#[fg=colour60]: #[fg=colour60]#W#[fg=colour60]#F'
#setw -g window-status-current-format '#[fg=colour33] #{s|/home/untitled|  |:pane_current_path}'
#set -g status-right '#(history | grep `date +%-m/%-d/%Y` | wc -l)'
set -g status-left '#[fg=colour33] #{s|/home/untitled|  |:pane_current_path} '
#set -g status-right '#{?client_prefix,#[fg=colour39]prefix-ON,} #[fg=colour202] #[fg=colour109] #(exec_time)#[fg=colour33] #(task active|grep -v task|tail -n2|head -n1|rev|cut -d " " -f1|rev)#[fg=colour203] #h #[fg=colour63] #(cat /tmp/numbhist) #[fg=color209]#S.#I.#P'
#set -g status-right '#{?client_prefix,#[fg=colour39]prefix-ON,} #[fg=colour202] #[fg=colour109] #(~/histor.sh) #[fg=colour33] #{s|/home/untitled| |:pane_current_path}#[fg=colour203]  #H #[fg=colour63]:#[fg=color209]#S.#I.#P'
#set -g status-right '#{?client_prefix,#[fg=colour51]prefix-ON,} #[fg=colour202] #(tail -1 ~/.zsh_history | cut -d ";" -f2- | cut -f 1 -d " ") #[fg=colour33] #{s|/home/untitled|  |:pane_current_path} #[fg=colour109] #(~/tools/histor.sh) #[fg=colour63]#I:#P.#S'
set -g status-right '#{?client_prefix,#[fg=colour51]prefix-ON,} #[fg=colour202] #(tail -1 ~/.zsh_history | cut -d ";" -f2- | cut -f 1 -d " ") #[fg=colour109] #(~/tools/histor.sh) #[fg=colour63]#S:#I.#P'
#set -g status-right '#{?client_prefix,#[fg=colour51]prefix-ON,} #I#[fg=colour60]: #[fg=colour60]#W#[fg=colour60]#F #[fg=colour202] #(tail -1 ~/.zsh_history | cut -d ";" -f2- | cut -f 1 -d " ") #[fg=colour109] #(~/histor.sh) #[fg=colour63]#I:#P.#S'
setw -g window-status-bell-style bold
setw -g window-status-bell-style fg=colour255
setw -g window-status-bell-style bg=colour1

#+----------+
#+ Messages +
#+---------+
set -g message-style fg=colour196
set -g message-style bg=colour236
set -g message-command-style fg=cyan
set -g message-command-style bg=colour237

#set-option -g status-position top
set-option -g status-position bottom
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'
set -g @plugin 'JindrichPilar/tmux-timekeeper'
#set -g @plugin 'arcticicestudio/nord-tmux'
#set -g @plugin 'tmux-plugins/tmux-prefix-highlight'
# Other examples:
set -g @plugin 'tmux-plugins/tmux-resurrect'
#set -g @plugin 'tmux-plugins/tmux-timekeeper'
# for vim
#set -g @plugin 'christoomey/vim-tmux-navigator'
#run '~/.tmux/plugins/tpm/tpm'
set -g @plugin 'tmux-plugins/tmux-sidebar'
set -g @resurrect-strategy-vim 'session'
set -g @plugin 'tmux-plugins/tmux-yank'
set -g @plugin 'tmux-plugins/tmux-net-speed'
#source "/home/untitled/.tmux/plugins/tmux-timekeeper/timekeeper.tmux"
# Initialize TMUX plugin manager (keep this line at the very bottom of tmux.conf)
#run "~/.tmux/themes/nord-tmux/nord.tmux"
#set status-bg default
#set status-fg red

#if "test ! -d ~/.tmux/plugins/tpm" \
   #"run 'git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm && ~/.tmux/plugins/tpm/bin/install_plugins'"
run '~/.tmux/plugins/tpm/tpm'
```
