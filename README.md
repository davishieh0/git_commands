# git_commands

## Reset
O comando git reset pode ser usado para desfazer o(s) último(s) commit(s) ou quaisquer alterações no índice (alterações em stage, mas não submetidas ao commit) e na árvore de trabalho (alterações não stage e não submetidas ao commit).

git reset --soft COMMITHASH
- Preserva as alterações num stage area

git reset --hard COMMITHASH 
- Descarta todas as mudanças e volta para o o commit
- Funciona para apagar alterações no stage area, que não foram commitadas.
- Comando PERIGOSO!

### Remote
git remote add <name> <uri>
- Adiciona repositório remoto

git fetch 
-  Faz o download dos objetos e refs do outro repositório
- Não temos todos os arquivos
- 
git log remote/branch
- Visualizo os commits da branch remota

git merge remote/branch
- Faz um merge da remota na local, criando um fast-foward limpo
### Github 
curl -sS https://webi.sh/gh | sh
- Instala o github CLI que facilita a autenticação

gh auth login
- Realizar autenticacao

git push <remote> <branch_local>
- Envia de uma branch local para uma branch remota

## Fiz cagada
ver comandos para voltar a branch no #Reset

git commit --amend -m "<message>"
- Reescreve a mensagem do commit

My Solo Workflow
When I'm working by myself, I usually stick to a single branch, main. I mostly use Git on solo projects to keep a backup remotely and to keep a history of my changes. I only rarely use separate branches.

Make changes to files
git add . (or git add <files> if I only want to add specific files)
git commit -m "a message describing the changes"
git push origin main
It really is that simple for most solo work. git log, git reset, and some others are, of course, useful from time to time, but the above is the core of what I do day-to-day.

My Team Workflow
When you're working with a team, Git gets a bit more involved (and we'll cover more of this in part 2 of this course). Here's what I do:

Update my local main branch with git pull origin main
Checkout a new branch for the changes I want to make with git switch -c <branchname>
Make changes to files
git add .
git commit -m "a message describing the changes"
git push origin <branchname> (I push to the new branch name, not main)
Open a pull request on GitHub to merge my changes into main
Ask a team member to review my pull request
Once approved, click the "Merge" button on GitHub to merge my changes into main
Delete my feature branch, and repeat with a new branch for the next set of changes
