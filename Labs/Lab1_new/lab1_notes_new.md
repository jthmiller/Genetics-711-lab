# Lab 2 (First in person)

## SSH into RON
<!-- is this still true? -->
Username = `student UNH id` 

Password = `id+ zfG1`

<details><summary><i>example</i></summary>

- `kcd1021`
- `kcd1021zfG1`
</details> <!-- end examples --> 
<br>

Example login
``` 
ssh kcd1021@ron.sr.unh.edu
``` 

**Students are required to change their password after first login**

## SSH Key

- VSCode remote work site [see here](https://code.visualstudio.com/docs/remote/ssh). 

- Terminal to generate ssh key

        cd ~/.ssh
        ssh-keygen -t ed25519 -b 4096
        chmod 400 ~/.ssh/id_ed25519

- Next, share the public key with the Ron server

        ssh-copy-id username@ron.sr.unh.edu


## GitHub

- Clone their forked repos onto Ron

```
git clone https://github.com/<username>/<repo>
```


- Lab notebook
  - VSCode: 'file' → 'new text file'. Save this empty file as 'lastname_firstname.md'. (replacing with your last/firstname). 
  - nano: 

        nano lastname_firstname.md

**remind students importance of good notes, they will be graded, and can/will be used throughout classes**

- Have students use VSCode's built in git source control to upload to github, and have students check that the changes were made

    - you can use the `source control` tab in VS Code
    - or through the terminal 

```
git add lastname_firstname.md
git commit -m "update notes"
git push
```

- through terminal may cause some issues
  - github keys: developer options -> classic
    - insert as password when prompted

## Learning Git fetch/ merge
- Save your VS Code workspace in your repo on RON. Go to 'File' → 'Save Workspace As' and save it to the 'gen711-811' folder on RON. This way, you can load this workspace each week to pick up where you left off. 

- To get new course files added to your repository later, you will need to add the original repository (the one you forked) as a 'remote' 

    - [help](https://stackoverflow.com/questions/3903817/pull-new-updates-from-original-github-repository-into-forked-github-repository)
    -  [and more help](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo)  

<!-- https://www.cs.unh.edu/~cs925/assignments/gitlab.html -->

- To add updates from the gen711-811 repo:

```
cd gen711-811
git remote add upstream https://github.com/jthmiller/gen711-811.git
git fetch upstream
git merge upstream/master master
```

- Note, git merge is like "git pull" which is fetch + merge. Or, better, you can replay your local work on top of the fetched branch like a "git pull --rebase"

```
git rebase upstream/master
```

## Optional Portion of Lab

- if we somehow make it through ssh and github keys

<details><summary><i>full terminal</i></summary>

- nano
- tmux

```
tmux new -s "session name"
tmux attach -t "session name
```

- command/b d: exits tmux session
- command/b %: creates horizontal pane
- command/b ": creates vertical pane
- command/b x: deletes current pane
- command/b arrow key: change current pane to direction of arrow

</details> <!-- end  tmux --> 

<details><summary><i>changing PS1</i></summary>

- PS1 is `Prompt String 1`
- allows you to change what you see in the command prompt

- temporary

```
PS1="🎅\[\e[33;41m\][\[\e[m\]\[\e[32m\]\u\[\e[m\]\[\e[36m\]@\[\e[m\]\[\e[34m\]\h\[\e[m\]\[\e[33;41m\]]\[\e[m\]🎄 "
```

- add `export out front to make it permanent`

[details on what does what](https://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html)

</details> <!-- end  PS1 --> 

<details><summary><i>VS Code Extensions</i></summary>

- important ones 
  - Dracula Official
  - Indent Rainbow
  - Rainbow CSV
- silly ones
  - vscode-pets

</details> <!-- end  PS1 --> 

 
