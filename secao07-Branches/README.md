# Seção 07 - Branches:

## Aula 01 - Conceitos sobre Branch:

    https://github.com/DevMasterTeam/Udemy-Git/blob/master/Se%C3%A7%C3%A3o%2007%20-%20Branches/(Slide)%20Conceitos%20sobre%20branch.pdf

Branch é uma ramificaçõ no projeto que permite que funcionalidades sejam desenvolvidas separadamente sem impactar funcionalidades estáveis no projeto.

Uma branch permite realizar testes e ser consideradas apenas aqueles testes que deram certos, usando a mesclagem.

## Aula 02 - Criando Branch local:
Para verificar em qual branch o seu repositório se encontra no local:

- git branch

Para verificar quais branchs a sua local tem:

- git branch --list

Para criamos a branch localmente:

- git branch (nome da branch nova que vc pode denotar)

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch develop
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch --list
    develop
    * main

Para mudar de uma branch para outra:

- git checkout (nome da branch existente)

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git checkout develop
    M	Notas-Aula
    Switched to branch 'develop'
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch
    * develop
    main

No caso, visto que temos duas branchs, não interessa o que acontece na branch develop e isso não influencia nada na branch main.

Para criar uma branch nova no local e ainda mudar para ela:

- git checkout -b (atribuir um nome novo para essa branch)
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch
    develop
    * main
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git checkout -b TASK-1
    Switched to a new branch 'TASK-1'
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch
    * TASK-1
    develop
    main

Obs: Os nomes das branchs não podem ter espaços. Procure sempre conectar com traços.
Temos um caso em que podemos criar ou mudar para uma branch:

- git switch (nome da branch existente)

- git switch - - Esse comando serve para vc voltar na branch anterior.
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git switch develop
    Switched to branch 'develop'
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch
    TASK-1
    * develop
    main
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git switch -
    Switched to branch 'main'
    Your branch is up to date with 'origin/main'.
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch
    TASK-1
    develop
    * main

Obs: Vc consegue ficar alternando entre duas branchs ao ficar rodando "git switch -" toda hora, visto que esse comando faz vc voltar na última branch em que vc esteve.

Vamos usar o git switch para criar uma nova branch:

- git switch -c (nome da branch nova que vc queira criar)

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git switch -c TASK-2
    Switched to a new branch 'TASK-2'
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch
    TASK-1
    * TASK-2
    develop
    main

## Aula 03 - Mudançãs não salvas:
Um ponto importante de mudanças não salvas.

Suponhamos que vc esteja em uma branch realizando as modificações que vc quer e, no meio do processo, vc queria mudar da atual branch para uma outra.

Ao darmos git checkout para uma outra branch e dermos o git status, veremos que as alterações que vc fez na última branch vem para a branch que vc mudou.

Ou seja, vc precisa tomar muito cuidado nisso, pois existem alterações que vc quer que ela fique na branch em que vc estava realizando tais alterações.

No caso, uma boa prática para evitar que isso aconteça seria dando git add e git commit antes de ir para uma outra branch nova.

Existe tbm uma outra alternativa para isso, que é dando o seguinte comando:

- git checkout -f (nome da branch existente) - Esse comando irá dar uma limpa em todas as alterações não rastreadas para mudar de branch.

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch
    TASK-1
    TASK-2
    develop
    * main
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git checkout -f develop
    Switched to branch 'develop'
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch
    TASK-1
    TASK-2
    * develop
    main

Note que, ao darmos um git checkout . ou git checkout -f, e se vc quiser que o arquivo que vc estava modificando volte na forma como vc estava modificando, basta dar Crtl+z ou Command + Z.

## Aula 04 - Detached HEAD:
Vamos começar fazendo o git log --oneline.

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git log --oneline
    a66b0c0 (HEAD -> main, origin/main, origin/HEAD) Atualizando as notas de aula
    51783b7 Atualizando notas de aula
    cc635a1 (TASK-2) Atualizando as notas de aula
    8c83887 Atualizando as notas de aula com o usuario certo
    0fc34ee (TASK-1) Atualizando as notas de aula sobre git - controle de versionamento
    684b766 (develop) Vantagens de pull request para enriquecer o teu curriculo
    0ac21b5 Leituras para Star, Watch e Fork
    3b0342a Atualizacao do titulo
    82864fb Forma de dar push no github - novas regras
    b2c9f7f Versao inicial do site
    cd08034 Commit inicial
    ad8b997 Initial commit

Agora, vamos pegar o penúltimo git para darmos o checkout sobre ele.

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git checkout 51783b7
    Note: switching to '51783b7'.

    You are in 'detached HEAD' state. You can look around, make experimental
    changes and commit them, and you can discard any commits you make in this
    state without impacting any branches by switching back to a branch.

    If you want to create a new branch to retain commits you create, you may
    do so (now or later) by using -c with the switch command. Example:

    git switch -c <new-branch-name>

    Or undo this operation with:

    git switch -

    Turn off this advice by setting config variable advice.detachedHead to false

    HEAD is now at 51783b7 Atualizando notas de aula

O que esse detached HEAD significa?

A tradução dela é "Cabeça destacada"

    https://github.com/DevMasterTeam/Udemy-Git/blob/master/Se%C3%A7%C3%A3o%2007%20-%20Branches/(Slide)%20Detached%20HEAD.pdf

No caso, nela permite que vc faça as alterações sobre ela e que tal alteração não impactará nenhuma outra branch, lembrando que as branchs são independentes.

Vamos experimentar isso modificando o arquivo main.html que temos no diretório Website, o título Aprendendo Git.

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git log --oneline
    a953567 (HEAD -> main, origin/main, origin/HEAD) Atualizando as notas de aula
    b8f4ddf Atualizando as notas de aula
    a66b0c0 Atualizando as notas de aula
    51783b7 Atualizando notas de aula
    cc635a1 (TASK-2) Atualizando as notas de aula
    8c83887 Atualizando as notas de aula com o usuario certo
    0fc34ee (TASK-1) Atualizando as notas de aula sobre git - controle de versionamento
    684b766 (develop) Vantagens de pull request para enriquecer o teu curriculo
    0ac21b5 Leituras para Star, Watch e Fork
    3b0342a Atualizacao do titulo
    82864fb Forma de dar push no github - novas regras
    b2c9f7f Versao inicial do site
    cd08034 Commit inicial
    ad8b997 Initial commit
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git checkout b8f4ddf
    Note: switching to 'b8f4ddf'.

    You are in 'detached HEAD' state. You can look around, make experimental
    changes and commit them, and you can discard any commits you make in this
    state without impacting any branches by switching back to a branch.

    If you want to create a new branch to retain commits you create, you may
    do so (now or later) by using -c with the switch command. Example:

    git switch -c <new-branch-name>

    Or undo this operation with:

    git switch -

    Turn off this advice by setting config variable advice.detachedHead to false

    HEAD is now at b8f4ddf Atualizando as notas de aula
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git status
    HEAD detached at b8f4ddf
    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
        modified:   Website/main.html

    no changes added to commit (use "git add" and/or "git commit -a")
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git switch -c head-example
    Switched to a new branch 'head-example'
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git add .
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git commit -m "Entendendo Detached Head"
    [head-example 552b13d] Entendendo Detached Head
    1 file changed, 1 insertion(+), 1 deletion(-)
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git push
    fatal: The current branch head-example has no upstream branch.
    To push the current branch and set the remote as upstream, use

        git push --set-upstream origin head-example

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git push --set-upstream origin head-example
    Enumerating objects: 7, done.
    Counting objects: 100% (7/7), done.
    Delta compression using up to 16 threads
    Compressing objects: 100% (4/4), done.
    Writing objects: 100% (4/4), 487 bytes | 487.00 KiB/s, done.
    Total 4 (delta 3), reused 0 (delta 0)
    remote: Resolving deltas: 100% (3/3), completed with 3 local objects.
    remote: 
    remote: Create a pull request for 'head-example' on GitHub by visiting:
    remote:      https://github.com/HelloWounderworld/notes-git/pull/new/head-example
    remote: 
    To github.com:HelloWounderworld/notes-git.git
    * [new branch]      head-example -> head-example
    Branch 'head-example' set up to track remote branch 'head-example' from 'origin'

Logo, faltaria dar o git merge para juntarmos as modificações com a branch principal.

## Aula 05 - Enviando branch para o repositório remoto:
O envio já foi feito na aula anterior.

No caso, o comando que foi usado foi:

- git push --set-upstream origin head-example

- git push -u origin head-example - Serviria tbm.

Visto que a tal branch, que não existia remotamente, agora existe remotamente, nos próximos pushs bastar dar o comando "git push".

Agora, uma detalhe curioso.

Quando hávimos dado o git clone de um repositório remoto, foi visto que não era necessário dar nenhum --set-upstream.

Isso é devido ao fato de que a branch main já vem com esse detalhe configurado.

## Aula 06 - Removendo branch local:
O comando para deletar as branchs criadas localmente é:

- git branch -d (nome da branch)

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch
    TASK-1
    TASK-2
    develop
    head-example
    * main
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch -d TASK-1
    Deleted branch TASK-1 (was 0fc34ee).
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch
    TASK-2
    develop
    head-example
    * main

Caso vc queira fazer a remoção de forma forçada, sem que o git te pergunte se realmente quer mesmo remover a tal branch:

- git branch -D (nome da branch)

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch
    TASK-2
    develop
    head-example
    * main
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch -D TASK-2
    Deleted branch TASK-2 (was cc635a1).
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch
    develop
    head-example
    * main

Lembre-se que essa remoção de branch, em ambos os casos, vc estará excluindo até os históricos de commits que vc deu para essa branch.

Por isso, sempre que vc for remover uma branch local, tenha certeza do que esteja fazendo.

## Aula 07 - Removendo branch remota:
O comando para fazer isso, seria:

- git push --delete (caminho) (nome da branch)

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git checkout TASK5
    Switched to branch 'TASK5'
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git status
    On branch TASK5
    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
        modified:   Notas-Aula

    no changes added to commit (use "git add" and/or "git commit -a")
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git add .
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git commit -m "Teste"
    [TASK5 3317431] Teste
    1 file changed, 1 insertion(+), 1 deletion(-)
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git push --set-upstream origin TASK5
    Enumerating objects: 5, done.
    Counting objects: 100% (5/5), done.
    Delta compression using up to 16 threads
    Compressing objects: 100% (3/3), done.
    Writing objects: 100% (3/3), 326 bytes | 326.00 KiB/s, done.
    Total 3 (delta 2), reused 0 (delta 0)
    remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
    remote: 
    remote: Create a pull request for 'TASK5' on GitHub by visiting:
    remote:      https://github.com/HelloWounderworld/notes-git/pull/new/TASK5
    remote: 
    To github.com:HelloWounderworld/notes-git.git
    * [new branch]      TASK5 -> TASK5
    Branch 'TASK5' set up to track remote branch 'TASK5' from 'origin'.
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git push --delete origin TASK5
    To github.com:HelloWounderworld/notes-git.git
    - [deleted]         TASK5

Não se esqueça de que no passo, onde vc deu o git push -u, se certificar que a tal branch de fato se encontra criada no teu repositório.

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git checkout main
    Switched to branch 'main'
    Your branch is up to date with 'origin/main'.
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch
    TASK5
    develop
    head-example
    * main
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch -d TASK5
    error: The branch 'TASK5' is not fully merged.
    If you are sure you want to delete it, run 'git branch -D TASK5'.
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ gt branch -D TASK5

    Comando 'gt' não encontrado, mas poder ser instalado com:

    sudo apt install genometools

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch -D TAKS5
    error: branch 'TAKS5' not found.
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch -D TASK5
    Deleted branch TASK5 (was 3317431).

Note que, o comando que serviu para deletar a branch no repositório, ela não deletou a branch local?

## Aula 08 - Renomeando branch:
O comando para alterar o nome da branch é:

- git branch -m (nome novo para a branch) - Vc precisa tar na branch que quer alterar o nome.

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git checkout -b TASK1
    Switched to a new branch 'TASK1'
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch
    * TASK1
    develop
    head-example
    main
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch -m TASK10
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch
    * TASK10
    develop
    head-example
    main

Caso vc queira alterar o nome da branch sem estar nela, local, seria:

- git branch -m (nome da branch que vc quer trocar o nome) (nome novo para essa branch)

Obs: Uma vez enviada a branch ao servidor remoto, não tem possibilidade de alterar o nome.

Podemos contornar a observação acima da seguinte forma:

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git checkout TASK5
    Switched to branch 'TASK5'
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git add .
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git commit -m "Teste"
    [TASK5 411d8b4] Teste
    1 file changed, 1 insertion(+), 1 deletion(-)
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git push -u origin TASK5
    Enumerating objects: 5, done.
    Counting objects: 100% (5/5), done.
    Delta compression using up to 16 threads
    Compressing objects: 100% (3/3), done.
    Writing objects: 100% (3/3), 329 bytes | 329.00 KiB/s, done.
    Total 3 (delta 2), reused 0 (delta 0)
    remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
    remote: 
    remote: Create a pull request for 'TASK5' on GitHub by visiting:
    remote:      https://github.com/HelloWounderworld/notes-git/pull/new/TASK5
    remote: 
    To github.com:HelloWounderworld/notes-git.git
    * [new branch]      TASK5 -> TASK5
    Branch 'TASK5' set up to track remote branch 'TASK5' from 'origin'.
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git push --delete origin TASK5
    To github.com:HelloWounderworld/notes-git.git
    - [deleted]         TASK5
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch -m TASK10
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git push -u origin TASK10
    Enumerating objects: 5, done.
    Counting objects: 100% (5/5), done.
    Delta compression using up to 16 threads
    Compressing objects: 100% (3/3), done.
    Writing objects: 100% (3/3), 329 bytes | 329.00 KiB/s, done.
    Total 3 (delta 2), reused 0 (delta 0)
    remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
    remote: 
    remote: Create a pull request for 'TASK10' on GitHub by visiting:
    remote:      https://github.com/HelloWounderworld/notes-git/pull/new/TASK10
    remote: 
    To github.com:HelloWounderworld/notes-git.git
    * [new branch]      TASK10 -> TASK10
    Branch 'TASK10' set up to track remote branch 'TASK10' from 'origin'.

Note que, acima, basicamente, a sequência em série foi o seguinte, excluo a branch de forma remota, visto que a mesma não é excluída localmente, então altero o nome da branch local e, em seguida, dou, novamente, o git push -u.

Lembre-se, se vc estiver fazendo um trabalho em conjunto, e fizer algo de alteração dessa natureza, avisa ao time.                                                                      

## Aula 09 - Histórico de alteraçãoes em diferente branch:
Podemos ver o histórico de commits de outras branchs sem acessar elas, localmente, da segunite forma:

- git log (nome da branch existente)

Daí, com a forma acima vc consegue combinar com outras formas de comando de git log existente, por exemplo, git log (nome da branch) --oneline.