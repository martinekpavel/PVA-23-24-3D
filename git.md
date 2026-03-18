# Git

### Create a new repository on the command line (and connect to Github)

```
echo "# PVA-23-24-3D" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/martinekpavel/PVA-23-24-3D.git
git push -u origin main
```

### ... or push an existing repository from the command line

```
git remote add origin https://github.com/martinekpavel/PVA-23-24-3D.git
git branch -M main
git push -u origin main
```

## Pokud vytvořím nějaký kód a chci si ho uložit na github

1. Nejdříve vytvořím repozitář na github.com, nechci se chlubit kódem, takže soukromý, nebudu přidávat žádné soubory, nic. Objeví se obrázek níže a kliknu si na ssh.

2. Vlezu si do složky na serveru, počítači, kdekoliv potřebuji a zadám:

```cmd
git config --global init.defaultBranch main
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```

Na linuxovém serveru postupuji podle tohoto návodu.
[https://dev.to/jajera/how-to-configure-ssh-for-github-authentication-2b53](https://dev.to/jajera/how-to-configure-ssh-for-github-authentication-2b53)

```cmd
ls -al ~/.ssh
ssh-keygen -o -a 100 -t ed25519 -f ~/.ssh/id_ed25519_github -C "ssh key for github"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519_github
nano ~/.ssh/config
```

Obsah souboru
```
Host github.com
  IdentityFile ~/.ssh/id_ed25519_github
  AddKeysToAgent yes
```

```cmd
cat ~/.ssh/id_ed25519_github.pub
```
Now, go to GitHub > Settings > SSH and GPG Keys and click New SSH Key. Paste the copied key and save it.

3. A potom nakonfiguruji repozitář

```cmd
git init
git add *
git commit -m "first commit"
git remote add origin git@github.com:martinekpavel/oahosting.git
git push -u origin main
```

a hotovo! 

