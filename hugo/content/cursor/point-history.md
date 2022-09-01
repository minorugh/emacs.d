+++
date = "2022-09-01T15:21:37+09:00"
title = "3.6. Point Histry"
draft = true
+++
## [point-history.el] 過去のカーソル位置を記憶・閲覧・選択・移動する
🔗 [blue0513/point-history: Show the history of points you visited before.](https://github.com/blue0513/point-history) 

過去に訪れた箇所の一覧をリストとして表示して、そこから戻りたい箇所を選択できます。
デフォルトは `tab`移動ですが変更しています。また、`g` でリスト画面が消えてくれるので、わかりやすく`gg`で発動するようにキーバインドしています。

リスト上でポイントを移動させると、連動してビューバッファーを表示し対応位置をハイライトしてくれるところが優れものです。

```elisp
;; point-history
;; point-history
(leaf point-history
  :el-get blue0513/point-history
  :hook (after-init-hook . point-history-mode)
  :chord ("gg" . point-history-show) ;; Since it disappears with `g'
  :bind ((:point-history-show-mode-map
		  ("<SPC>" . point-history-next-line)
		  ("b" . point-history-prev-line)))
  :custom (point-history-show-buffer-height . 15))
```
