# git_commands

### Man Git
- O manual do git

---

## Trocando de branch
`git switch`  
`git switch -c`  
- Cria uma branch caso não haja  

---

### Ver minhas configs do git
`cat ~/.gitconfig`

---

## Reset
O comando `git reset` pode ser usado para desfazer o(s) últPorque vocimo(s) commit(s) ou quaisquer alterações no índice (alterações em stage, mas não submetidas ao commit) e na árvore de trabalho (alterações não stage e não submetidas ao commit).

`git reset --soft COMMITHASH`  
- Preserva as alterações na área de stage

`git reset --hard COMMITHASH`  
- Descarta todas as mudanças e volta para o commit  
- Funciona para apagar alterações na área de stage que não foram commitadas  
- **Comando PERIGOSO!**

---

### Remote
`git remote add <name> <uri>`  
- Adiciona repositório remoto  

`git fetch`  
- Faz o download dos objetos e refs do outro repositório  
- Não traz todos os arquivos para o working directory, apenas atualiza o histórico  

`git log remote/branch`  
- Visualiza os commits da branch remota  

`git merge remote/branch`  
- Faz um merge da remota na local, criando um *fast-forward* limpo  
- **Nota:** na prática, raramente se usa `git merge` puro para atualizar a branch; o mais comum é usar `git rebase` para manter o histórico linear

---

### Github 
`curl -sS https://webi.sh/gh | sh`  
- Instala o GitHub CLI que facilita a autenticação  

`gh auth login`  
- Realiza a autenticação  

`git push <remote> <branch_local>`  
- Envia de uma branch local para uma branch remota  

---

## Rebase
`git rebase`  
- Reaplica seus commits locais por cima de outro branch, criando um histórico linear e sem commits de merge desnecessários  
- Muito usado no lugar do `git merge` ao atualizar branches

---

## Rebase interativo
`git rebase -i <base>`  
- Permite editar o histórico local antes de enviar para o remoto  
- Possibilidades:
  - Reordenar commits
  - Juntar commits (`squash`)
  - Editar mensagens
  - Excluir commits  
- Muito útil para limpar o histórico e deixar os commits organizados

---

## Configurar pull com rebase
`git config --global pull.rebase true`  
- Define que todo `git pull` fará rebase ao invés de merge por padrão  
- Isso evita commits de merge automáticos ao atualizar do remoto e mantém o histórico linear  
- É muito raro usar `git merge` puro nesse fluxo

---

## Fiz cagada
Ver comandos para voltar a branch no **#Reset**  

`git commit --amend -m "<message>"`  
- Reescreve a mensagem do commit

---

## Log customizado
`git log --oneline --decorate --graph --parents -5`  
- **`--oneline`** → mostra cada commit em uma única linha (hash abreviado + mensagem).  
- **`--decorate`** → exibe referências associadas ao commit (tags, branches).  
- **`--graph`** → desenha o grafo ASCII representando a estrutura de commits e merges.  
- **`--parents`** → mostra o(s) commit(s) pai(s) de cada commit, útil para analisar merges e bifurcações.  

**Exemplo:**  
```bash
git log --oneline --decorate --graph --parents
```

My Solo Workflow
When I'm working by myself, I usually stick to a single branch, main. I mostly use Git on solo projects to keep a backup remotely and to keep a history of my changes. I only rarely use separate branches.

Make changes to files
git add . (or git add <files> if I only want to add specific files)
git commit -m "a message describing the changes"
git push origin main
It really is that simple for most solo work. git log, git reset, and some others are, of course, useful from time to time, but the above is the core of what I do day-to-day.
<img width="930" height="436" alt="image" src="https://github.com/user-attachments/assets/179784e0-8831-49d5-9381-cc867c0fa682" />

### Meus Alias
nano ~/.bashrc       # Bash
nano ~/.zshrc        # Zsh
nano ~/.config/fish/config.fish  # Fish
gl = git log --oneline --decorate --graph --parents
grs = git reset --soft
grh = git  reset --hard
gs = git switch
gb = git branch
gr = git rebase
