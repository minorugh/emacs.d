+++
date = "2022-08-29T05:58:29+09:00"
title = "9.3. recentf"
draft = false
+++
## 開いたファイルの履歴を保存

複数端末でHistファイルの `.recentf`ファイルを共有している場合、`auto-cleanup` を `never` にしておかないと大変なことになる。

```elisp
;; recentf
(leaf recentf
  :custom `((recentf-auto-cleanup . 'never)
			(recentf-exclude
			 . '("\\.howm-keys" "Dropbox/backup" ".emacs.d/tmp/" ".emacs.d/elpa/" "/scp:"))))
```
