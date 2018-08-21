Title: Emacs 的 bookmark 插件

Date: 2013-12-23 05:53:47

有时候经常要在同一个 LaTeX 文件的前后来回跳转，当文件很大时还是十分不便的，因此有个标记位置的插件还是十分必要的。之前用过很久，但是换电脑的时候忘记怎么回事了，于是又搜索了一下，重新发现 joodland 的 [bm](https://github.com/joodland/bm) 这个插件，

[caption id="attachment_703" align="aligncenter" width="1024"][![bm](http://www.xjliu.net/blog/wp-content/uploads/2013/12/屏幕快照-2013-12-24-上午12.18.16-1024x694.png)](http://www.xjliu.net/blog/wp-content/uploads/2013/12/屏幕快照-2013-12-24-上午12.18.16.png) bm[/caption]

可以很明显的标记出文章中的某些行，短小精悍，而且也支持文件间跳转，遂记录之。安装很简单，下载下来放在 .emacs.d/ 目录下就可以了。

#### 设置

非常简单，只要在 .emacs 文件中添加上相应的路径：


(add-to-list 'load-path "~/.emacs.d/bm/")

(require 'bm)

#### 快捷键设置



(global-set-key (kbd "M-S-return") 'bm-toggle) 

(global-set-key (kbd "M-S-down") 'bm-next) 

(global-set-key (kbd "M-S-up") 'bm-previous)



这组快捷键用的挺顺手，并且不和系统现有的快捷键冲突 ^_^