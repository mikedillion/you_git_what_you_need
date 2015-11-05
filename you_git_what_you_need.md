---
title: you git what you need
author:
  name: MikeD
output: miked-you_git_what_you_need.html
theme: jdan/cleaver-retro
controls: false
---

--

# You Git What You Need
## (if you try sometimes, well you just might find)

--

# "You're not using Git enough"

--

> "The code comes and goes like muffled and veiled figures sent from a distant friendly party; but it says nothing, and if we do not use the gifts they bring, they carry them as silently away"
> *Ralph Waldo Emerson*

> "Yes, you can lose commits overnight, yes, your whole life can be turned upside down. Life is short. It can come and go like a feather in the wind."
> *Shania Twain*

--

### Diff!

On your mac, probably (GNU diffutils) 2.8.1

* [kdiff3](http://kdiff3.sourceforge.net/doc/documentation.html) (`brew install kdiff3`)
* [Kaleidoscope](http://www.kaleidoscopeapp.com/) ($70!!)

--

### Normal old diffing

Diff between files

```
diff one.txt two.text
```

Diff between outputs

```
diff <(ssh host1 "cat one.txt") \
     <(ssh host2 "cat two.txt")
```

Diff directories of files

```
diff -qr dir1/ dir2/
```

--

### kdiff3
Command line kdiff3 (as you would expect)

```
kdiff3 one.txt two.txt
kdiff3 dir1/filename dir2 dir3
```

--

### Kaleidoscope as git diff and merge tools

```
"
" .gitconfig
"
[difftool "Kaleidoscope"]
	cmd = ksdiff --partial-changeset --relative-path \"$MERGED\" -- \"$LOCAL\" \"$REMOTE\"
[diff]
	tool = Kaleidoscope
[difftool]
	prompt = false

[mergetool "Kaleidoscope"]
	cmd = ksdiff --merge --output \"$MERGED\" --base \"$BASE\" -- \"$LOCAL\" --snapshot \"$REMOTE\" --snapshot
	trustExitCode = true
[mergetool]
	prompt = false
[merge]
	tool = Kaleidoscope
```
--

### Kaleidoscope as git diff and merge tools

```
git difftool master.. whateverfile
alias gdit='git difftool' # my personal alias
```

--

### kdiff3 as git diff and merge tools

```
"
" .gitconfig
"
[difftool "kdiff3"]
    path = /Applications/kdiff3.app/Contents/MacOS/kdiff3
    trustExitCode = false
[difftool]
    prompt = false
[diff]
    tool = kdiff3
[mergetool "kdiff3"]
    path = /Applications/kdiff3.app/Contents/MacOS/kdiff3
    trustExitCode = false
[mergetool]
    keepBackup = false
[merge]
    tool = kdiff3
```

--

### Git diff between branches, files and directories

```
git diff master..
git diff master.. app
git diff master.. config/database.yml
```

```
git diff --name-only master..
```

--

### Git diffs as patches

```
git diff master.. config/database.yml > my_thing.patch
```

### Saving patches as files instead of stashing!!

```
git diff b4da55.. > stuff_i_was_working_on
git apply stuff_i_was_working_on
```

## OR! Just pipe!!

```
git diff b4da55.. config/database.yml | git apply
```

--

# The Sweet Stuff

--

### Fugitive and a Sublime equivalent
[fugitive.vim](https://github.com/tpope/vim-fugitive) (Tim Pope!)

* Gdiff
* Gblame
* Fugitive between branches? (I dunno)
* [resolving merge conflicts with vimdiff](http://vimcasts.org/episodes/fugitive-vim-resolving-merge-conflicts-with-vimdiff/)

[Sublimerge](http://www.sublimerge.com/)

[SublimeGit](https://sublimegit.net/)

--

### Fugitive and a Sublime equivalent

# DEMO

--

### Gitgutter!! (was on Sublime first!)

[Sublime GitGutter](https://github.com/jisaacks/GitGutter)

[vim-gitgutter](https://github.com/airblade/vim-gitgutter)

* Custom emoji! (vim only?)

--

### Aside: vcprompt

[gward/vcprompt](https://bitbucket.org/gward/vcprompt)

[djl/vcprompt](https://github.com/djl/vcprompt) ***I think this is the best one***

[gward/vcprompt](https://bitbucket.org/gward/vcprompt)

* no official release, don't do the homebrew version
* matching custom emoji!
