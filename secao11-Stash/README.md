# Seção 11 - Stash:

## Aula 01 - Funcionalidades Stash:
Leitura para o conteúdo:

    https://blog.betrybe.com/git/git-stash/

É uma forma de guardar as alterações de uma dada branch que vc está trabalhando de forma que vc permita mudar de branch sem a necessidade de excluir tudo o que vc fez ou commitar o que vc está fazendo no meio do processo.

A tal mudança de branch usando o git stash, ela permite que vc não traga as mudanças que vc estava realizando de uma branch para outra tbm.

- git stash

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git status
    On branch main
    Your branch is up to date with 'origin/main'.

    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
        modified:   Notas-Aula

    no changes added to commit (use "git add" and/or "git commit -a")
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git stash
    Saved working directory and index state WIP on main: 8b39332 Atualizando as notas de aula
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git log --oneline
    8b39332 (HEAD -> main, origin/main, origin/HEAD) Atualizando as notas de aula
    3e5a5b8 Atualizando as notas de aula
    5a8b605 Atualizando as notas de aula
    9f29b1d Atualizando as notas de aula
    9e38a62 Atualizacao das notas de aula
    dc75fef Atualizacao das notas de aula
    f100917 Atualizando as notas de aula
    7698ed4 Atualizando as notas de aula
    d2fd20e (tag: V1) Atualizando as notas de aula sobre conceito tag
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
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch
    develop
    head-example
    * main

Note que, se vc observar a área em que vc estava trabalhando os arquivos foram voltadas.

Além disso, ela não foi commitada.

Logo, onde é que ela fica guardada?

Basta analisar o seguinte:

- git stash list

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git stash list
    stash@{0}: WIP on main: 8b39332 Atualizando as notas de aula

No caso, visto que as alterações estão guardadas, vc pode dar um git checkout/switch para uma outra branch e realizar as alterações que vc precisa nelas.

Feito as alterações dejesadas na outra branch, agora, vc quer voltar ao seu projeto anterior.

Vc voltou na branch onde vc guardou todas as alterações que vc precisou e nela vc vai querer retomar.

O comando para vc recuperar as alterações que foram guaradas pelo git stash seria:

- git stash apply

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git stash apply
    On branch main
    Your branch is up to date with 'origin/main'.

    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
        modified:   Notas-Aula

    no changes added to commit (use "git add" and/or "git commit -a")

A vantagem de git stash, está no fato de que, visto que vc guardou as alterações em uma dada branch e depois continuou no processo de alteração e, no meio do processo, vc acabou mudando, por git checkout, para uma outra branch e isso acabou desfazendos as alterações que vc havia feito.

No caso, bastaria vc voltar na branch em que vc estava realizando as mudanças e dar git stash apply novamente, que vc irá conseguir recuperar os seus feitos, mesmo que não completo, pelo menos, vc não irá perder toda a modificação que vc realizou.

Ou seja, uma vez guardado as informações no git stash, ela ficará guardado para sempre, a não ser que seja removida.

Outra vantagem da git stash, é que a mesma modificação salva e guardada de uma dada branch, pode ser aplicada para outra branch.

Ou seja, se vc está em uma branch x realizando modificações e em seguida vc mudou para a branch y, nessa branch y vc pode aplicar as modificações que ficaram guardadas na branch x.

Você, pode salvar quantos git stahs possíveis. Mas lembre que, quando vc dar git stash apply, ela irá considerar sempre a última modificação salva.

No caso, seria necessário, em alguns casos, especificar qual modificação seria necessário ser feito.

- git stash apply (nome da stash, geralmente, no formato stash@{N}).

A numeração de stash é em ordem crescente. Ou seja, sempre a informação mais recente salva no stash será o número 0.

Agora, haverá casos em que terá muito, mas muito, stashs salvos e vc precisará removê-las.

O comando para remoção da stash seria:

- git stash pop - Removerá a stash mais recente, a posição 0.

- git stash pop (número da stash) - irá remover stash específico.

Ambas as remoções acima, são em casos em que vc aplicou uma determinada stash e, logo em seguida, vc viu que não está de acordo com o que vc queira.

Agora, existe um caso em que vc consegue remover uma stash sem que vc aplique-a:

- git stash drop - irá remover a stash recente, a posição 0.

- git stash drop (número da stash) - irá remover uma stash de uma posição específica que foi dada.

Agora, existe um caso em que vc uma mudança que vc estiver realizando em uma determinada branch vc queria simplesmente salvar a tal mudança em alguma outra branch que nem existe.

Então, com git stash é possível criar uma nova branch e nela salvar as alterações que vc realizou para limpar a branch atual em que vc está realizando as mudanças.

O comando para isso seria:

- git stash branch (nome da branch nova)