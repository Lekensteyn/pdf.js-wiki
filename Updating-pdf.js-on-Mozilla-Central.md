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
        IdentityFile ~/.ssh/id_rsa
```

+ Setup Git
	+ Make sure your account's default identity is set.
```
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```

	+ On Windows, make sure automatic line endings conversion is turned off.
```
git config --global core.autocrlf false
```

### Updating Steps

+ make sure all patches are popped off your queue
```
hg qpop -a
```

+ update moz central
```
hg pull -u
```

+ update pdf.js and build extension
```
node make mozcentral
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
# copy files build ./build/mozcenral/* into mozilla-central/ root
hg qrefresh
```

+ Add Try Stuff
```
hg qnew try --message "try: -b do -p macosx,macosx64,win32,linux,linux32 -u all -t none"
```

+ Double Check What Your Sending
```
hg outgoing
```

+ Push to Try Server
```
hg push -f try
```

+ Pop off the try patch (if you can't pop the patch see https://wiki.mozilla.org/ReleaseEngineering/TryServer#Disable_hg_phases_with_a_post-push_hook )
```
hg qpop
```

+ Generate Patch (after successful try run, replace bug number)
```
hg export qtip > ~/projects/mine/pdf.js/patches~/bug-743264-fix.patch
```

### If Uplift is Needed
+ Find what version of pdf.js is in the branch by looking at the pdf.js file and PDFJS.build variable e.g. PDFJS.build = 'f8e70dc';

+ Check out that version
```
git checkout -b tt-aurora-fix <baseLineCommit>
```

+ Cherry Pick the commit you need to uplift
```
git cherry-pick <someCommit>
```

+ Build the patch
```
BASELINE=<baseLineCommit> node make mozcentralbaseline; node make mozcentraldiff
```

+ Apply that to the branch
```
qimport -n cherry-pick <pdf.js build folder>/mozcentral.diff; qpush;
```