+++
date = "2022-08-29T05:53:26+09:00"
title = "6.13. smartparens"
draft = false
weight = 13
+++
## [smartparens.el] 対応する括弧の挿入をアシスト
🔗 [Fuco1/smartparens: Minor mode for Emacs that deals with parens pairs and tries to be smart about it.](https://github.com/Fuco1/smartparens) 

設定がいまいちよくわからず、試行錯誤しましたが、
```
(require 'smartparens-config)
```
を追加したところとても賢く機能するようになりました。 

```elisp
(leaf smartparens
  :ensure t
  :hook ((after-init-hook . smartparens-global-mode)
		 (prog-mode-hook . turn-on-smartparens-mode))
  :config
  (require 'smartparens-config))
```
