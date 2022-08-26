+++
title = "12.1. auto-delete"
draft = false
+++
### 空になったファイルを自動的に削除
下記の設定をしておくと、`C-x h` で全選択して delete したあと `kill-buffer` することで自動的にファイルが削除されるので便利です。

```elisp
(defun my:delete-file-if-no-contents ()
  "Automatic deletion for empty files (Valid in all modes)."
  (when (and (buffer-file-name (current-buffer))
			 (= (point-min) (point-max)))
    (delete-file
     (buffer-file-name (current-buffer)))))
(if (not (memq 'my:delete-file-if-no-contents after-save-hook))
    (setq after-save-hook
		  (cons 'my:delete-file-if-no-contents after-save-hook)))
```

### 開いているバッファーを閉じて当該ファイルを削除する
やや危険なのであまりおすすめできませんが…

安全を期すために確認するようにはしてます。
```elisp
(defun my:delete-this-file ()
	"Delete the current file, and kill the buffer."
	(interactive)
	(unless (buffer-file-name)
      (error "No file is currently being edited"))
	(when (yes-or-no-p (format "Really delete '%s'?"
                               (file-name-nondirectory buffer-file-name)))
      (delete-file (buffer-file-name))
      (kill-this-buffer)))
```