---
layout: post
title: "How to Use Multiple GitHub Accounts using SSH on Windows"
date: 2023-07-06
categories: git
tags: git github devops
---

## How to have multiple Github accounts on the same computer

## 1. Enable OpenSSH in services.

## 2. Create SSH Keys

1. Open PowerShell ([for help](https://explainshell.com/))
2. Add command for the default account (personal recommended first)

```bash
ssh-keygen -t rsa -b 4096 -C "juanpablodiaz"
```

3. Enter the path location where you want to save the key (personal_key)

```text
C:\Users\juanc\.ssh\juanpablodiaz_key
```

4. The key has been generated. To check, go to the folder where you save it.
5. Add next Github account. (example: Github for work)

```bash
ssh-keygen -t rsa -b 4096 -C "1diazdev"
```

6. Enter the path location where you want to save the key

```text
C:\Users\juanc\.ssh\1diazdev_key
```

7. The key has been generated. To check, go to the folder where you save it.

## 3. Create SSH Config File

1. Open the file explorer in the folder where both keys are stored
2. Create the file `config`
3. Open the file in VScode and add the info below:

```bash
# juanpablodiaz Github
Host juanpablodiaz
  Hostname github.com
  User git
  IdentityFile ~/.ssh/juanpablodiaz_key
  IdentitiesOnly yes

# 1diazdev Github
Host 1diazdev
  Hostname github.com
  User git
  IdentityFile ~/.ssh/1diazdev_key
  IdentitiesOnly yes
```

## 4. Add Keys to Gothub

1. Go to github.com and login
2. Go to menu > Setting > SSH and GPG keys > new SSH keys
3. Add the public key and save.
4. Repet the process on the other Github account.

## 5. Add Keys to OpenSSH Cache

This is to prevent having to login to github everytime I interact with github.com.

1. Open PowerShell and add the command (this will add the private key)

```bash
ssh-add C:\Users\juanc\.ssh\juanpablodiaz_key
```

2. Repet the process for the other account (adding the private key)

```bash
ssh-add C:\Users\juanc\.ssh\1diazdev_key
```

3. To test this add the code

```bash
   ssh -Tv juanpablodiaz
```

4. And

```bash
   ssh -Tv 1diazdev
```

## 6. Preparing Folder Structure

1. Create two folders inside a github folder

- `C:\Users\juanc\Documents\Github\juanPabloDiaz`

- `C:\Users\juanc\Documents\Github\1diazdev`

2. In the `Users\juanc` folder, Create 3 files:

- `.gitconfig`
- `.gitconfig-juanpablodiaz`
- `.gitconfig-1diazdev`

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

4. Open the `.gitconfig-juanpablodiaz` and add the following code:

```bash
[user]
	name = juanpablodiaz
	email = juanchodis@hotmail.com
[core]
	sshCommand = ssh -i ~.ssh/juanpablodiaz_key
```

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

1. Go to github and find the repo
2. From the SSH link in github
   example

```bash
  git@github.com:JuanPabloDiaz/repoName.git
```

You will only copy and use:

```bash
  JuanPabloDiaz/repoName.git
```

3. Add the code to that especific folder repo (JuanPabloDiaz/repoName.git)

```bash
git remote set-url origin juanpablodiaz:JuanPabloDiaz/repoName.git
```

example:

```bash
git remote set-url origin juanpablodiaz:JuanPabloDiaz/doc.git
or
git remote set-url origin 1diazdev:1diazdev/JuanDiaz.git
```

4. Test doing a `git pull`

### Command to add a new repo from Github to local

```bash
git clone juanpablodiaz:JuanPabloDiaz/repoName.git
```

or

```bash
git clone 1diazdev:1diazdev/repoName.git
```

Test doing a `git pull`

<!-- ACKNOWLEDGMENTS -->

## Acknowledgments 📚

Resources list that I find helpful and would like to give credit to.

- [@jc_miron Video](https://www.youtube.com/watch?v=6lA0oPoFCAE)
