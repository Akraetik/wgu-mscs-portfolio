# D796 — Unix and Linux

**Course 5 of 10** · May 8 – 18, 2026 · 1 performance task (scripts + flowchart + recorded demo)

**Time:** 11 calendar days · ~7 hours on WGU work · ~25 hours of outside courses 

**How it went:** Only about 7 hours of coursework. Three weeks of pwn.college's Linux course before the program did most of the work. The rest of the calendar went to the LPI Linux Essentials course, Vim, and x86 assembly.

This class is basically an introduction to LINUX and scripting and there are plenty of quality resources for this. I recommend PWN.College or directed study towards a certificate (LPIC/LINUX+/RHCSA)

## In one line

I wrote Bash scripts that create and safely delete user accounts, customized the shell environment, and demoed it all live on video.

## What the course covers

The Unix/Linux command line for sysadmin and developer work: common commands, navigating the shell, managing files, configuring the environment, and writing shell scripts to automate routine tasks.

## What I did

**`create_user.sh`**
- Fails fast with exit code 1 if no username is given (`[ -z "$1" ]`).
- Creates a group only if it doesn't exist (`getent group … > /dev/null 2>&1`).
- `useradd -m -G <group> -s /bin/bash` creates the user, home directory, group membership, and shell in one step.
- Sets a temporary password non-interactively (`chpasswd`), then forces a change at first login (`chage -d 0`).
- Confirms the account by grepping `/etc/passwd`.

**`delete_user.sh`**
- Same input check.
- Asks for typed confirmation (`read -p`) before anything destructive.
- Checks the user exists (`id`), then removes the account and home directory (`userdel -r`).
- Checks the exit code (`$?`) and shows the result.

**Shell customization**
- A two-color `PS1` prompt using ANSI escape codes.
- An aliases file (`ll`, `la`, `cls`, and more), sourced from `.bashrc`.
- `~/bin` added to `PATH` so scripts run from anywhere.

**Delivery:** a flowchart of each script's logic and a recorded live demo, including the failure paths (no argument, typing "no", deleting a user who doesn't exist).

Environment: Ubuntu on WSL2, edited in Nano and Vim.

## Skills used

`Bash` `useradd / userdel / groupadd` `chpasswd` `chage` `getent` `exit codes` `I/O redirection` `PS1` `aliases` `PATH` `.bashrc` `WSL2` `Vim`

## What I'd do differently

- **No hard-coded passwords.** The script stored a temporary password in plain text. Better: generate one (`openssl rand -base64 12`) and print it once, or use `passwd -e` with a key-based login.
- **Add `set -euo pipefail`** so the script stops on any error, not only the ones I checked.
- **Check for root at the top** (`[ "$EUID" -ne 0 ]`) instead of relying on the operator to type `sudo`.
- **Log every account change** to a file with a timestamp. That's an audit trail.

## Key ideas worth knowing

- Unix vs. Linux; the kernel vs. the shell; CLI vs. GUI
- File permissions (`chmod`, `chown`, octal modes), users and groups, `/etc/passwd` vs. `/etc/shadow`
- stdin / stdout / stderr; `>`, `>>`, `2>&1`, `/dev/null`; pipes
- Login vs. non-login shells; `.bash_profile` vs. `.bashrc`; `source`
- Environment variables, `export`, PATH
- Vim modes: normal, insert, visual, command

## Books and reading

### *The Linux Command Line* (2nd ed.)
**William Shotts** · 2019 · No Starch Press · [free online](https://linuxcommand.org/tlcl.php)

**What's in it:** four parts. *Learning the shell* (navigation, files, permissions, processes). *Configuration and the environment* (`.bashrc`, Vim). *Common tasks and essential tools* (packages, storage, networking, regex, text processing). *Writing shell scripts* (variables, flow control, loops, arrays, troubleshooting).

**Thoughts:** Great book if you learn through reading material. It's also something you can download. I recommend it. If you read and learn through reading, that is.

## Outside courses I took for this one

About 25 hours finished, plus pwn.college before the program.

| Course | Platform | Length |
|---|---|---|
| [LPI Linux Essentials (010) Cert Prep](#lpi-linux-essentials-010-cert-prep) | LinkedIn Learning | 7h 12m |
| [Learning Bash Scripting](#learning-bash-scripting) | LinkedIn Learning | 2h 42m |
| [Vim Masterclass](#vim-masterclass) | Udemy | about 3h 40m |
| [Learning VI](#learning-vi) | LinkedIn Learning | 1h 30m |
| [x86 Assembly Language Programming From Ground Up](#x86-assembly-language-programming-from-ground-up) | Udemy | 14h |
| [pwn.college — Linux Luminarium](#pwncollege--linux-luminarium) | pwn.college | free, self-paced |

### LPI Linux Essentials (010) Cert Prep
[LinkedIn Learning](https://www.linkedin.com/learning/lpi-linux-essentials-010-160-cert-prep) · 7h 12m

**Thoughts:** This was a course towards a certificate. It was OKAY and Linkedin Learning is never my favorite but I was eager and new to the program and just did what was linked in the notes. 

### Learning Bash Scripting
[LinkedIn Learning](https://www.linkedin.com/learning/learning-bash-scripting-26210777) · 2h 42m

**Thoughts:** Good review but I had already known this material from PWN.College so it was quickly watched. Good introduction to Bash Scripting, which is LINUX.

### Vim Masterclass
[Udemy](https://www.udemy.com/course/vim-commands-cheat-sheet/?couponCode=PMNVD1525) · about 3h 40m

**Thoughts:** This is something that is thick and takes time to go through and write notes. VIM commands are something you should do often and in small doses to learn and retain. 7.5 hour total course. 

### Learning VI
[LinkedIn Learning](https://www.linkedin.com/learning/search?keywords=Learning+VI) · 1h 30m

**Thoughts:** Part of the course curriculum. Like the previous course it's good to get more VIM. The video game VIM-Adventures is a good supplement https://vim-adventures.com/

### x86 Assembly Language Programming From Ground Up
[Udemy](https://www.udemy.com/courses/search/?q=x86+Assembly+Language+Programming+From+Ground+Up) · 14h

**Thoughts:** This wasn't part of the program and was more connected to what I was doing with assembly languages (x86-64) in PWN.College. It was okay but a tangent. 

### pwn.college — Linux Luminarium
[pwn.college](https://pwn.college/linux-luminarium/) · free, self-paced

**Thoughts:** This took probably 100+ hours to complete. If you don't cheat or use AI for answers it can be difficult. I am not entirely sure that's because it's difficult or the instructions are not fully clear. But it's difficult and challenging and I learned a lot aobut LINUX through this. Also now I believe there is an ASU-backed certificate for completing this if you pay $200.

## Public rebuild (planned)

A hardened user-provisioning script with the fixes above, a system-health report script, a dotfiles folder, and ShellCheck running in GitHub Actions. It will go in `rebuilds/` when it's done. I will do some LINUX stuff in a public rebuild when I have time. I do not know exactly what that will look like yet. But writing short and then later complex scripts in linux is a great output or deliverable. 

I started and mainly used NANO, but VIM is something I am slowly working on incorporating. I recommend either VIM or EMACS as a base but preferences may vary.
