
## Git and Github

### Setting up your environment

```ps1
git config --global user.name "Amit Naik"

git config --global user.email "amit.naik8103@gmail.com"

git config --edit --global
```

```
git --version
git --help
git --help config
```
- Push an existing Repository
```
git init
git remote add origin 'git_url'
git push -u origin master
```
- Clone a remote Repository
```
git clone <git_url>
git remote -v
``````
- Git Configuration
```
git config --list
git config --list --show-origin
```