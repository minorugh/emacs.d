+++
date = "2022-08-29T05:50:55+09:00"
title = "3.4. exchange-point-and-mark"
draft = false
+++
## 直前の編集ポイントと現在のポイントとを行き来する設定

`my:exchange-point-and-mark` は、直前の編集ポイントと現在のポイントとを行き来できる設定です。

```elisp
(defun my:exchange-point-and-mark ()
  "No mark active `exchange-point-and-mark'."
  (interactive)
  (exchange-point-and-mark)
  (deactivate-mark))		 
(bind-key "C-x C-x" 'my:exchange-point-and-mark)
```
