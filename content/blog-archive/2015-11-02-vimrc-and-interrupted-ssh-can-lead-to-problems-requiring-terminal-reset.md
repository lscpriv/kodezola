---
title: .vimrc and interrupted ssh can lead to problems, requiring terminal reset
author: Chris
date: 2015-11-02T02:06:57+00:00
categories:
  - Uncategorized

---
I discovered something neat today. I have the following script in my .vimrc for all of my shells, as well as my local machine:
<!-- more -->  
```vim
if &term =~ &#8220;xterm.*&#8221;
let &t\_ti = &t\_ti . &#8220;e[?2004h&#8221;
let &t\_te = &#8220;e[?2004l&#8221; . &t\_te
function XTermPasteBegin(ret)
set pastetoggle=<Esc>[201~
set paste
return a:ret
endfunction
map <expr> <Esc>[200~ XTermPasteBegin(&#8220;i&#8221;)
imap <expr> <Esc>[200~ XTermPasteBegin(&#8220;&#8221;)
cmap <Esc>[200~ <nop>
cmap <Esc>[201~ <nop>
endif
```

This isn&#8217;t really a problem with local instances of vim, but remote instances, if the connection is terminated while the editor is active, it will leave this edit mode enabled in the terminal client on OS X, whether it&#8217;s Terminal.app or iTerm2.

This results in all pastes getting surrounded with \`<Esc>[200~\` and \`<Esc>[201~\`, which only appear in echoes as \`0~\` and \`1~\`. This can really be annoying when doing any minor editing, and can make pasting passwords into prompts quite confusing if you don&#8217;t know what&#8217;s going on.

The fix, quite simply, is to issue a \`reset\` command to the terminal, which will restore it to normal operation.

Noting this error and fix down for future reference.
