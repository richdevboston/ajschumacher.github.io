# Fix R Tcl/Tk dependency problem on Mac OS X by installing working Tcl/Tk

For some reason, if you just install R on Mac OS X, you don't have a working Tcl/Tk by default. The problem manifests itself like this:

```html
&gt; tkplot(g)
Loading required package: tcltk
Loading Tcl/Tk interface ... Error : .onLoad failed in loadNamespace() for 'tcltk', details:
  call: dyn.load(file, DLLpath = DLLpath, ...)
  error: unable to load shared object '/Library/Frameworks/R.framework/Versions/2.15/Resources/library/tcltk/libs/x86_64/tcltk.so':
  dlopen(/Library/Frameworks/R.framework/Versions/2.15/Resources/library/tcltk/libs/x86_64/tcltk.so, 10): Library not loaded: /usr/local/lib/libtcl8.5.dylib
  Referenced from: /Library/Frameworks/R.framework/Versions/2.15/Resources/library/tcltk/libs/x86_64/tcltk.so
  Reason: image not found
Error in tkplot(g) : tcl/tk library not available
```

There are other functions that depend on Tcl/Tk as well. It's particularly annoying that you don't see the problem when you install or even load a library, but only when you try to use a function that depends on Tcl/Tk.

Fortunately, there's an easy solution. You need these two things:

1. <a href="http://xquartz.macosforge.org/">X Windows for Mac OS X</a>. You may already have this. If not, install it.
2. <a href="http://cran.us.r-project.org/bin/macosx/tools/">A Tcl/Tk installation that actually works</a>. This will do the trick. Just install!

After you have these two installed, things should work. I didn't even have to restart R.

```html
&gt; tkplot(g)
Loading required package: tcltk
Loading Tcl/Tk interface ... done
```


*This post was originally hosted [elsewhere](http://planspace.blogspot.com/2013/01/fix-r-tcltk-dependency-problem-on-mac.html).*
