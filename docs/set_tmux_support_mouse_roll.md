## Set tmux support mouse roll

* add the following lines to `~/.tmux.conf`
  
```bash
set -g mouse on
set -g mouse-utf8 on
```

* reload tmux configuration
  
```bash
tmux source-file ~/.tmux.conf
```

* now you can use mouse to scroll in tmux
