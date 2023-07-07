---
layout: post
title: "How to Use Multiple GitHub Accounts using SSH on Windows"
date: 2023-07-06
categories: git
tags: git github devops
image: /assets/img/featured-posts/github.jpg
---

Have you ever desired to manage multiple GitHub accounts on the same computer but lacked the knowledge on how to accomplish it? Fear not, for it is a simple task requiring only a small portion of code.

## 1. [Enable OpenSSH](https://dev.to/jasoncruzdev/activating-your-openssh-authentication-agent-in-windows-10-1fdh)

1. In windows, open the "Services" app and search for **OpenSSH Authentication Agent**
2. Right click over `OpenSSH Authentication Agent`, then `Properties`
3. Set the startup type to `Automatic`
4. `Apply` changes and click `start`. Then close it.

## 2. Create SSH Keys[^SSH]

1. Open PowerShell[^help]
2. Add command for the default account (personal recommended first)

```bash
ssh-keygen -t rsa -b 4096 -C "juanpablodiaz"
```

{:start="3"}

3. Enter the path location where you want to save the key (personal_key)

```text
C:\Users\juanc\.ssh\juanpablodiaz_key
```

{:start="4"}

4. The key has been generated. To check, go to the folder where you save it.
5. Add next GitHub account. (example: GitHub for work)

```bash
ssh-keygen -t rsa -b 4096 -C "1diazdev"
```

{:start="6"}

6. Enter the path location where you want to save the key

```text
C:\Users\juanc\.ssh\1diazdev_key
```

{:start="7"}

7. The key has been generated. To check, go to the folder where you save it.

## 3. Create SSH Config File

1. Open the `file explorer` in the folder where both keys are stored
2. Create the `config` file
3. Open the file in VScode and add the info below:

```bash
# juanpablodiaz GitHub
Host juanpablodiaz
  Hostname github.com
  User git
  IdentityFile ~/.ssh/juanpablodiaz_key
  IdentitiesOnly yes

# 1diazdev GitHub
Host 1diazdev
  Hostname github.com
  User git
  IdentityFile ~/.ssh/1diazdev_key
  IdentitiesOnly yes
```

## 4. [Add Keys to GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

1. Go to [GitHub.com](https://github.com/) and login
2. Go to `Menu` > `Setting` > `SSH and GPG keys` > `new SSH keys`
3. Add the public key and save.
4. Repet the process on the other GitHub account.

## 5. Add Keys to OpenSSH Cache

This is to prevent having to login to GitHub everytime I interact with [GitHub.com](https://github.com/).

1. Open PowerShell and add the command (this will add the private key)

```bash
ssh-add C:\Users\juanc\.ssh\juanpablodiaz_key
```

{:start="2"}

2. Repet the process for the other account (adding the private key)

```bash
ssh-add C:\Users\juanc\.ssh\1diazdev_key
```

{:start="3"}

3. To test this add the code

```bash
   ssh -Tv juanpablodiaz
```

{:start="4"}

4. And

```bash
   ssh -Tv 1diazdev
```

## 6. Preparing Folder Structure

1. Create two folders inside a GitHub folder

- `C:\Users\juanc\Documents\Github\juanPabloDiaz`

- `C:\Users\juanc\Documents\Github\1diazdev`

{:start="2"}

2. In the `Users\juanc` folder, Create 3 files:

- `.gitconfig`
- `.gitconfig-juanpablodiaz`
- `.gitconfig-1diazdev`

{:start="3"}

3. In my case, the `.gitconfig` file was already created.

- Open and replace it with the following:

```bash
[filter "lfs"]
	clean = git-lfs clean -- %f
	smudge = git-lfs smudge -- %f
	process = git-lfs filter-process
	required = true
[includeIf "gitdir:C:Users/juanc/Documents/Github/juanPabloDiaz"]
	path = ./.gitconfig-juanpablodiaz

[includeIf "gitdir:C:\Users/juanc/Documents/Github/1diazdev"]
	path = ./.gitconfig-1diazdev
[user]
	name = Juan Diaz
	email = juanchodis@hotmail.com
[core]
	sshCommand = C:/Windows/System32/OpenSSH/ssh.exe
```

{:start="4"}

4. Open the `.gitconfig-juanpablodiaz` and add the following code:

```bash
[user]
	name = juanpablodiaz
	email = juanchodis@hotmail.com
[core]
	sshCommand = ssh -i ~.ssh/juanpablodiaz_key
```

{:start="5"}

5. Open the `.gitconfig-1diazdev` and add the following code:

```bash
[user]
	name = 1diazdev
	email = juan.diaz.rodriguez93@gmail.com
[core]
	sshCommand = ssh -i ~.ssh/1diazdev_key
```

## 7. Preparing Folder Structure

### A. Link the existing repos to the new SSH

1. Go to [GitHub.com](https://github.com/) and find the repo
2. Copy the last part of the SSH link.

   > - SSH link: `git@github.com:JuanPabloDiaz/repoName.git`<br>
   > - Copy: `JuanPabloDiaz/repoName.git`

{:start="3"}

3. Add the [SSH link][id1] to that especific folder repo

[id1]: ## "JuanPabloDiaz/repoName.git"

```bash
git remote set-url origin juanpablodiaz:JuanPabloDiaz/repoName.git
```

Example:

```bash
git remote set-url origin juanpablodiaz:JuanPabloDiaz/doc.git
or
git remote set-url origin 1diazdev:1diazdev/JuanDiaz.git
```

{:start="4"}

4. Test it by doing a `git pull`

### Command to add a new repo from GitHub to local

```bash
git clone juanpablodiaz:JuanPabloDiaz/repoName.git
```

or

```bash
git clone 1diazdev:1diazdev/repoName.git
```

Test it by doing a `git pull`

<!-- ACKNOWLEDGMENTS -->

## Acknowledgments 📚

Resources list that I find helpful and would like to give credit to.

- [@jc_miron video](https://www.youtube.com/watch?v=6lA0oPoFCAE)

<br>

---

<!-- ## Footnote -->

[^SSH]:
    SSH or Secure Shell is a network communication protocol that enables two computers to communicate.<br>
    Go to [GitHub Doc](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)

[^help]:
    [PowerShell](https://learn.microsoft.com/en-us/powershell/) is a task automation and configuration management program from Microsoft, consisting of a command-line shell and the associated scripting language.<br>
    To undestand better any line of code in PowerShell visit ([Explain Shell](https://explainshell.com/))
