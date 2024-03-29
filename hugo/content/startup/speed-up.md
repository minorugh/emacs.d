+++
date = "2022-08-29T05:45:20+09:00"
title = "1.2. speed up startup"
+++
## 起動時間の短縮

マジックファイル名を一時的に無効にすることで、起動時間を短縮できます。

GC設定とともに設定ファイル読み込み後に正常値に戻します。
`eary-init.el` に書くよりも `init.el` の先頭に書くほうが効果がある感じです。

```elisp
;; Speed up startup
(unless (or (daemonp) noninteractive init-file-debug)
  (let ((old-file-name-handler-alist file-name-handler-alist))
    (setq file-name-handler-alist nil)
    (add-hook 'emacs-startup-hook
              (lambda ()
                "Recover file name handlers."
                (setq file-name-handler-alist
                      (delete-dups (append file-name-handler-alist
                                           old-file-name-handler-alist)))))))

;; Defer garbage collection further back in the startup process
(setq gc-cons-threshold most-positive-fixnum)
(add-hook 'emacs-startup-hook
          (lambda ()
            "Recover GC values after startup."
            (setq gc-cons-threshold 800000)))
```
