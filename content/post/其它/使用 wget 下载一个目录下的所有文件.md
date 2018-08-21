+++
title = "使用 wget 下载一个目录下的所有文件"
date = "2013-04-16 11:44:32"
draft = false
tags = ["Download" , "Shell" , "Snippet" , "wget"]
author = "tt4"
+++



今天想下载 MIT 的李代数课程笔记，参见网页：[http://math.mit.edu/classes/18.745/Notes/](http://math.mit.edu/classes/18.745/Notes/). 突然间忘了 [cciN_bash]wget[/cciN_bash] 的用法，如果直接将上述 URL 作为 [cciN_bash]wget[/cciN_bash] 的参数的话，只会下载 index.html 文件。上网搜了一下，发现需要用到以下参数，所以写此日志记录之. 我参考了以下网站 [http://bmwieczorek.wordpress.com/2008/10/01/wget-recursively-download-all-files-from-certain-directory-listed-by-apache/](http://bmwieczorek.wordpress.com/2008/10/01/wget-recursively-download-all-files-from-certain-directory-listed-by-apache/)

基本上，只要：

[ccN_bash]wget -r -np -nH -R index.html http://url/including/files/you/want/to/download/ [/ccN_bash]

解释一下各个参数的含义：

*   [cciN_bash] -r [/cciN_bash] : 遍历所有子目

*   [cciN_bash] -np [/cciN_bash] : 不到上一层子目录

*   [cciN_bash] -nH [/cciN_bash] : 不要将文件保存到主机名文件

*   [cciN_bash] -R index.html [/cciN_bash] : 不下载 index.html 文件

看，瞬间你要的所有文件就会下载到当前目录了！
