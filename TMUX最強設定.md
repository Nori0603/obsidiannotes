---
tags: ""
datetimeCreate: 2025-06-21 12:57
---
##### 基本 #####
set -g prefix C-a           # HHKBのControlを生かす
unbind C-b
bind C-a send-prefix

set -g base-index 1         # window 1 始まり
setw -g pane-base-index 1   # pane  1 始まり
set -sg escape-time 0       # キレの良いレスポンス

##### カラー & フォント #####
set -g default-terminal "tmux-256color"
set -as terminal-overrides ",xterm-256color:RGB"

##### マウス＋トラックポイント #####
set -g mouse on             # クリックで pane 選択／ドラッグでリサイズ可

##### Alt(⌥) = Meta キー拡張（Mac用） #####
# 移動
bind -n M-h select-pane -L
bind -n M-j select-pane -D
bind -n M-k select-pane -U
bind -n M-l select-pane -R
# サイズ変更（長押しOK）
bind -n M-H resize-pane -L 5
bind -n M-J resize-pane -D 2
bind -n M-K resize-pane -U 2
bind -n M-L resize-pane -R 5

##### クリップボード & コピーモード改善 #####
bind-key -T copy-mode-vi y send -X copy-pipe-and-cancel "pbcopy"
set -g set-clipboard on

##### ステータスバー #####
set -g status-interval 5
set -g status-right-length 120
set -g status-right '#[fg=cyan]#(git -C #{pane_current_path} rev-parse --abbrev-ref HEAD) #[fg=yellow]#(pmset -g batt |grep -Eo "[0-9]+%") #[fg=green]%Y-%m-%d %H:%M '

##### プラグイン #####
set -g @plugin 'tmux-plugins/tpm'          # 必須
set -g @plugin 'tmux-plugins/tmux-resurrect'
set -g @plugin 'tmux-plugins/tmux-continuum'
set -g @plugin 'tmux-plugins/tmux-yank'    # pbcopy 連携
set -g @plugin 'tmux-plugins/tmux-fzf'     # pane/window 検索
set -g @continuum-restore 'on'             # 自動セッション復元

##### 最後に #####
run '~/.tmux/plugins/tpm/tpm'






```dataviewjs
dv.header(3, "関連ノート");
var maxLoop = Math.min(dv.current().file.tags.length, 3);
for(let i=0;i<maxLoop;i++){
dv.span(dv.current().file.tags[i]);
dv.list(dv.pages(dv.current().file.tags[i]).sort(f=>f.file.mtime.ts,"desc").limit(15).file.link);
}

for (let outgo of dv.pages('outgoing([[' + dv.current().file.name + ']])')) {
    dv.header(4, outgo.file.name);
    dv.list(outgo.file.inlinks.sort());
}
```