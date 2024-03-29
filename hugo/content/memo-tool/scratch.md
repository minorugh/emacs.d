+++
date = "2022-08-29T06:00:38+09:00"
title = "11.3. scratch-memo"
draft = false
weight = 3
+++

## scratchバッファーを付箋として使う

Emacsで作業中の編集画面から短期的なメモを気軽に書きたいので付箋代わりに `*scratch*`バッファーが使えるように設定してみた。

再起動しても`*scratch*` の内容が消えないように [`auto-save-buffers`](http://emacs.rubikitch.com/auto-save-buffers-enhanced/) の `*scratch*` 自動保存機能を併用しています。

専用のパッケージもあるようです。

* [persistent-scratch.el: scratch バッファを永続化・自動保存・復元する](http://emacs.rubikitch.com/persistent-scratch/) 

`toggle-scratch` は、編集中のバッファーと`scratch`とをトグルで切り替えます。

```elisp
;; Scratch for sticky-memo
(leaf *scratch-memo
  :after auto-save-buffers-enhanced
  :bind ("S-<return>" . toggle-scratch)
  :custom ((auto-save-buffers-enhanced-save-scratch-buffer-to-file-p . t)
		   (auto-save-buffers-enhanced-file-related-with-scratch-buffer . "~/.emacs.d/tmp/scratch"))
  :init
  (defun toggle-scratch ()
	"Toggle current buffer and *scratch* buffer."
	(interactive)
	(if (not (string= "*scratch*" (buffer-name)))
		(progn
		  (setq toggle-scratch-prev-buffer (buffer-name))
		  (switch-to-buffer "*scratch*"))
	  (switch-to-buffer toggle-scratch-prev-buffer)))

  (defun read-scratch-data ()
	(let ((file "~/.emacs.d/tmp/scratch"))
	  (when (file-exists-p file)
		(set-buffer (get-buffer "*scratch*"))
		(erase-buffer)
		(insert-file-contents file))))
  (read-scratch-data))
```

## Scratch バッファーを消さない
`scratch`付箋環境を実現させるのに必須なのは、決して`scratch`バッファーを消さないようにすること。
難しい関数を設定せずともビルトインコマンドで簡単に実現できます。

```elisp
;; Set buffer that can not be killed
(with-current-buffer "*scratch*"
  (emacs-lock-mode 'kill))
(with-current-buffer "*Messages*"
  (emacs-lock-mode 'kill))
```
