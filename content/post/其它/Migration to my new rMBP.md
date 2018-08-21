Title: Migration to my new rMBP

Date: 2013-12-14 21:58:38

Since I got a refurbished rMBP, it is time to migrate everything in my old MBP to the new one. Here I recorded a few important or interesting things I had in my old laptop. This would remind me in the future system upgrade.

1.  Migrate iTunes and iPhoto libraries: The fastest and most reliable way is using an external disk to copy your libraries out

2.  Finder plugin to quick look all text files (selection also be allowed), one should use QLStephen plugin which can be found here: [https://github.com/whomwah/qlstephen/downloads](https://github.com/whomwah/qlstephen/downloads) , after that, just copy the plugin (QLStephen.qlgenerator) to [ccibN_bash] /Library/QuickLook/ [/cci], and finally, restart the Finder (  **Cmd+Option+Escape** ) ( or just run [ccibN_bash] qlmanage -r [/cci]) .To let the text selectable, just try the following shell command:

[ccN_bash]defaults write com.apple.finder QLEnableTextSelection -bool true; killall Finder[/ccN

3.  Use MacVim more proficiently: move command line script [ccibN_bash]mvim[/cci] to [ccibN_bash]/usr/local/bin/[/cci

4.  Install [UnicodeIt](svenkreiss.com/UnicodeIt): UnicodeIt is a workflow allowing you to input unicode characters by using LaTeX commands. You can assign a shortcut (such as **Command+Option+Shift+u**) to trigger the workflow. It can be used in most of the Mac apps. Installation is easy, just follows the instruction in their website

5.  Install [GitCommand](https://github.com/bkozora/osx-prefz/blob/master/Widgets/ZIPs/GitCommands.zip) widget for mac: Then you can check git command on the fly

6.  Add/install more dictionaries:

To add new dictionaries, just open dictionary.app and check more dictionaries in Preference...  To install new dictionaries, here's a nice instruction on DouBan: [http://www.douban.com/group/topic/9591106/](http://www.douban.com/group/topic/9591106/) 

7.  Install [QuickSilver](qsapp.com/‎): It is more than a launcher. To set English as a searching and launching language, just use the following shell command:

[ccN_bash] defaults write com.blacktree.Quicksilver AppleLanguages -array English [/ccN

8.  Install MacTeX: In order to get LaTeXit and TexLive Manager, it is better to install **BasicTeX** and **MacTeX-additions*

9.  Install Fish: The friend interactive shell, may install it by using the .pkg file. It'll make fish the default shell, to temporary use Bash back, just type bash in the command line.

Some resources about fish:  [http://hackercodex.com/guide/install-fish-shell-mac-ubuntu/](http://hackercodex.com/guide/install-fish-shell-mac-ubuntu/)   [http://matthewcampbell.org/fish-shell-on-os-x-mountain-lion/](http://matthewcampbell.org/fish-shell-on-os-x-mountain-lion/

10.  HomeBrew: Following the instruction on its website

11.  Install XQuartz: It is now the XWindow system for Mac OS X. Just download it from [http://xquartz.macosforge.org/trac](http://xquartz.macosforge.org/trac) and install

12.  Install Xcode command line tool: Download it from [https://developer.apple.com/downloads/index.action](https://developer.apple.com/downloads/index.action

13.  Install sbcl and gmp by using homebrew

14.  Install FriCAS: It's a traditional configure/make/make install process. The configure parameters are: [ccibN_bash]./configure --x-includes=/usr/X11R6/include --x-libraries=/usr/X11R6/lib --with-lisp=/usr/local/bin/sbcl[/cci

15.  Install Markdown QuickView plugin: [https://github.com/toland/qlmarkdown](https://github.com/toland/qlmarkdown "qlmarkdown")