+++
date = "2022-08-29T06:03:08+09:00"
title = "12.5. open thunar"
draft = false
+++
## Thunarを Emacsから呼び出す

Emacsで開いている `buffer` の`current-dir` で `Debian` の `Thuner` を開きます。

使う機会は少ないと思いますが...

```elisp
(defun filer-current-dir-open ()
  "Open filer in current dir."
  (interactive)
  (compile (concat "Thunar " default-directory)))
(bind-key "<f3>" 'filer-current-dir-open)
```
