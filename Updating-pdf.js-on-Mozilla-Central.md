### Initial Setup (hopefully one time)
+ Get Commit Access Level 1 (http://www.mozilla.org/hacking/committer/) (https://bugzilla.mozilla.org/show_bug.cgi?id=714712)
+ Check out Mozilla Central
	(https://developer.mozilla.org/En/Simple_Firefox_build)
+ Setup HG
	+ Edit ~/.hgrc (https://developer.mozilla.org/en/Mercurial_FAQ#How_can_I_generate_a_patch_for_somebody_else_to_check-in_for_me.3f)
	Mine:
```
[ui]
username = YOUR NAME <YOUR_HANDLE@mozilla.com>

[defaults]
qnew = -Ue

[extensions]
hgext.mq =

[diff]
git = 1
showfunc = 1
unified = 8

[paths]
try = ssh://hg.mozilla.org/try
```
+ Edit ~.ssh/config
```
Host hg.mozilla.org
        User YOUR_HANDLE@mozilla.com
        IdentityFile ~/.ssh/id_rsa.pub
```

### Updating Steps

+ update moz central
```
hg pull -u
```

+ update pdf.js and build extension
```
node make extension
```

+ Open new bugzilla bug
	+ Copy release notes there
	+ Set depends bug ????

+ Create Patch (replace bug number)
```
hg qnew bug-743264-fix -m "Bug 743264 - Update pdf.js to Version 0.2.537."
```

+ Update Files
```
copy updated files into mozilla-central/browser/app/profile/extensions/uriloader\@pdf.js
hg qrefresh
```

+ Add Try Stuff
```
hg qnew patch.try
hg qpush patch.try
hg qref --message "try: -b do -p macosx,macosx64,win32,linux,linux32 -u all -t none"
```

+ Double Check What Your Sending
```
hg outgoing
```

+ Push to Try Server
```
hg push -f try
```

+ Pop off the try patch
```
hg qpop patch.try
// Maybe just hg qpop
```

+ Generate Patch (after successful try run, replace bug number)
```
hg export qtip >~/projects/mine/pdf.js/patches~/bug-743264-fix.patch
```