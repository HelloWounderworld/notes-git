# Seção 10 - Tags:

## Aula 01 - Criando e Listando tags:
Leitura de conceitos:

    https://github.com/DevMasterTeam/Udemy-Git/blob/master/Se%C3%A7%C3%A3o%2010%20-%20Tags/(Slide)%20Conceitos%20sobre%20Tag.pdf

    https://docs.github.com/en/rest/git/tags?apiVersion=2022-11-28

    https://www.atlassian.com/br/git/tutorials/inspecting-a-repository/git-tag#:~:text=git%20tag%20%C3%A9%20em%20geral,t%C3%AAm%20mais%20hist%C3%B3rico%20de%20commits.

Vamos realizar algumas marcações para mlhor fixar o conceito de tag:

- git tag (nome da marcação) - Versão de tag mais simples, lightwight. Ou seja, não tem tanto peso de importância.

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git tag V1
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git log --onoline
    fatal: argumento não reconhecido: --onoline
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git log --oneline
    d2fd20e (HEAD -> main, tag: V1, origin/main, origin/HEAD) Atualizando as notas de aula sobre conceito tag
    6549899 Atualizando as notas de aulas minhas
    1f5c1de Atualizando as notas de aulas próprias
    cedb5d4 Atualizando as notas de aulas
    1849886 Atualizando as notas de aula
    331f357 Atualizando as notas de aula
    7228cb1 Atualizando as notas de aula
    68baf0a Atualizando as notas de aula
    3dd0d95 Atualizando as notas de aula
    e195982 Atualizando as notas de aula
    01b9e03 atualizando as notas de aula
    92e1258 Atualizando as notas de aula
    be95bbf Atualizando as notas de aula
    a953567 Atualizando as notas de aula
    b8f4ddf Atualizando as notas de aula
    a66b0c0 Atualizando as notas de aula
    51783b7 Atualizando notas de aula
    cc635a1 Atualizando as notas de aula
    8c83887 Atualizando as notas de aula com o usuario certo
    0fc34ee Atualizando as notas de aula sobre git - controle de versionamento
    684b766 (develop) Vantagens de pull request para enriquecer o teu curriculo
    0ac21b5 Leituras para Star, Watch e Fork
    3b0342a Atualizacao do titulo
    82864fb Forma de dar push no github - novas regras
    b2c9f7f Versao inicial do site
    cd08034 Commit inicial
    ad8b997 Initial commit

Note que, foi feito uma marcação no último commit que eu realizei.

Mas, vale ressaltar que tal marcação foi feita localmente.

Ou seja, ela não é remota.

Isso significa que se vc olhar agora no github no repositório, não haverá alguma tag marcada.

Não podemos duplicar uma tag com o mesmo nome. O que podemos é mudar o seu nome.

Agora, vamos criar uma tag mais completa:

- git tag -a -m "alguma msg" (nome da tag) - Essa tag é um tipo annotaded.

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git tag -a -m "Tag criada v2" V2
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git log --oneline
    d2fd20e (HEAD -> main, tag: V2, tag: V1, origin/main, origin/HEAD) Atualizando as notas de aula sobre conceito tag
    6549899 Atualizando as notas de aulas minhas
    1f5c1de Atualizando as notas de aulas próprias
    cedb5d4 Atualizando as notas de aulas
    1849886 Atualizando as notas de aula
    331f357 Atualizando as notas de aula
    7228cb1 Atualizando as notas de aula
    68baf0a Atualizando as notas de aula
    3dd0d95 Atualizando as notas de aula
    e195982 Atualizando as notas de aula
    01b9e03 atualizando as notas de aula
    92e1258 Atualizando as notas de aula
    be95bbf Atualizando as notas de aula
    a953567 Atualizando as notas de aula
    b8f4ddf Atualizando as notas de aula
    a66b0c0 Atualizando as notas de aula
    51783b7 Atualizando notas de aula
    cc635a1 Atualizando as notas de aula
    8c83887 Atualizando as notas de aula com o usuario certo
    0fc34ee Atualizando as notas de aula sobre git - controle de versionamento
    684b766 (develop) Vantagens de pull request para enriquecer o teu curriculo
    0ac21b5 Leituras para Star, Watch e Fork
    3b0342a Atualizacao do titulo
    82864fb Forma de dar push no github - novas regras
    b2c9f7f Versao inicial do site
    cd08034 Commit inicial
    ad8b997 Initial commit

Essa tag tbm irá marcar no último commit realizado.

A diferença entre as duas tags mostrada até agora, seria que a segunda tag, annotaded, tem como finalidade não apenas marcar, mas mostrar quem a marcou.

Basta dar o seguinte comando para mostrar quem foi feito a tal marcação:

- git show (nome que foi atribuído à tag)

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git show V2
    tag V2
    Tagger: Leonardo Takashi Teramatsu <leonardo.teramatsu@gmail.com>
    Date:   Mon Jan 16 11:03:44 2023 -0300

    Tag criada v2

    commit d2fd20ef0689aa1e157ef79d8d6244a29c8b10a4 (HEAD -> main, tag: V2, tag: V1, origin/main, origin/HEAD)
    Author: Leonardo Takashi Teramatsu <leonardo.teramatsu@gmail.com>
    Date:   Mon Jan 16 10:59:30 2023 -0300

        Atualizando as notas de aula sobre conceito tag

    diff --git a/Notas-Aula b/Notas-Aula
    index d356b31..d6c02e3 100644
    --- a/Notas-Aula
    +++ b/Notas-Aula
    @@ -1403,6 +1403,14 @@ Seção 09 - Source Control Management (SCM):
    Seção 10 - Tags:
    
        Aula 01 - Criando e Listando tags:
    +        Leitura de conceitos:
    +            https://github.com/DevMasterTeam/Udemy-Git/blob/master/Se%C3%A7%C3%A3o%2010%20-%20Tags/(Slide)%20Conceitos%20sobre%20Tag.pdf
    +            https://docs.github.com/en/rest/git/tags?apiVersion=2022-11-28
    +            https://www.atlassian.com/br/git/tutorials/inspecting-a-repository/git-tag#:~:text=git%20tag%20%C3%A9%20em%20geral,t%C3%AAm%20mais%20hist%C3%B3rico%20de%20commits.
    +
    +        Vamos realizar algumas marcações para mlhor fixar o conceito de tag:
    +            - git tag (nome da marcação) - Versão de tag mais simples, lightwight. Ou seja, não tem tanto peso de importância.
    +                
    
        Aula 02 - Usar tag em commits antigos:

Note que, acima é mostrado todas as informações e quem fez a tal marcação.

Diferentemente da outra tag que faz apenas uma marcação.

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git show V1
    commit d2fd20ef0689aa1e157ef79d8d6244a29c8b10a4 (HEAD -> main, tag: V2, tag: V1, origin/main, origin/HEAD)
    Author: Leonardo Takashi Teramatsu <leonardo.teramatsu@gmail.com>
    Date:   Mon Jan 16 10:59:30 2023 -0300

        Atualizando as notas de aula sobre conceito tag

    diff --git a/Notas-Aula b/Notas-Aula
    index d356b31..d6c02e3 100644
    --- a/Notas-Aula
    +++ b/Notas-Aula
    @@ -1403,6 +1403,14 @@ Seção 09 - Source Control Management (SCM):
    Seção 10 - Tags:
    
        Aula 01 - Criando e Listando tags:
    +        Leitura de conceitos:
    +            https://github.com/DevMasterTeam/Udemy-Git/blob/master/Se%C3%A7%C3%A3o%2010%20-%20Tags/(Slide)%20Conceitos%20sobre%20Tag.pdf
    +            https://docs.github.com/en/rest/git/tags?apiVersion=2022-11-28
    +            https://www.atlassian.com/br/git/tutorials/inspecting-a-repository/git-tag#:~:text=git%20tag%20%C3%A9%20em%20geral,t%C3%AAm%20mais%20hist%C3%B3rico%20de%20commits.
    +
    +        Vamos realizar algumas marcações para mlhor fixar o conceito de tag:
    +            - git tag (nome da marcação) - Versão de tag mais simples, lightwight. Ou seja, não tem tanto peso de importância.
    +                
    
        Aula 02 - Usar tag em commits antigos:

No caso, aqui só tem apens o detalhe do commit, mas não é mostrado o tagger.

Para consultar todas as tags do projeto, basta colocar:]

- git tag

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git tag
    V1
    V2

Isso irá exibir todas as tags.

## Aula 02 - Usar tag em commits antigos:
Quero realizar uma tag em um commit antigo:

- git tag (nome da tag) (número do commit)

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git log --oneline
    7698ed4 (HEAD -> main, origin/main, origin/HEAD) Atualizando as notas de aula
    d2fd20e (tag: V2, tag: V1) Atualizando as notas de aula sobre conceito tag
    6549899 Atualizando as notas de aulas minhas
    1f5c1de Atualizando as notas de aulas próprias
    cedb5d4 Atualizando as notas de aulas
    1849886 Atualizando as notas de aula
    331f357 Atualizando as notas de aula
    7228cb1 Atualizando as notas de aula
    68baf0a Atualizando as notas de aula
    3dd0d95 Atualizando as notas de aula
    e195982 Atualizando as notas de aula
    01b9e03 atualizando as notas de aula
    92e1258 Atualizando as notas de aula
    be95bbf Atualizando as notas de aula
    a953567 Atualizando as notas de aula
    b8f4ddf Atualizando as notas de aula
    a66b0c0 Atualizando as notas de aula
    51783b7 Atualizando notas de aula
    cc635a1 Atualizando as notas de aula
    8c83887 Atualizando as notas de aula com o usuario certo
    0fc34ee Atualizando as notas de aula sobre git - controle de versionamento
    684b766 (develop) Vantagens de pull request para enriquecer o teu curriculo
    0ac21b5 Leituras para Star, Watch e Fork
    3b0342a Atualizacao do titulo
    82864fb Forma de dar push no github - novas regras
    b2c9f7f Versao inicial do site
    cd08034 Commit inicial
    ad8b997 Initial commit
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git tag V0 51783b7
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git log --oneline
    7698ed4 (HEAD -> main, origin/main, origin/HEAD) Atualizando as notas de aula
    d2fd20e (tag: V2, tag: V1) Atualizando as notas de aula sobre conceito tag
    6549899 Atualizando as notas de aulas minhas
    1f5c1de Atualizando as notas de aulas próprias
    cedb5d4 Atualizando as notas de aulas
    1849886 Atualizando as notas de aula
    331f357 Atualizando as notas de aula
    7228cb1 Atualizando as notas de aula
    68baf0a Atualizando as notas de aula
    3dd0d95 Atualizando as notas de aula
    e195982 Atualizando as notas de aula
    01b9e03 atualizando as notas de aula
    92e1258 Atualizando as notas de aula
    be95bbf Atualizando as notas de aula
    a953567 Atualizando as notas de aula
    b8f4ddf Atualizando as notas de aula
    a66b0c0 Atualizando as notas de aula
    51783b7 (tag: V0) Atualizando notas de aula
    cc635a1 Atualizando as notas de aula
    8c83887 Atualizando as notas de aula com o usuario certo
    0fc34ee Atualizando as notas de aula sobre git - controle de versionamento
    684b766 (develop) Vantagens de pull request para enriquecer o teu curriculo
    0ac21b5 Leituras para Star, Watch e Fork
    3b0342a Atualizacao do titulo
    82864fb Forma de dar push no github - novas regras
    b2c9f7f Versao inicial do site
    cd08034 Commit inicial
    ad8b997 Initial commit

Note que, em um commit antigo, foi feito uma marcação de uma tag.

O mesmo vale para a tag do tipo annotaded, pois nela será feito uma marcação mostrando quem foi que fez a tal tag.

- git tag -a -m "alguma msg" (nome para a tag) (número do commit)

## Aula 03 - Enviando tag para o repositório:
Agora, vamos a aprender a enviar as tags locais para o servidor.

- git push (nome do caminho) (nome da Tag)

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git push origin V0
    Total 0 (delta 0), reused 0 (delta 0)
    To github.com:HelloWounderworld/notes-git.git
    * [new tag]         V0 -> V0

Com isso, ao olharmos no github onde está esse repositório projeto, vamos poder ver que a contagem de tags aparecerá como 1, mostrando em qual commit foi feito.

Podemos mandar todas as tags de uma vez tbm com o seguinte comando:

- git push --tags

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git push --tags
    Enumerating objects: 1, done.
    Counting objects: 100% (1/1), done.
    Writing objects: 100% (1/1), 176 bytes | 176.00 KiB/s, done.
    Total 1 (delta 0), reused 0 (delta 0)
    To github.com:HelloWounderworld/notes-git.git
    * [new tag]         V1 -> V1
    * [new tag]         V2 -> V2

No caso, todas as tags criadas localmente, foram enviadas ao servidor/repositório remoto do github.

Isso não é uma prática recomandada, pois existem tags que ficam salvas no servidor que depois não é mais necessário e que tal tag ainda reside no mesmo repositório, só que localmente.

Daí, realizar o comando acima, fará com que crie, novamente, a mesma marcação que havía sido desconsiderada antes.

Logo, vc precisaria ter muita certeza em usar esse comando.

Em todo caso, uma boa prática é vc ir dando push de tags específicas que vc marcou.

## Aula 04 - Usando tags:
Uma vez criado uma tag, podemos usar a mesma commo um commit.

No caso, é como usar um commit, só que no lugar de vc especificar o número bizarro do commit, vc pode especificar o nome da tag que foi salva.

- git checkout (nome da tag salva)

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git checkout V1
    Note: switching to 'V1'.

    You are in 'detached HEAD' state. You can look around, make experimental
    changes and commit them, and you can discard any commits you make in this
    state without impacting any branches by switching back to a branch.

    If you want to create a new branch to retain commits you create, you may
    do so (now or later) by using -c with the switch command. Example:

    git switch -c <new-branch-name>

    Or undo this operation with:

    git switch -

    Turn off this advice by setting config variable advice.detachedHead to false

    HEAD is now at d2fd20e Atualizando as notas de aula sobre conceito tag
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch
    * (HEAD detached at V1)
    develop
    head-example
    main

Disso, podemos realizar as mesmas mudanças que fizemos, por exemplo, para haed-example, que é uma branch criada.

O mesmo pode ser usada para git diff especificando as tags:

- git diff (nome da tag)

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git diff V1
    diff --git a/Notas-Aula b/Notas-Aula
    index d6c02e3..06e607c 100644
    --- a/Notas-Aula
    +++ b/Notas-Aula
    @@ -1410,13 +1410,265 @@ Seção 10 - Tags:
    
            Vamos realizar algumas marcações para mlhor fixar o conceito de tag:
                - git tag (nome da marcação) - Versão de tag mais simples, lightwight. Ou seja, não tem tanto peso de importância.
    +                leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git tag V1
    +                leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git log --onoline
    +                fatal: argumento não reconhecido: --onoline
    +                leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git log --oneline
    +                d2fd20e (HEAD -> main, tag: V1, origin/main, origin/HEAD) Atualizando as notas de aula sobre conceito tag
    +                6549899 Atualizando as notas de aulas minhas
    +                1f5c1de Atualizando as notas de aulas próprias
    +                cedb5d4 Atualizando as notas de aulas
    +                1849886 Atualizando as notas de aula
    +                331f357 Atualizando as notas de aula
    +                7228cb1 Atualizando as notas de aula
    +                68baf0a Atualizando as notas de aula
    +                3dd0d95 Atualizando as notas de aula
    +                e195982 Atualizando as notas de aula
    +                01b9e03 atualizando as notas de aula
    +                92e1258 Atualizando as notas de aula
    +                be95bbf Atualizando as notas de aula
    +                a953567 Atualizando as notas de aula
    +                b8f4ddf Atualizando as notas de aula
    +                a66b0c0 Atualizando as notas de aula
    +                51783b7 Atualizando notas de aula
    +                cc635a1 Atualizando as notas de aula
    +                8c83887 Atualizando as notas de aula com o usuario certo
    +                0fc34ee Atualizando as notas de aula sobre git - controle de versionamento
    +                684b766 (develop) Vantagens de pull request para enriquecer o teu curriculo
    +                0ac21b5 Leituras para Star, Watch e Fork
    +                3b0342a Atualizacao do titulo
    +                82864fb Forma de dar push no github - novas regras
    +                b2c9f7f Versao inicial do site
    +                cd08034 Commit inicial
    +                ad8b997 Initial commit
    +        Note que, foi feito uma marcação no último commit que eu realizei.
    +        Mas, vale ressaltar que tal marcação foi feita localmente.
    +        Ou seja, ela não é remota.
    +        Isso significa que se vc olhar agora no github no repositório, não haverá alguma tag marcada.
    +

- git diff (nome da tag) (nome da tag) - irá comparar o que mudou de uma para outra.

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git diff V0 V2
    diff --git a/Notas-Aula b/Notas-Aula
    index 3b32087..d6c02e3 100644
    --- a/Notas-Aula
    +++ b/Notas-Aula
    @@ -1070,30 +1070,360 @@ Seção 07 - Branches:
                    * TASK-2
                    develop
                    main
    -        
    
        Aula 03 - Mudançãs não salvas:
    +        Um ponto importante de mudanças não salvas.
    +        Suponhamos que vc esteja em uma branch realizando as modificações que vc quer e, no meio do processo, vc queria mudar da atual branch para uma outra.
    +        Ao darmos git checkout para uma outra branch e dermos o git status, veremos que as alterações que vc fez na última branch vem para a branch que vc mudou.
    +        Ou seja, vc precisa tomar muito cuidado nisso, pois existem alterações que vc quer que ela fique na branch em que vc estava realizando tais alterações.
    +        No caso, uma boa prática para evitar que isso aconteça seria dando git add e git commit antes de ir para uma outra branch nova.
    +        Existe tbm uma outra alternativa para isso, que é dando o seguinte comando:
    +            - git checkout -f (nome da branch existente) - Esse comando irá dar uma limpa em todas as alterações não rastreadas para mudar de branch.
    +                leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch
    +                TASK-1
    +                TASK-2
    +                develop
    +                * main
    +                leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git checkout -f develop
    +                Switched to branch 'develop'
    +                leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch
    +                TASK-1
    +                TASK-2
    +                * develop
    +                main
    +        Note que, ao darmos um git checkout . ou git checkout -f, e se vc quiser que o arquivo que vc estava modificando volte na forma como vc estava modificando, basta dar Crtl+z ou Command + Z.
    
        Aula 04 - Detached HEAD:
    +        Vamos começar fazendo o git log --oneline.
    +            leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git log --oneline
    +            a66b0c0 (HEAD -> main, origin/main, origin/HEAD) Atualizando as notas de aula
    +            51783b7 Atualizando notas de aula
    +            cc635a1 (TASK-2) Atualizando as notas de aula

Em ambos os casos, podemos verificar os tipos de alterações que ocorreram.

## Aula 05 - Removendo tags:
Uma forma de remover a tag temos duas formas, uma forma remove a tag localmente e, outra, remove no servidor remoto.

Remoção local:

- git tag -d (nome da tag)

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git tag -d V0
    Deleted tag 'V0' (was 51783b7)
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git tag -d V2
    Deleted tag 'V2' (was 64ecfa4)

Note que, a remoção das tags indifere se é do tipo lightweight ou annotated.

Remoção do servidor remoto:

- git push --delete (nome do caminho) (nome da tag)

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git push --delete origin V0
    To github.com:HelloWounderworld/notes-git.git
    - [deleted]         V0
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git push --delete V2
    fatal: --delete doesn't make sense without any refs
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git push --delete origin V2
    To github.com:HelloWounderworld/notes-git.git
    - [deleted]         V2
