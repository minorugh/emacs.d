+++
date = "2022-08-29T05:53:26+09:00"
title = "6.16. font-awesome"
draft = false
weight = 16
+++
## [font-awesom.el] 絵文字フォント入力支援
🔗 [krismolendyke/font-awesome.el: A simple library for using Font Awesome icons in Emacs.](https://github.com/krismolendyke/font-awesome.el) 

`Font-awesome` の入力を`counsel` で支援してくれる。

```elisp
(leaf font-awesome
  :ensure t
  :bind ("s-f" . counsel-fontwesame))
```

