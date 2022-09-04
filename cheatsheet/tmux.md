## TMUX

:setw synchronize-panes on (sincroniza tds os panes)
:resize-pane -U 10 (redimensiona pra cima tirando 10px)
:resize-pane -D 10 (redimensiona pra baixo jogando 10px)

alt = C-b

alt
   c create window
   & kill window
   '/% create pane
   x kill pane
   up/down/right/left
   [
   0/1/2/3/4/5/...
   q mostra a numeracao dos panes
   z tela cheia no pane

tmux ls
tmux new -s docker
tmux a -t docker 
tmux kill-session -t docker
