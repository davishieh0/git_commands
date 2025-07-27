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
