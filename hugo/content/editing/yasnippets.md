+++
date = "2022-08-29T05:53:26+09:00"
title = "6.7. yasunippets"
draft = false
weight = 7
+++
## [yasnippets.el] テンプレート システム
🔗 [joaotavora/yasnippet: Template system for Emacs.](https://github.com/joaotavora/yasnippet) 

`yasnippet`は、Emacsのテンプレートシステムです。省略形を入力すると、それが関数テンプレートに自動的に展開されます。

`company` と連携することでとても便利になります。

```elisp
(leaf yasnippet
  :ensure t
  :hook (after-init-hook . yas-global-mode)
  :custom (yas-indent-line . 'fixed))
(leaf yasnippet-snippets
  :ensure t
  :after yasnippet)
```
