Title: Emacs 的颜色补强计划

Date: 2013-04-04 22:05:21

用了 Emacs Carbon 这么久，这次才发现真的落伍了！今天想要安装 Paul Onion 开发的 axiom-environment，不料一个关于 color-theme 的变量老是出错。上网搜了一下，才发现原来从 Emacs24 开始，改变了以前的颜色机制，这样文本高亮比以前似乎要更加犀利了（没有仔细读文献，只是看了看图直观的感觉是这样）。

但是，在 Emacs24 之前的版本，必须要手动加入这项功能。具体的包见：

[https://github.com/sellout/emacs-color-theme-solarized](https://github.com/sellout/emacs-color-theme-solarized "https://github.com/sellout/emacs-color-theme-solarized")

安装很简单，这里是针对我这个 pre emacs24 来说的，我就犯懒直接复制 github 里的说明好了：

1.  Download and install [color-theme](http://www.nongnu.org/color-theme "color-theme")

2.  Add the &lt;cci_lisp&gt;emacs-color-theme-solarized directory to your Emacs &lt;cci_lisp&gt;load-path

3.  Add &lt;cci_lisp&gt;(require 'color-theme-solarized) to your Emacs init file (usually &lt;cci_bash&gt;~/.emacs)

4.  Reload the init file, or restart Emacs

5.  Use the usual [color-theme](http://www.nongnu.org/color-theme) mechanism to select one of the Solarized themes, or &lt;cci_lisp&gt;M-x color-theme-solarized-[light|dark].

具体的代码像这样：

`

(add-to-list 'load-path "~/.emacs.d/color-theme-6.6.0/color-theme.el")

(load-file "~/.emacs.d/emacs-color-theme-solarized/color-theme-solarized.el")

(require 'color-theme)

(require 'color-theme-solarized)

(color-theme-initialize)

(color-theme-solarized-light)

`

这个颜色增强包不止针对 emacs, 对 vim, 甚至 terminal 都有对应的方法。以后慢慢尝试。但是 axiom-environment 仍未成功。看来还得请教作者。