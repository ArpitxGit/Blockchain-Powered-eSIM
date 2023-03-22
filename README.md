# Blockchain-Powered-eSIM

## AOSP

##### Building AOSP on Mac is not officially supported. So we may not be able to build all tools.

### Step 1: Setting up File system

The default file system on macOS 10.13 and later which is called Apple File System (APFS) is case-insensitive. But to build AOSP, we need a case-sensitive file system.

##### Createed a case-sensitive file system "aosp" using Disk Utility in mackbook pro 14" 2442, before we can start downloading the code.

Need at least 130GB of space on you system in order to download the source code.

### Step 2: Downloading the source

android team has made an utility called (repo)[https://gerrit.googlesource.com/git-repo/], which helps in managing multiple repositories. We will be using this utility to download android source.

##### Output

Installing `repo` using `brew`  
Running`brew update --auto-update`...
==> Homebrew is run entirely by unpaid volunteers. Please consider donating:
https://github.com/Homebrew/brew#donations

==> Downloading https://formulae.brew.sh/api/formula.jws.json
######################################################################## 100.0%
==> Downloading https://formulae.brew.sh/api/cask.jws.json
######################################################################## 100.0%
==> Fetching repo
==> Downloading https://ghcr.io/v2/homebrew/core/repo/manifests/2.32
######################################################################## 100.0%
==> Downloading https://ghcr.io/v2/homebrew/core/repo/blobs/sha256:3fc56eb1a20b6
==> Downloading from https://pkg-containers.githubusercontent.com/ghcr1/blobs/sh
######################################################################## 100.0%
==> Pouring repo--2.32.arm64_monterey.bottle.tar.gz
🍺 /opt/homebrew/Cellar/repo/2.32: 11 files, 129.2KB
==> Running `brew cleanup repo`...
Disable this behaviour by setting HOMEBREW_NO_INSTALL_CLEANUP.
Hide these hints with HOMEBREW_NO_ENV_HINTS (see `man brew`).
==> `brew cleanup` has not been run in the last 30 days, running now...
Disable this behaviour by setting HOMEBREW_NO_INSTALL_CLEANUP.
Hide these hints with HOMEBREW_NO_ENV_HINTS (see `man brew`).

Created and base directory inside the new volume, where we want to clone all the repos required for building inside the volume we created in first step.  
❯ cd /Volumes/aosp
❯ mkdir source
❯ cd source
Now let's initialise repo. This will create a .repo/ directory with Git repositories for the Repo source code and the manifest files which specifies where the various repositories included in the Android source.
`repo init -u https://android.googlesource.com/platform/manifest`

##### Output

Downloading Repo source from https://gerrit.googlesource.com/git-repo
repo: Updating release signing keys to keyset ver 2.3
warning: gpg (GnuPG) is not available.
warning: Installing it is strongly encouraged.

Your identity is: ArpitxGit <arpitxdungeon@gmail.com>
If you want to change this, please re-run 'repo init' with --config-name

Testing colorized output (for 'repo diff', 'repo status'):
black red green yellow blue magenta cyan white
bold dim ul reverse
Enable color display in this user account (y/N)? y

repo has been initialized in /Volumes/aosp/source

Now cloning the source. Also remember to pass the -c, it will tell repo clone only master branch, else it will try to clone all the branches. Optionally you can pass the -j flag to specify number of threads for faster cloning.  
`repo sync -c -j8`  
Stuck here a whole night
