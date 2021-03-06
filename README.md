# emacs-neotree #

A Emacs tree plugin like NerdTree for Vim.

`Develop` [![Build Status](https://travis-ci.org/jaypei/emacs-neotree.svg?branch=dev)](https://travis-ci.org/jaypei/emacs-neotree)
`Master` [![Build Status](https://travis-ci.org/jaypei/emacs-neotree.svg?branch=master)](https://travis-ci.org/jaypei/emacs-neotree)


## Screenshots ##

![NeoTree-1] (https://raw.githubusercontent.com/wiki/jaypei/emacs-neotree/imgs/neotree-1.png)

## Installation ##

### Melpa

You can install the plugin using the packages on [melpa](http://melpa.milkbox.net/).

Make sure you have something like the following in your Emacs startup file (`~/.emacs.d/init.el`, or `~/.emacs`):

```elisp
    (add-to-list 'package-archives
                 '("melpa" . "http://melpa.milkbox.net/packages/"))
```

To make that take effect, either evaluate that elisp expression or restart Emacs.

Then use `M-x package-list-packages`, select `neotree` from
the list by pressing `i`, then press `x` to execute the changes. At
that point, the package will be installed.


### Source

Clone project:
```sh
$ cd /some/path
$ git clone https://github.com/jaypei/emacs-neotree.git neotree
$ cd neotree
$ git checkout dev
```

Add config to emacs:

```elisp
(add-to-list 'load-path "/some/path/neotree")
(require 'neotree)
(global-set-key [f8] 'neotree-toggle)
```

Open (toggle) NeoTree:

```
<F8>
```

## Useful tips

### find-file-in-project

If you use the `find-file-in-project` (ffip) library, you can open `neotree` at your directory root by
adding this code to your `.emacs.d`:

```elisp
(defun neotree-project-dir ()
  "Open dirtree using the git root."
  (interactive)
  (let ((project-dir (ffip-project-root))
        (file-name (buffer-file-name)))
    (if project-dir
        (progn
          (neotree-dir project-dir)
          (neotree-find file-name))
      (message "Could not find git project root."))))

(define-key map (kbd "C-c C-p") 'neotree-project-dir)
```


## More documentation ##

* [EmacsWiki](http://www.emacswiki.org/emacs/NeoTree)
* [中文版 NeoTree](http://www.emacswiki.org/emacs-zh/NeoTree_%E4%B8%AD%E6%96%87wiki)
