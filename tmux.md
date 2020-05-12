# [TMUX]()
## MAC
下載Homebrew，然後再下載tmux
>ruby -e "$(curl -fsSL https://raw.github.com/mxcl/homebrew/go)"
brew update
brew install tmux

## Ubuntu
>sudo apt-get install tmux

# 基本概念
- session  
每次下 tmux 指令時都會開啟一個新的 session，每個 session 各自獨立  
- window  
window 就是下圖整個終端機畫面，一個 session 裡面可以有多個 window  
- pane  
如下圖，一個 window 可以切成多個小區塊，每個區塊就是一個 pane，通常會用來同時觀察多個程式

# vim ~/.tmux.conf
>###rebind hotkey  
>  
>#prefix setting (screen-like)  
>  
>set -g prefix C-a  
>unbind C-b  
>bind C-a send-prefix  
>  
>#reload config without killing server  
>bind R source-file ~/.tmux.conf \; display-message "Config reloaded..."  
>  
>#"|" splits the current window vertically, and "-" splits it horizontally  
>unbind %  
>bind | split-window -h  
>bind - split-window -v  
>  
>#Pane navigation (vim-like)  
>bind h select-pane -L  
>bind j select-pane -D  
>bind k select-pane -U  
>bind l select-pane -R  
>  
>#Pane resizing  
>bind -r Left  resize-pane -L 4  
>bind -r Down  resize-pane -D 4  
>bind -r Up    resize-pane -U 4  
>bind -r Right resize-pane -R 4  
>  
>###other optimization  
>set the shell you like (zsh, "which zsh" to find the path)  
>set -g default-command /bin/zsh  
>set -g default-shell /bin/zsh  
>  
>use UTF8  
>set -g utf8  
>set-window-option -g utf8 on  
>
>#display things in 256 colors  
>set -g default-terminal "screen-256color"  
>  
>#mouse is great!  
>set-option -g mouse on  
>  
>#Enable mouse control (clickable windows, panes, resizable panes)  
>set -g mouse-select-window on  
>set -g mouse-select-pane on  
>set -g mouse-resize-pane on  
>  
>#history size  
>set -g history-limit 10000  
>  
>#fix delay  
>set -g escape-time 0  
>  
>#0 is too far  
>set -g base-index 1  
>setw -g pane-base-index 1  
>  
>###rename-set  
>  
>set -g base-index         1     # 窗口编号从 1 开始计数  
>set -g display-panes-time 10000 # PREFIX-Q 显示编号的驻留时长，单位 ms  
>set -g mouse              on    # 开启鼠标  
>set -g pane-base-index    1     # 窗格编号从 1 开始计数  
>set -g renumber-windows   on    # 关掉某个窗口后，编号重排  
>  
>#window notifications; display activity on other window  
>setw -g monitor-activity on  
>set -g visual-activity on  

# conf參考資料
- [1](https://gist.github.com/ryerh/14b7c24dfd623ef8edc7)
