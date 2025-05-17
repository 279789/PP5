# PP5

## Goal

In this exercise you will:

* Use Git **locally** on your own machine: create branches, make commits, and merge them back.
* Set up and interact with a **bare** Git repository on an SSH‐accessible server (e.g. **vorlesungsserver**, or any machine you have SSH access to).
* Push and pull to/from **GitHub** and the **THGA GitLab** server.
* Practice **forking** an existing repo, making changes, and submitting a **Pull Request** (on GitHub) or **Merge Request** (on GitLab).
* Have fun

**Important:** Start a stopwatch when you begin and work uninterruptedly for **90 minutes**. Once time is up, stop immediately and document exactly where you had to pause.

---

## Workflow

1. **Fork** this repository
2. **Modify & commit** your solution
3. **Submit your link for Review**

---

## Prerequisites

* Several starter repos are available here:
  [https://github.com/orgs/STEMgraph/repositories?q=Git%3A](https://github.com/orgs/STEMgraph/repositories?q=Git%3A)
* Ensure you have **SSH access** to a remote server (e.g., “vorlesungsserver”).
* Throughout, consult Git’s built-in man-pages (`git help <command>`) for explanations and options.

---

## Tasks

### Task 1: Local Git – Branching & Merging

1. Create a new directory in your home directory and initialize a repository in it. 
2. In one of your cloned repos, initialize a new branch called `feature-1`.
3. On `feature-1`, create a file `feature.txt` containing a short description of what you’re doing.
4. Commit your changes, then switch back to `master` (or `main`), and merge `feature-1` into your `master`.
5. Resolve any merge conflicts (if they arise) by hand, then commit the merge. 

**Your Commands & Output**

```bash
# Paste here the sequence of git commands you ran
# and the relevant terminal output (e.g., branch listing, merge messages)
philr@3245-Laptop:~/Programieren/repos$ mkdir PP5
philr@3245-Laptop:~/Programieren/repos$ cd PP5
philr@3245-Laptop:~/Programieren/repos/PP5$ git init
Initialized empty Git repository in /home/philr/Programieren/repos/PP5/.git/
philr@3245-Laptop:~/Programieren/repos/PP5$ branch feature-1
Command 'branch' not found, but can be installed with:
sudo apt install rheolef
philr@3245-Laptop:~/Programieren/repos/PP5$ git branch feature-1
fatal: not a valid object name: 'master'
philr@3245-Laptop:~/Programieren/repos/PP5$ git checkot -b feature 1
git: 'checkot' is not a git command. See 'git --help'.

The most similar command is
        checkout
philr@3245-Laptop:~/Programieren/repos/PP5$ git checkout -b feature 1
fatal: '1' is not a commit and a branch 'feature' cannot be created from it
philr@3245-Laptop:~/Programieren/repos/PP5$ git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
philr@3245-Laptop:~/Programieren/repos/PP5$ git log
fatal: your current branch 'master' does not have any commits yet
philr@3245-Laptop:~/Programieren/repos/PP5$ touch sens.txt
philr@3245-Laptop:~/Programieren/repos/PP5$ git add sens.txt
philr@3245-Laptop:~/Programieren/repos/PP5$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   sens.txt

philr@3245-Laptop:~/Programieren/repos/PP5$ git commit -m "Test"
[master (root-commit) 7814dc9] Test
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 sens.txt
philr@3245-Laptop:~/Programieren/repos/PP5$ git log
commit 7814dc9139a3683e72cf8d0fa8f07e3fdbe55849 (HEAD -> master)
Author: Filz <phil.reinartz@gmx.de>
Date:   Sat May 17 10:45:13 2025 +0200

    Test
philr@3245-Laptop:~/Programieren/repos/PP5$ git branch feature-1
philr@3245-Laptop:~/Programieren/repos/PP5$ git log
commit 7814dc9139a3683e72cf8d0fa8f07e3fdbe55849 (HEAD -> master, feature-1)
Author: Filz <phil.reinartz@gmx.de>
Date:   Sat May 17 10:45:13 2025 +0200

    Test
philr@3245-Laptop:~/Programieren/repos/PP5$ git checkout feature-1
Switched to branch 'feature-1'
philr@3245-Laptop:~/Programieren/repos/PP5$ vim feature.txt
philr@3245-Laptop:~/Programieren/repos/PP5$ ls
feature.txt  sens.txt
philr@3245-Laptop:~/Programieren/repos/PP5$ git status
On branch feature-1
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        feature.txt

nothing added to commit but untracked files present (use "git add" to track)
philr@3245-Laptop:~/Programieren/repos/PP5$ git add feature.txt
philr@3245-Laptop:~/Programieren/repos/PP5$ git status
On branch feature-1
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   feature.txt

philr@3245-Laptop:~/Programieren/repos/PP5$ git commit -M "feature commit"
error: unknown switch `M'
usage: git commit [-a | --interactive | --patch] [-s] [-v] [-u<mode>] [--amend]
                  [--dry-run] [(-c | -C | --squash) <commit> | --fixup [(amend|reword):]<commit>)]
                  [-F <file> | -m <msg>] [--reset-author] [--allow-empty]
                  [--allow-empty-message] [--no-verify] [-e] [--author=<author>]
                  [--date=<date>] [--cleanup=<mode>] [--[no-]status]
                  [-i | -o] [--pathspec-from-file=<file> [--pathspec-file-nul]]
                  [(--trailer <token>[(=|:)<value>])...] [-S[<keyid>]]
                  [--] [<pathspec>...]

    -q, --[no-]quiet      suppress summary after successful commit
    -v, --[no-]verbose    show diff in commit message template

Commit message options
    -F, --[no-]file <file>
                          read message from file
    --[no-]author <author>
                          override author for commit
    --[no-]date <date>    override date for commit
    -m, --[no-]message <message>
                          commit message
    -c, --[no-]reedit-message <commit>
                          reuse and edit message from specified commit
    -C, --[no-]reuse-message <commit>
                          reuse message from specified commit
    --[no-]fixup [(amend|reword):]commit
                          use autosquash formatted message to fixup or amend/reword specified commit
    --[no-]squash <commit>
                          use autosquash formatted message to squash specified commit
    --[no-]reset-author   the commit is authored by me now (used with -C/-c/--amend)
    --trailer <trailer>   add custom trailer(s)
    -s, --[no-]signoff    add a Signed-off-by trailer
    -t, --[no-]template <file>
                          use specified template file
    -e, --[no-]edit       force edit of commit
    --[no-]cleanup <mode> how to strip spaces and #comments from message
    --[no-]status         include status in commit message template
    -S, --[no-]gpg-sign[=<key-id>]
                          GPG sign commit

Commit contents options
    -a, --[no-]all        commit all changed files
    -i, --[no-]include    add specified files to index for commit
    --[no-]interactive    interactively add files
    -p, --[no-]patch      interactively add changes
    -o, --[no-]only       commit only specified files
    -n, --no-verify       bypass pre-commit and commit-msg hooks
    --verify              opposite of --no-verify
    --[no-]dry-run        show what would be committed
    --[no-]short          show status concisely
    --[no-]branch         show branch information
    --[no-]ahead-behind   compute full ahead/behind values
    --[no-]porcelain      machine-readable output
    --[no-]long           show status in long format (default)
    -z, --[no-]null       terminate entries with NUL
    --[no-]amend          amend previous commit
    --no-post-rewrite     bypass post-rewrite hook
    --post-rewrite        opposite of --no-post-rewrite
    -u, --[no-]untracked-files[=<mode>]
                          show untracked files, optional modes: all, normal, no. (Default: all)
    --[no-]pathspec-from-file <file>
                          read pathspec from file
    --[no-]pathspec-file-nul
                          with --pathspec-from-file, pathspec elements are separated with NUL character

philr@3245-Laptop:~/Programieren/repos/PP5$ git commit -m "feature commit"
[feature-1 b900b9d] feature commit
 1 file changed, 3 insertions(+)
 create mode 100644 feature.txt
philr@3245-Laptop:~/Programieren/repos/PP5$ git log
commit b900b9d356d06a10aada3655412a92a1f4ae4101 (HEAD -> feature-1)
Author: Filz <phil.reinartz@gmx.de>
Date:   Sat May 17 10:48:57 2025 +0200

    feature commit

commit 7814dc9139a3683e72cf8d0fa8f07e3fdbe55849 (master)
Author: Filz <phil.reinartz@gmx.de>
Date:   Sat May 17 10:45:13 2025 +0200

    Test
philr@3245-Laptop:~/Programieren/repos/PP5$ git merge feature master
merge: feature - not something we can merge
philr@3245-Laptop:~/Programieren/repos/PP5$ git merge feature-1 master
Already up to date.
philr@3245-Laptop:~/Programieren/repos/PP5$ git log
commit b900b9d356d06a10aada3655412a92a1f4ae4101 (HEAD -> feature-1)
Author: Filz <phil.reinartz@gmx.de>
Date:   Sat May 17 10:48:57 2025 +0200

    feature commit

commit 7814dc9139a3683e72cf8d0fa8f07e3fdbe55849 (master)
Author: Filz <phil.reinartz@gmx.de>
Date:   Sat May 17 10:45:13 2025 +0200

    Test
philr@3245-Laptop:~/Programieren/repos/PP5$ git merge master feature-1
Already up to date.
philr@3245-Laptop:~/Programieren/repos/PP5$ ls
feature.txt  sens.txt
philr@3245-Laptop:~/Programieren/repos/PP5$ git log
commit b900b9d356d06a10aada3655412a92a1f4ae4101 (HEAD -> feature-1)
Author: Filz <phil.reinartz@gmx.de>
Date:   Sat May 17 10:48:57 2025 +0200

    feature commit

commit 7814dc9139a3683e72cf8d0fa8f07e3fdbe55849 (master)
Author: Filz <phil.reinartz@gmx.de>
Date:   Sat May 17 10:45:13 2025 +0200

    Test
philr@3245-Laptop:~/Programieren/repos/PP5$ git checkout master
Switched to branch 'master'
philr@3245-Laptop:~/Programieren/repos/PP5$ ls
sens.txt
philr@3245-Laptop:~/Programieren/repos/PP5$ git merge feature
merge: feature - not something we can merge
philr@3245-Laptop:~/Programieren/repos/PP5$ git merge feature-1
Updating 7814dc9..b900b9d
Fast-forward
 feature.txt | 3 +++
 1 file changed, 3 insertions(+)
 create mode 100644 feature.txt
philr@3245-Laptop:~/Programieren/repos/PP5$ git log
commit b900b9d356d06a10aada3655412a92a1f4ae4101 (HEAD -> master, feature-1)
Author: Filz <phil.reinartz@gmx.de>
Date:   Sat May 17 10:48:57 2025 +0200

    feature commit

commit 7814dc9139a3683e72cf8d0fa8f07e3fdbe55849
Author: Filz <phil.reinartz@gmx.de>
Date:   Sat May 17 10:45:13 2025 +0200

    Test
philr@3245-Laptop:~/Programieren/repos/PP5$
```

---

### Task 2: Bare Repository on an SSH Server

1. On your SSH server (e.g., “vorlesungsserver”), create a **bare** repo at `~/repos/myproject.git`:

   ```bash
   ssh youruser@vorlesungsserver \
     "mkdir -p ~/repos/myproject.git && cd ~/repos/myproject.git && git init --bare"
   ```
2. On your local machine, add it as a remote named `origin-ssh`:

   ```bash
   git remote add origin-ssh youruser@vorlesungsserver:~/repos/myproject.git
   ```
3. Push your `master` branch to `origin-ssh`, then clone it into a fresh directory to verify.

**Your Commands & Output**

```bash
# Paste here the push & clone commands and outputs
philr@3245-Laptop:~/Programieren/repos/PP5$ ssh Vorlesung
 -p ~/repos/myproject.git && cd ~/repos/myproject.git && git init --bare"^[[201~Linux vorlesung 6.1.0-21-amd64 #1 SMP PREEMPT_DYNAMIC Debian 6.1.90-1 (2024-05-03) x86_64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Sat May 17 08:37:33 2025 from 91.32.49.226
  "mkdir -p ~/repos/myproject.git && cd ~/repos/myproject.git && git init --bare"^[[201~user12@vorlesung:~$   "mkdir -p ~/repos/myproject.git && cd ~/repos/myproject.git && git init --bare"~^C
user12@vorlesung:~$ cd
user12@vorlesung:~$ ls
user12@vorlesung:~$ mkdir -p ~/repos/myproject.git && cd ~/repos/myproject.git && git init --bare
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint:
hint:   git config --global init.defaultBranch <name>
hint:
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint:
hint:   git branch -m <name>
Initialized empty Git repository in /home/user12/repos/myproject.git/
user12@vorlesung:~/repos/myproject.git$ exit
logout
Connection to 128.140.85.215 closed.
philr@3245-Laptop:~/Programieren/repos/PP5$ git remote add origin-ssh Vorlesung:~/repos/myproject.git
philr@3245-Laptop:~/Programieren/repos/PP5$ ls
feature.txt  sens.txt
philr@3245-Laptop:~/Programieren/repos/PP5$ git log
commit b900b9d356d06a10aada3655412a92a1f4ae4101 (HEAD -> master, feature-1)
Author: Filz <phil.reinartz@gmx.de>
Date:   Sat May 17 10:48:57 2025 +0200

    feature commit

commit 7814dc9139a3683e72cf8d0fa8f07e3fdbe55849
Author: Filz <phil.reinartz@gmx.de>
Date:   Sat May 17 10:45:13 2025 +0200

    Test
philr@3245-Laptop:~/Programieren/repos/PP5$ git switch master
Already on 'master'
philr@3245-Laptop:~/Programieren/repos/PP5$ git push
fatal: The current branch master has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin-ssh master

To have this happen automatically for branches without a tracking
upstream, see 'push.autoSetupRemote' in 'git help config'.

philr@3245-Laptop:~/Programieren/repos/PP5$ git push -u origin-ssh master
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 24 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (6/6), 570 bytes | 570.00 KiB/s, done.
Total 6 (delta 0), reused 0 (delta 0), pack-reused 0
To Vorlesung:~/repos/myproject.git
 * [new branch]      master -> master
branch 'master' set up to track 'origin-ssh/master'.
philr@3245-Laptop:~/Programieren/repos/PP5$ cd ..
philr@3245-Laptop:~/Programieren/repos$ mkdir PP5_clone && cd PP5_clone
philr@3245-Laptop:~/Programieren/repos/PP5_clone$ git clone Vorlesung:~/repos/myproject
Cloning into 'myproject'...
remote: Enumerating objects: 6, done.
remote: Counting objects: 100% (6/6), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 6 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (6/6), done.
philr@3245-Laptop:~/Programieren/repos/PP5_clone$ git log
fatal: not a git repository (or any of the parent directories): .git
philr@3245-Laptop:~/Programieren/repos/PP5_clone$ git init
Initialized empty Git repository in /home/philr/Programieren/repos/PP5_clone/.git/
philr@3245-Laptop:~/Programieren/repos/PP5_clone$ git log
fatal: your current branch 'master' does not have any commits yet
philr@3245-Laptop:~/Programieren/repos/PP5_clone$ git clone Vorlesung:~/repos/myproject
fatal: destination path 'myproject' already exists and is not an empty directory.
philr@3245-Laptop:~/Programieren/repos/PP5_clone$ ls
myproject
philr@3245-Laptop:~/Programieren/repos/PP5_clone$ git myproject
git: 'myproject' is not a git command. See 'git --help'.
philr@3245-Laptop:~/Programieren/repos/PP5_clone$ ls
myproject
philr@3245-Laptop:~/Programieren/repos/PP5_clone$ cd myproject
philr@3245-Laptop:~/Programieren/repos/PP5_clone/myproject$ ls
feature.txt  sens.txt
philr@3245-Laptop:~/Programieren/repos/PP5_clone/myproject$

```

---

### Task 3: GitHub & THGA GitLab

1. On [GitHub](github.com), create a new empty repo under your account named `myproject-gh`.
2. On [THGA GitLab](gitlab.thga.de), create a new project named `myproject-gl`.
3. In your local repository, add these as remotes:

   ```bash
   git remote add github  git@github.com:YOUR_USERNAME/myproject-gh.git
   git remote add gitlab  git@gitlab.thga.de:YOUR_USERNAME/myproject-gl.git
   ```
4. Push your `master` branch to both `github` and `gitlab` remotes.

> Hint: You are just adding two more bare-remotes to your already existing repository!

**Your Commands & Output**

```bash
# Paste here the remote‐adding & push outputs
Github:
philr@3245-Laptop:~/Programieren/repos$ mkdir myproject-gh
philr@3245-Laptop:~/Programieren/repos$ cd myproject-gh
philr@3245-Laptop:~/Programieren/repos/myproject-gh$ git init
Initialized empty Git repository in /home/philr/Programieren/repos/myproject-gh/.git/
philr@3245-Laptop:~/Programieren/repos/myproject-gh$ git remote add github github.com:279789/myproject-gh.git
philr@3245-Laptop:~/Programieren/repos/myproject-gh$ vim github.txt
philr@3245-Laptop:~/Programieren/repos/myproject-gh$ git add github.txt
philr@3245-Laptop:~/Programieren/repos/myproject-gh$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   github.txt

philr@3245-Laptop:~/Programieren/repos/myproject-gh$ git commit -m "Github test"
[master (root-commit) d6cd4b6] Github test
 1 file changed, 1 insertion(+)
 create mode 100644 github.txt
philr@3245-Laptop:~/Programieren/repos/myproject-gh$ git push -u github master
Enter passphrase for key '/home/philr/.ssh/Githubkey':
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 228 bytes | 228.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote:
remote: Create a pull request for 'master' on GitHub by visiting:
remote:      https://github.com/279789/myproject-gh/pull/new/master
remote:
To github.com:279789/myproject-gh.git
 * [new branch]      master -> master
branch 'master' set up to track 'github/master'.
philr@3245-Laptop:~/Programieren/repos/myproject-gh$

Gitlab:

philr@3245-Laptop:~$ cd .ssh
philr@3245-Laptop:~/.ssh$ ls
Aspire  Aspire.pub  Githubkey  Githubkey.pub  config  known_hosts  known_hosts.old  user12  user12.pub
philr@3245-Laptop:~/.ssh$ ssh-keygen -t ed25519 -f THGA_Gitlab -C "Gitlab Server Thga"
Generating public/private ed25519 key pair.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in THGA_Gitlab
Your public key has been saved in THGA_Gitlab.pub
The key fingerprint is:
SHA256:ua+lzBpSqdbZ/yriOWRb5pQcTNT/pCGmAVaMh3C6ymQ Gitlab Server Thga
The key's randomart image is:
+--[ED25519 256]--+
|    ...*o.       |
|     o= + .      |
|    .. =   .     |
|     . .+.o o .  |
|  E . o.S* . =   |
| + . +ooB.  . .  |
|  o +o+*o .      |
|   . .+=o=       |
|     .++=o+o.    |
+----[SHA256]-----+
philr@3245-Laptop:~/.ssh$ vim THGA_Gitlab.pub
philr@3245-Laptop:~/.ssh$ cd
philr@3245-Laptop:~$ cd .ssh
philr@3245-Laptop:~/.ssh$ ls -la
total 52
drwx------  2 philr philr 4096 May 17 15:09 .
drwxr-x--- 13 philr philr 4096 May 17 15:09 ..
-rw-------  1 philr philr  411 May  7 16:07 Aspire
-rw-r--r--  1 philr philr   96 May  7 16:07 Aspire.pub
-rw-------  1 philr philr  464 Apr 18 13:08 Githubkey
-rw-r--r--  1 philr philr  102 Apr 18 13:08 Githubkey.pub
-rw-------  1 philr philr  411 May 17 15:07 THGA_Gitlab
-rw-r--r--  1 philr philr  100 May 17 15:07 THGA_Gitlab.pub
-rw-r--r--  1 philr philr  328 May 17 10:37 config
-rw-------  1 philr philr 2934 May 17 10:20 known_hosts
-rw-------  1 philr philr 2098 May 17 10:19 known_hosts.old
-rw-------  1 philr philr  432 May 17 10:30 user12
-rw-r--r--  1 philr philr  114 May 17 10:30 user12.pub
philr@3245-Laptop:~/.ssh$ vim config
philr@3245-Laptop:~/.ssh$ ls
Aspire  Aspire.pub  Githubkey  Githubkey.pub  THGA_Gitlab  THGA_Gitlab.pub  config  known_hosts  known_hosts.old  user12  user12.pub
philr@3245-Laptop:~/.ssh$ cd
philr@3245-Laptop:~$ cd Programieren
philr@3245-Laptop:~/Programieren$ cd repos
philr@3245-Laptop:~/Programieren/repos$ mkdir myproject-gl
philr@3245-Laptop:~/Programieren/repos$ cd myproject-gl
philr@3245-Laptop:~/Programieren/repos/myproject-gl$ git init
Initialized empty Git repository in /home/philr/Programieren/repos/myproject-gl/.git/
philr@3245-Laptop:~/Programieren/repos/myproject-gl$ git remote add gitlab gitlab.thga.de:279789/myproject-gl.git
philr@3245-Laptop:~/Programieren/repos/myproject-gl$ vim gitlab.txt
philr@3245-Laptop:~/Programieren/repos/myproject-gl$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        gitlab.txt

nothing added to commit but untracked files present (use "git add" to track)
philr@3245-Laptop:~/Programieren/repos/myproject-gl$ git add gitlab.txt
philr@3245-Laptop:~/Programieren/repos/myproject-gl$ git commit -m "Gitlabtest"
[master (root-commit) ab1b566] Gitlabtest
 1 file changed, 1 insertion(+)
 create mode 100644 gitlab.txt
philr@3245-Laptop:~/Programieren/repos/myproject-gl$ ls
gitlab.txt
philr@3245-Laptop:~/Programieren/repos/myproject-gl$ git push
fatal: The current branch master has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream gitlab master

To have this happen automatically for branches without a tracking
upstream, see 'push.autoSetupRemote' in 'git help config'.

philr@3245-Laptop:~/Programieren/repos/myproject-gl$ git push -u gitlab master
The authenticity of host 'gitlab.thga.de (195.37.5.155)' can't be established.
ED25519 key fingerprint is SHA256:4+4+prKVzsU8Bw0eBjkbBm86bl9+OinZJIidEMGHpqc.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'gitlab.thga.de' (ED25519) to the list of known hosts.
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 229 bytes | 229.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To gitlab.thga.de:279789/myproject-gl.git
 * [new branch]      master -> master
branch 'master' set up to track 'gitlab/master'.
philr@3245-Laptop:~/Programieren/repos/myproject-gl$
```

---

### Task 4: Fork, Modify, and Pull/Merge Request

1. On GitHub, **fork** one of the repos from the STEMgraph org.
2. Clone your fork locally, create a branch `pp5-changes`, and make a small change (e.g., update the README).
3. Commit and push `pp5-changes` to **your** fork, then open a **Pull Request** against the original repo.
4. Repeat on THGA GitLab: fork another students repository, clone, branch, change, push, and open a **Merge Request**. If your peers opened a merge request to your repository, review and merge or decline it!

**Your PR/MR Links & Descriptions**

* GitHub PR: *paste URL and a one-sentence summary*
* GitLab MR: *paste URL and a one-sentence summary*

---

**Remember:** Stop working after **90 minutes** and record where you stopped!
