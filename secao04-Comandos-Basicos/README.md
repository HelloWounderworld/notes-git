# Seção 04 - Comandos Básicos:
## Aula 01 - Configuração do usuário:
Vamos dizer ao git qual é o meu email e qual é o meu usuário. Os comandos para isso são:

- git config --global user.name "Leonardo Takashi Teramatsu"

- git config --global user.email "leonardo.teramatsu@gmail.com"

Isso é importante, pois o git precisa saber quem está realizando as mudanças.

Além dele funcionar para permissões de controles de acessos ao repositório.

- git config --global user.name: O comando mostrará quem é o nome cadastrado

- git config --global user.email: O comando mostrará de qual email está cadastrado.

"--global" indicará que os dados que foi indicado serão usadas nas outras vezes, sem a necessidade de ficar toda hora especificando para verificar as permissões de acessos.

## Aula 02 - Criando Repositório local:
Vamos aprender a criar o nosso primeiro projeto.

No caso, vamos criar um projeto notes-git e esse será o nosso projeto.

Vamos criar um arquivo chamado hello.txt dentro desse projeto e dentro dela escrever Hello.

Agora, os seguintes comandos servem para listarem as pastas presentes:

- ls - Serve para listar arquivos e pastas presentes

- ls -a - Serve para listar arquivos e pastas, até aquelas escondidas, presentes.

Mas ainda esse diretório não é considerado um repositório git.

Para precisarmos fazer com que esse projeto se torne um repositório git basta lançar o seguinte comando:

- git init - fará com que o seu diretório torne-a um repositório git.

        Repositório vazio Git inicializado em  /home/leonardo/Documentos/estudos/notes-git/.git/

A priori deveria aparecer o nome da branch padrão em que se encontra, master.

Por algum motivo isso não está acontecendo, mas foi inicializado.

Mas, ao fizermos "ls -a" vamos conseguir ver que tem uma nova pasta que surgiu nela e que esteja escondida/não visível.

Podemos mudar o nome da branch padrão da seguinte forma:

- git config --global init.defaultBranch (nome da nova branch padrão)

Agora, sempre que vc criar um diretório novo e nela realizar o git init o nome da branch padrão será o que vc atribuiu acima.

Recomedamos que vc rode novamente o comando acima colocando como a branch padrão "master".

## Aula 03 - Adicionando Mudanças:
Vamos adicionar as mudanças.

Até agora, colocamos pouca coisa no arquivo hello.txt que criamos.

Para verificar o status rode o seguinte comando:

- git status: Isso mostrará todos os arquivos que sofreram alguma alteração ou aquelas que foram incluídas. Entretanto, esse arquivo que teve alguma alteração não tem alguma notoriedade ainda, pois para o git ele não é importante

Para fazer com que tais alterações ganhe relevência para o git:

- git add (nome do arquivo com extensão) - Isso fará com que estamos dizendo ao git que esse arquivo que sofreu alteração é importante.

Basta dar o git status, novamente, para verificar a tal importância:

    On branch master

    No commits yet

    Changes to be committed:
    (use "git rm --cached <file>..." to unstage)
        new file:   hello.txt

    Untracked files:
    (use "git add <file>..." to include in what will be committed)
        Notas-Aula

No caso, o arquivo hello.txt, ganhou relevância agora para o git.

No caso, se quisermos realizar tais consiederações ao git para um projeto que visa a criação de sites, haverá centenas de arquivos que sofreram alguma alteração.

Para isso, seria muito inconveniente ficar toda hora digitando git add para cada arquivos e pastas.

OBS: Caso grave de vc zoar muito feio o teu repositório git:

    rm -fr .git/

    O comando acima, ele irá remover, literalmente, todo o seu repositório git, ou seja, todas as mudanças, históricos de mudanças, etc... serão apagadas e isso tem um grande potencial de vc comprometer para sempre algum projeto que vc esteja trabalhando.

O comando para conseguirmos adicionar todos os arquivos com modificação, seria:

- git add .

- git add -a

- git add --all

As três acima serve para adicionar todos os arquivos que vc modificou no seu projeto.

Relembrando, o git add, ela serve para que a tal alteração ganhe relevência para o git e que se ocorrer qualquer outra alteração, isso fique marcado no histórico.

## Aula 04 - Removendo Arquivos Adicionados:
Suponhamos que, quando usamos o git add ., e adicionamos ao repositório todos os arquivos que sofreram alguma modificação.

Daí, dentro desses arquivos, teve algum arquivo que vc viu que não era para ser considerado.

Para corrigir esse problema, o git, tem o seguinte comando para conseguirmos desconsiderar.

- git rm --cached (nome do arquivo com extensão) - servirá para vc conseguir desconsiderar dentro do git add.

Note que, o arquivo hello.txt não foi apagado, e sim, foi apenas removido dos arquivos de rastreamento do git.

Agora, suponhamos que vc, por engano, acabou dando git add .,  e todos esses arquivos não eram para serem enviados ao repositório.

Para corrigir esse problema, vamos colocar o seguinte comando do git:

- git rm --cached -rm .

No caso, todos arquivos adicionados, foram removidos, recursivamente, do rastreamento.
Basta dar o git status para verificar que, de fato, isso aconteceu.

## Aula 05 - Salvando mudanças:
Visto que os arquivos para rastreamento, as que realmente vc quer que o git considera, foram adicionados e que vc queira agora salvar tais alterações.

Para isso, vamos usar um processo de commit.

- git commit -m "Alguma mensagem"

    git commit -m "Versao inicial"
    [master (root-commit) 24660aa] Versao inicial
    2 files changed, 135 insertions(+)
    create mode 100644 Notas-Aula
    create mode 100644 hello.txt

Ao rodarmos o comando acima aparecerá uma das mensagens acima.

Isso indica que vc criou a sua versão do arquivo hello.

A partir disso, se fizermos alguma alteração no arquivo hello.txt e novamente rodar o git status, voltaremos na condição em que o git não está considerando a mudança dentro do rastreamento dele.

No caso, se vc quiser considerar novamente tais mudanças, será o mesmo processos que fizemos acima, git add., git commit -m "mensagem".

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git add .
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git commit -m "Versao Segunda"
    [master 9a08112] Versao Segunda
    2 files changed, 10 insertions(+), 1 deletion(-)

Recomendamos que as msgs que são colocadas no commit, sejam didáticas e resumidas para facilitar, ao analisar o hitórico das modificações, a instrução ao usuário. 

## Aula 06 - Quatro Estados:
Leituras sobre o assunto:

    https://github.com/DevMasterTeam/Udemy-Git/blob/master/Se%C3%A7%C3%A3o%2004%20-%20Comandos%20B%C3%A1sicos/(Slide)%20Quatro%20estados.pdf

    https://blog.4linux.com.br/git-ciclo-de-vida/

Ciclo de vida de arquivos:

    https://medium.com/@rafaelvicio/introdu%C3%A7%C3%A3o-a-git-5ae36c303850]

    https://dev.to/lazarocontato/git-um-breve-estudo-9gl

## Aula 07 - Quatro estados - Prática:
Vamos colocar alguma alteração de texto no arquivo hello.txt. (O conteúdo de texto colocado deixo a critério do estudante)

Assim, ao darmos o git status, vamos ver o seguinte estado

    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
        modified:   Notas-Aula
        modified:   hello.txt

    no changes added to commit (use "git add" and/or "git commit -a")

No caso, está em not staged, ou seja, não foi enviado para a área de preparação.
Visto que a modificação é o que queremos, então vamos dar o "git add ." e, em seguida, "git status".

    On branch master
    Changes to be committed:
    (use "git restore --staged <file>..." to unstage)
        modified:   Notas-Aula
        modified:   hello.txt

Vimos que as mudanças para serem comidatas e estão no estado unstages.

Por fim, vamos dar o "git commit -m "alguma mensagem"".

    [master fddac79] versao Tres
    2 files changed, 28 insertions(+), 1 deletion(-)

Em seguida, damos o git status.

    On branch master
    nothing to commit, working tree clean

Agora, vamos fazer o seguinte, copiamos o arquivo hello.txt e mudamos o nome dele para main e dentro dela vamos colocar algum texto aleatório (deixo no critério da pessoa).

Feito isso, vamos dar um fit status e aparecerá o seguinte.

    On branch master
    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
        modified:   Notas-Aula
        modified:   hello.txt

    Untracked files:
    (use "git add <file>..." to include in what will be committed)
        main.txt

    no changes added to commit (use "git add" and/or "git commit -a")

Agora, será mostrado os quatro estágios, pois na primeira, não estava sendo exibido o untracked.

Daí, vamos dar o git add e, em seguida, o git status para verificarmos o que será exibido.

    On branch master
    Changes to be committed:
    (use "git restore --staged <file>..." to unstage)
        modified:   Notas-Aula
        modified:   hello.txt
        new file:   main.txt

Em seguida, vamos modificar novamente o arquivo hello.txt, colocando algum texto a mais ou excluindo algo nela, só para criarmos um cenário em que demonstra que tal tipo de alteração não era o que o usuário queria realizar.

Em seguida, damos o git status.

    On branch master
    Changes to be committed:
    (use "git restore --staged <file>..." to unstage)
        modified:   Notas-Aula
        modified:   hello.txt
        new file:   main.txt

    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
        modified:   Notas-Aula
        modified:   hello.txt

Note que, o mesmo arquivo que está em rastreamento est'asendo mostrado como not staged, visto que foi feito a modificação.

Se fizermos o git commit -m sobre isso, será considerado o arquivo que está sobre o rastreamento e ignorando a que foi feito a alteração e não colocado dentro do rastreamento.

Vamos ver o que acontece, damos o git commit e, em seguida, o git status.

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git commit -m "Versao Quatro"
    [master 4596956] Versao Quatro
    3 files changed, 38 insertions(+), 2 deletions(-)
    create mode 100644 main.txt
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git status
    On branch master
    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
        modified:   Notas-Aula
        modified:   hello.txt

    no changes added to commit (use "git add" and/or "git commit -a")

Note que, aquele que sofreu alguma modificação, continua estando em not staged, ou seja, não está sobre o rastreamento.

## Aula 08 - Visualizando Alterações:
Primeiramente, vamos acrescentar mais alguns textos para os arquivos hello.txt e main.txt (o texto deixo ao critério do estudante).

No caso, suponhamos um cenário que tal alteração que foi feita acima nos dois arquivos tenha sido lá no passado e que vc não lembre exatamente o que foi feito ao ponto disso te dar o receio de dar git add e git commit.

No caso, o que poderíamos pensar, seria dar o git status.

Entretanto, o git status só deixa claro quais arquivos sofreram alguma alteração e quais estáo ou não sobre rastreamento.

No caso, ele não exibe o conteúdo dentro da alteração.

Para isso, uma outra alternativa que temos para verificarmos isso seria dando o seguinte comando:

- git diff - Será exibido as linhas que foram ou não adicionados. Para sair do git diff, basta dar Shift + q.

    diff --git a/Notas-Aula b/Notas-Aula
    index 27dfe82..711764f 100644
    --- a/Notas-Aula
    +++ b/Notas-Aula
    @@ -169,6 +169,72 @@ Seção 04 - Comandos Básicos:
                no changes added to commit (use "git add" and/or "git commit -a")
            Agora, será mostrado os quatro estágios, pois na primeira, não estava sendo exibido o untracked.
            Daí, vamos dar o git add e, em seguida, o git status para verificarmos o que será exibido.
    +            On branch master
    +            Changes to be committed:
    +            (use "git restore --staged <file>..." to unstage)
    +                modified:   Notas-Aula
    +                modified:   hello.txt
    +                new file:   main.txt
    +        Em seguida, vamos modificar novamente o arquivo hello.txt, colocando algum texto a mais ou excluindo algo nela, só para criarmos um cenário em que demonstra que tal tipo de alteração não era o que o usuário queria realizar.
    +        Em seguida, damos o git status.
    +            On branch master
    +            Changes to be committed:
    +            (use "git restore --staged <file>..." to unstage)
    +                modified:   Notas-Aula
    +                modified:   hello.txt
    +                new file:   main.txt
    +
    +            Changes not staged for commit:
    +            (use "git add <file>..." to update what will be committed)
    +            (use "git restore <file>..." to discard changes in working directory)
    +                modified:   Notas-Aula
    +                modified:   hello.txt
    +        Note que, o mesmo arquivo que está em rastreamento est'asendo mostrado como not staged, visto que foi feito a modificação.
    +        Se fizermos o git commit -m sobre isso, será considerado o arquivo que está sobre o rastreamento e ignorando a que foi feito a alteração e não colocado dentro do rastreamento.
    +        Vamos ver o que acontece, damos o git commit e, em seguida, o git status.
    +            leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git commit -m "Versao Quatro"
    +            [master 4596956] Versao Quatro
    +            3 files changed, 38 insertions(+), 2 deletions(-)
    +            create mode 100644 main.txt
    +            leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git status
    +            On branch master
    +            Changes not staged for commit:
    +            (use "git add <file>..." to update what will be committed)
    +            (use "git restore <file>..." to discard changes in working directory)
    +                modified:   Notas-Aula
    +                modified:   hello.txt
    +
    +            no changes added to commit (use "git add" and/or "git commit -a")
    +        Note que, aquele que sofreu alguma modificação, continua estando em not staged, ou seja, não está sobre o rastreamento.
    +
    +    Aula 08 - Visualizando Alterações:
    +        Primeiramente, vamos acrescentar mais alguns textos para os arquivos hello.txt e main.txt (o texto deixo ao critério do estudante).
    +        No caso, suponhamos um cenário que tal alteração que foi feita acima nos dois arquivos tenha sido lá no passado e que vc não lembre exatamente o que foi feito ao ponto disso te dar o receio de dar git add e git commit.
    +        No caso, o que poderíamos pensar, seria dar o git status.
    +        Entretanto, o git status só deixa claro quais arquivos sofreram alguma alteração e quais estáo ou não sobre rastreamento.
    +        No caso, ele não exibe o conteúdo dentro da alteração.
    +        Para isso, uma outra alternativa que temos para verificarmos isso seria dando o seguinte comando:
    +            - git diff - Será exibido as linhas que foram ou não adicionados.
    +
    +    Aula 09 - Histórico de Commits:
    +
    +    Aula 10 - Histórico de Commits - Variações:
    +
    +    Aula 11 - Alterando um commit:
    +
    +    Aula 12 - Editor de texto padrão:
    +
    +    Aula 13 - Usando commits anterioes:
    +
    +    Aula 14 - Desfazendo mudanças - Parte 1:
    +
    +    Aula 15 - Desfazendo mudanças - Parte 2:
    +
    +    Aula 16 - Ignorando arquivos:
    +
    +    Aula 17 - Parar de rastrear um arquivo:
    +
    +    Aula 18 - Clonando repositório:
        
    Seção 05 - Github:
    
    diff --git a/hello.txt b/hello.txt
    index 16ca364..09d09cd 100644
    --- a/hello.txt
    +++ b/hello.txt
    @@ -2,4 +2,7 @@ Hello WounderWorld!
    Welcome to the Cyberpunk!
    Your life will be bad with hight quality of tecnologies!
    Your life going to resume at drugs and more drugs!
    -And you will death with overdose, but without regrets.
    \ No newline at end of file
    +And you will death with overdose, but without regrets.
    +Well, is better birth rich than with talent.
    +We live in this society.
    +This society, that is hell!
    \ No newline at end of file
    diff --git a/main.txt b/main.txt
    index b5d3d01..311078d 100644

Ou seja, é isso que será exibido acima (feito no Mac. Precisaria verificar para Linux, na minha máquina).

Visto que tais alterações vão de acordo com o que vc realmente queria mesmo, então podemos dar o git add.

Damos o git status, para verificarmos o que o ocorreu.

    On branch master
    Changes to be committed:
    (use "git restore --staged <file>..." to unstage)
        modified:   Notas-Aula
        modified:   hello.txt
        modified:   main.txt

    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
        modified:   Notas-Aula

Mas, suponhamos que o git add que vc deu foi um engano tbm, ou seja, vc nem ao menos lembra direito o que fez de alteração e acabou, por engano, dar o git add.

Para revertermos isso, o git diff, apenas, já não serviria.

Entretanto, sabemos que ainda não tenhamos feito commit.

Então para verificarmos o que temos adicionado, podemos colocar o seguinte comando:

- git diff --cached - Isso mostrará as alterações que ocorreu dos arquivos que estão sendo considerados dentro do rastreamento.

    diff --git a/Notas-Aula b/Notas-Aula
    index 27dfe82..15dbdb8 100644
    --- a/Notas-Aula
    +++ b/Notas-Aula
    @@ -169,6 +169,168 @@ Seção 04 - Comandos Básicos:
                no changes added to commit (use "git add" and/or "git commit -a")
            Agora, será mostrado os quatro estágios, pois na primeira, não estava sendo exibido o untracked.
            Daí, vamos dar o git add e, em seguida, o git status para verificarmos o que será exibido.
    +            On branch master
    +            Changes to be committed:
    +            (use "git restore --staged <file>..." to unstage)
    +                modified:   Notas-Aula
    +                modified:   hello.txt
    +                new file:   main.txt
    +        Em seguida, vamos modificar novamente o arquivo hello.txt, colocando algum texto a mais ou excluindo algo nela, só para criarmos um cenário em que demonstra que tal tipo de alteração não era o que o usuário queria realizar.
    +        Em seguida, damos o git status.
    +            On branch master
    +            Changes to be committed:
    +            (use "git restore --staged <file>..." to unstage)
    +                modified:   Notas-Aula
    +                modified:   hello.txt
    +                new file:   main.txt
    +
    +            Changes not staged for commit:
    +            (use "git add <file>..." to update what will be committed)
    +            (use "git restore <file>..." to discard changes in working directory)
    +                modified:   Notas-Aula
    +                modified:   hello.txt
    +        Note que, o mesmo arquivo que está em rastreamento est'asendo mostrado como not staged, visto que foi feito a modificação.
    +        Se fizermos o git commit -m sobre isso, será considerado o arquivo que está sobre o rastreamento e ignorando a que foi feito a alteração e não colocado dentro do rastreamento.
    +        Vamos ver o que acontece, damos o git commit e, em seguida, o git status.
    +            leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git commit -m "Versao Quatro"
    +            [master 4596956] Versao Quatro
    +            3 files changed, 38 insertions(+), 2 deletions(-)
    +            create mode 100644 main.txt
    +            leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git status
    +            On branch master
    +            Changes not staged for commit:
    +            (use "git add <file>..." to update what will be committed)
    +            (use "git restore <file>..." to discard changes in working directory)
    +                modified:   Notas-Aula
    +                modified:   hello.txt
    +
    +            no changes added to commit (use "git add" and/or "git commit -a")
    +        Note que, aquele que sofreu alguma modificação, continua estando em not staged, ou seja, não está sobre o rastreamento.
    +
    +    Aula 08 - Visualizando Alterações:
    +        Primeiramente, vamos acrescentar mais alguns textos para os arquivos hello.txt e main.txt (o texto deixo ao critério do estudante).
    +        No caso, suponhamos um cenário que tal alteração que foi feita acima nos dois arquivos tenha sido lá no passado e que vc não lembre exatamente o que foi feito ao ponto disso te dar o receio de dar git add e git commit.
    +        No caso, o que poderíamos pensar, seria dar o git status.
    +        Entretanto, o git status só deixa claro quais arquivos sofreram alguma alteração e quais estáo ou não sobre rastreamento.
    +        No caso, ele não exibe o conteúdo dentro da alteração.
    +        Para isso, uma outra alternativa que temos para verificarmos isso seria dando o seguinte comando:
    +            - git diff - Será exibido as linhas que foram ou não adicionados. Para sair do git diff, basta dar Shift + q.
    +                diff --git a/Notas-Aula b/Notas-Aula
    +                index 27dfe82..711764f 100644
    +                --- a/Notas-Aula
    +                +++ b/Notas-Aula
    +                @@ -169,6 +169,72 @@ Seção 04 - Comandos Básicos:
    +                            no changes added to commit (use "git add" and/or "git commit -a")
    +                        Agora, será mostrado os quatro estágios, pois na primeira, não estava sendo exibido o untracked.
    +                        Daí, vamos dar o git add e, em seguida, o git status para verificarmos o que será exibido.
    +                +            On branch master
    +                +            Changes to be committed:
    +                +            (use "git restore --staged <file>..." to unstage)
    +                +                modified:   Notas-Aula
    +                +                modified:   hello.txt
    +                +                new file:   main.txt
    +                +        Em seguida, vamos modificar novamente o arquivo hello.txt, colocando algum texto a mais ou excluindo algo nela, só para criarmos um cenário em que demonstra que tal tipo de alteração não era o que o usuário queria realizar.
    +                +        Em seguida, damos o git status.
    +                +            On branch master
    +                +            Changes to be committed:
    +                +            (use "git restore --staged <file>..." to unstage)
    +                +                modified:   Notas-Aula
    +                +                modified:   hello.txt
    +                +                new file:   main.txt
    +                +
    +                +            Changes not staged for commit:
    +                +            (use "git add <file>..." to update what will be committed)
    +                +            (use "git restore <file>..." to discard changes in working directory)
    +                +                modified:   Notas-Aula
    +                +                modified:   hello.txt
    +                +        Note que, o mesmo arquivo que está em rastreamento est'asendo mostrado como not staged, visto que foi feito a modificação.
    +                +        Se fizermos o git commit -m sobre isso, será considerado o arquivo que está sobre o rastreamento e ignorando a que foi feito a alteração e não colocado dentro do rastreamento.
    +                +        Vamos ver o que acontece, damos o git commit e, em seguida, o git status.
    +                +            leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git commit -m "Versao Quatro"
    +                +            [master 4596956] Versao Quatro
    +                +            3 files changed, 38 insertions(+), 2 deletions(-)
    +                +            create mode 100644 main.txt
    +                +            leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git status
    +                +            On branch master
    +                +            Changes not staged for commit:

- git diff --staged - Isso tbm serve para verificarmos as modificações que ocorreu depois que demos o git add.

Para finalizarmos, vamos dar o git commit e finalizamos a aula.

## Aula 09 - Histórico de Commits:
Vamos ver o histórico.

No caso, o histórico está mais atrelado pela quantidade de commits que ocorreram e por quem foi feito tais commits.

O comando para conseguirmos dar tal acesso seria o seguinte:

- git log - Listará os commits que foram feitos. Para sair tbm, basta dar Shift + q.

    commit af9610d06d50b3d845b7472045b60fb67e7e0428 (HEAD -> master)
    Author: Leozin do grau xavoso <vercel@buudigital.com>
    Date:   Mon Jan 9 10:30:44 2023 -0300

        Versao Cinco

    commit 45969562752673c259180d2fed36f29bc474172e
    Author: Leonardo Takashi Teramatsu <leonardo.teramatsu@gmail.com>
    Date:   Sun Jan 8 19:10:40 2023 -0300

        Versao Quatro

    commit fddac799b96e358912ec749ae0db62296a0d35f0
    Author: Leonardo Takashi Teramatsu <leonardo.teramatsu@gmail.com>
    Date:   Sun Jan 8 18:45:52 2023 -0300

        versao Tres

    commit 9a081123fba91a1150c58aee7b1bd4ed8acf2d19
    Author: Leonardo Takashi Teramatsu <leonardo.teramatsu@gmail.com>
    Date:   Sun Jan 8 18:28:51 2023 -0300

        Versao Segunda

    commit 24660aa4bf94425e5954c6fd08da01cb5d9ecc74
    Author: Leonardo Takashi Teramatsu <leonardo.teramatsu@gmail.com>
    Date:   Sun Jan 8 18:23:09 2023 -0300

        Versao inicial

Note que, no histórico acima foi mostrado quem fez os commits com o seu respectivo email.

A Listagem é feito de forma descrescente, que é do commit recente até o mais antigo.

Note que, temos o HEAD, (HEAD -> master), isso indica literalmente o último conteúdo que foi colocado em algum arquivo.

## Aula 10 - Histórico de Commits - Variações:
Vimos anteriormente que temos o git log, o padrão, para vermos o histórico do que é exibido.

Mas existem casos em que tais históricos ficam variados ou até mesmo saturado de informações.

Muitas vezes, bastaria apenas a informação de mensagem ou do código único do histórico em vez de exibir tudo.

Para isso, bastaria colocar o seguinte comando:

- git log --oneline - Isso mostrará apenas o código único do git e a mensagem, apenas. Não interessa quem foi o autor ou quanto foi feito.

    af9610d (HEAD -> master) Versao Cinco
    4596956 Versao Quatro
    fddac79 versao Tres
    9a08112 Versao Segunda
    24660aa Versao inicial

- git log -N - Onde N pertence ao número natural sem o zero. Indicará a quantidade de logs que vc quer que seja exibido.

    git log -1:
        commit af9610d06d50b3d845b7472045b60fb67e7e0428 (HEAD -> master)
        Author: Leozin do grau xavoso <vercel@buudigital.com>
        Date:   Mon Jan 9 10:30:44 2023 -0300

            Versao Cinco
    git log -3:
        commit af9610d06d50b3d845b7472045b60fb67e7e0428 (HEAD -> master)
        Author: Leozin do grau xavoso <vercel@buudigital.com>
        Date:   Mon Jan 9 10:30:44 2023 -0300

            Versao Cinco

        commit 45969562752673c259180d2fed36f29bc474172e
        Author: Leonardo Takashi Teramatsu <leonardo.teramatsu@gmail.com>
        Date:   Sun Jan 8 19:10:40 2023 -0300

            Versao Quatro

        commit fddac799b96e358912ec749ae0db62296a0d35f0
        Author: Leonardo Takashi Teramatsu <leonardo.teramatsu@gmail.com>
        Date:   Sun Jan 8 18:45:52 2023 -0300

            versao Tres

- git log -p/git log --patch - Serve para caso vc queria que seja exibido não somente o histórico, mas tbm os conteúdos de cada alteração.

- git log --stat - Mostra não somente o que o git log comum mostraria, mas tbm mostra, por meio de + e -, o que foi acrescentado ou apagado, sem exibir o conteúdo.

    commit af9610d06d50b3d845b7472045b60fb67e7e0428 (HEAD -> master)
    Author: Leozin do grau xavoso <vercel@buudigital.com>
    Date:   Mon Jan 9 10:30:44 2023 -0300

        Versao Cinco

    Notas-Aula | 162 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    hello.txt  |   5 ++++-
    main.txt   |   3 ++-
    3 files changed, 168 insertions(+), 2 deletions(-)

    commit 45969562752673c259180d2fed36f29bc474172e
    Author: Leonardo Takashi Teramatsu <leonardo.teramatsu@gmail.com>
    Date:   Sun Jan 8 19:10:40 2023 -0300

        Versao Quatro

    Notas-Aula | 30 +++++++++++++++++++++++++++++-
    hello.txt  |  3 ++-
    main.txt   |  7 +++++++
    3 files changed, 38 insertions(+), 2 deletions(-)

    commit fddac799b96e358912ec749ae0db62296a0d35f0
    Author: Leonardo Takashi Teramatsu <leonardo.teramatsu@gmail.com>
    Date:   Sun Jan 8 18:45:52 2023 -0300

        versao Tres

    Notas-Aula | 24 ++++++++++++++++++++++++
    hello.txt  |  5 ++++-
    2 files changed, 28 insertions(+), 1 deletion(-)

    commit 9a081123fba91a1150c58aee7b1bd4ed8acf2d19
    Author: Leonardo Takashi Teramatsu <leonardo.teramatsu@gmail.com>
    Date:   Sun Jan 8 18:28:51 2023 -0300

        Versao Segunda

    Notas-Aula | 9 +++++++++
    hello.txt  | 2 +-
    2 files changed, 10 insertions(+), 1 deletion(-)

    commit 24660aa4bf94425e5954c6fd08da01cb5d9ecc74
    Author: Leonardo Takashi Teramatsu <leonardo.teramatsu@gmail.com>
    Date:   Sun Jan 8 18:23:09 2023 -0300

        Versao inicial

    Notas-Aula | 134 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    hello.txt  |   1 +
    2 files changed, 135 insertions(+)

- git log --shortstat - Faz o mesmo que o git log --stat, mas sem exibir os arquivos que sofreram a alteração.

    commit af9610d06d50b3d845b7472045b60fb67e7e0428 (HEAD -> master)
    Author: Leozin do grau xavoso <vercel@buudigital.com>
    Date:   Mon Jan 9 10:30:44 2023 -0300

        Versao Cinco

    3 files changed, 168 insertions(+), 2 deletions(-)

    commit 45969562752673c259180d2fed36f29bc474172e
    Author: Leonardo Takashi Teramatsu <leonardo.teramatsu@gmail.com>
    Date:   Sun Jan 8 19:10:40 2023 -0300

        Versao Quatro

    3 files changed, 38 insertions(+), 2 deletions(-)

    commit fddac799b96e358912ec749ae0db62296a0d35f0
    Author: Leonardo Takashi Teramatsu <leonardo.teramatsu@gmail.com>
    Date:   Sun Jan 8 18:45:52 2023 -0300

        versao Tres

    2 files changed, 28 insertions(+), 1 deletion(-)

    commit 9a081123fba91a1150c58aee7b1bd4ed8acf2d19
    Author: Leonardo Takashi Teramatsu <leonardo.teramatsu@gmail.com>
    Date:   Sun Jan 8 18:28:51 2023 -0300

        Versao Segunda

    2 files changed, 10 insertions(+), 1 deletion(-)

    commit 24660aa4bf94425e5954c6fd08da01cb5d9ecc74
    Author: Leonardo Takashi Teramatsu <leonardo.teramatsu@gmail.com>
    Date:   Sun Jan 8 18:23:09 2023 -0300

        Versao inicial

    2 files changed, 135 insertions(+)

## Aula 11 - Alterando um commit:
Por começo, vamos alterar algo dentro dos arquivos hello.txt e main.txt.

Visto que foi feito a alteração acima, vamos fazer um commit simples, seguindo os passos padrão.

Suponhamos que a tal msg que vc colocou no commit não tenha nada haver com o tipo de alteração que vc efetuou.

E que isso poderia ser um problema para um melhor gerenciamento do sistema.

Ao darmos o git log --online -3, por exemplo, será exibido o commit e a msg que foi atribuída para ela.

    8b405dc (HEAD -> master) Alteracao de arquivo
    af9610d Versao Cinco
    4596956 Versao Quatro

No caso, vc quer alterar a msg do commit.

Para isso, bastaria colocar o seguinte comando.

- git commit --amend -m "(msg que vc quer colocar)" - Isso alterará a msg do último commit para o commit que vc quer.

    notes-git git:(master) ✗ git commit --amend -m "Versao Seis"
    [master b3245d1] Versao Seis
    Date: Mon Jan 9 11:05:31 2023 -0300
    3 files changed, 283 insertions(+), 3 deletions(-)

    b3245d1 (HEAD -> master) Versao Seis
    af9610d Versao Cinco
    4596956 Versao Quatro

Basicamente, por baixo dos panos, o que aconteceu foi que o commit descartou o último commit e por cima foi feito uma nova, vide o código único diferente.

Isso, de certa forma, é um problema, quando se o repositório está sendo utilizado em conjunto e que a última pessoa tenha usado o seu último commit, onde vc havia alterado usando o --amend.

Poderia muito bem uma pessoa estar realizando alterações em um commit que nem mais existe, por isso muito cuidado ao usar essa opção.

Agora, vamos realizar mais algumas alterações nos arquivos hello.txt e main.txt, e fazermos um git add e git commit em cima disso, apenas no arquivo hello.txt, supondo que vc tenha achado que foi feito o commit no arquivo main.txt tbm.

Ao darmos o git status, estará lá o main.txt fora do rastreamento, ou seja, esquecido.
Podemos, nesse caso, darmos um git add e git commit, mais uma vez.

Porém isso custará que teremos dois commits no histórico.

E isso, pode ser que no gerenciamento seja problemático, pois o ideal é que em uma tarefa esteja todos os arquivos alterados nela sem haver tal tipo de fragmentação como é feito acima.

No caso, não vamos querer fazer dois commites aqui.

Para resolvermos o problema seriam os seguintes passos:

- git add .

- git commit --amend --nod-edit

    ➜  notes-git git:(master) ✗ git add .
    ➜  notes-git git:(master) ✗ git commit --amend --no-edit 
    [master d461dcf] Mais uma alteracao
    Date: Mon Jan 9 11:19:22 2023 -0300
    3 files changed, 31 insertions(+), 3 deletions(-)

Ao realizarmos agora o git log --oneline -3, vamos ver que

    d461dcf (HEAD -> master) Mais uma alteracao
    b3245d1 Versao Seis
    af9610d Versao Cinco

E dando git log --stat, vamos ver que no último git foi acrescentado o arquivo que vc esqueceu de adicionar.

    commit d461dcf68a25c30e29f4dd22f2f5b1a5e3a8f09f (HEAD -> master)
    Author: Leozin do grau xavoso <vercel@buudigital.com>
    Date:   Mon Jan 9 11:19:22 2023 -0300

        Mais uma alteracao

    Notas-Aula | 27 ++++++++++++++++++++++++++-
    hello.txt  |  4 +++-
    main.txt   |  3 ++-
    3 files changed, 31 insertions(+), 3 deletions(-)

Lembrando, como usamos o --amend, esse último commite será considerado um novo que foi substituído no lugar do que já existia.

- git commit --amend - Abrirá um diretor Vim, que não é nem um pouco simples de se usar. Porém dá para alterar a msg do commit por lá tbm.

Se vc fizer alguma alteração por lá, então para sair seria os seguintes passos:

- esc

- :wq - para manter o que foi escrito e salvar em seguida.

Novamente, ao olharmos o git log, nela aparecerá um novo commit que substituiu o último commit, apenas.

## Aula 12 - Editor de texto padrão:

    https://docs.github.com/en/get-started/getting-started-with-git/associating-text-editors-with-git

O editor de texto vim, é instalado junto no momento em que é instalado o git.
Visto que o vim é um tipo de editor de texto difícil de usar, podemos, sim, voncular um outro editor de texto ao git.

Porém, é necessário que tal editor de texto já tenha sido instalado na sua máquina.
No meu caso, será o VScode.

Agora, vamos à configuração:

- git config --global core.editor "code --wait"

- git commit --amend

Feito os comandos acima, conseguimos abrir, no VScode, o último commit que fizemos para conseguirmos realizar as alterações.

Assim, após realizar as alterações, bastaria vc salvar e simplesmente clicar em fechar, no "x", do arquivo, que tal alteração salva irá ser exibido no terminal.

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git commit --amend
    [master b64def3] Mais uma alteracao de novo [3]
    Author: Leozin do grau xavoso <vercel@buudigital.com>
    Date: Mon Jan 9 11:19:22 2023 -0300
    3 files changed, 31 insertions(+), 3 deletions(-)

Vale lembrar que, via o link que colei acima, podemos considerar outros tipos de editores de textos de forma padrão para realizamos as tais alterações.

Mas temos que ter ciência de alguns editores de texto serão necessários mostrar todo o caminho em que tal editor se encontra para conseguirmos torná-las padrão.

## Aula 13 - Usando commits anterioes:
Visto que sabemos usar o git log de forma versátil.

Mas suponhamos que queremos verificar o conteúdo que estava em um determinado arquivo anteriormente.

No caso, o hello.txt, por exemplo, ele está salvo no seu formato atual, mas se por acaso quisermos saber o que tinha dentro dele na versão anterior?

Uma das alternativas para podermos ver isso é usando o git diff, porém a sua análise por essa via acabaria sendo muito trabalhoso.

Existe sim uma forma mais eficiente de se fazer a tal análise:

- git checkout (número do commit que dá para ser consultado pelo log) - Eu já fiz isso quando estava vendo os pushs que eu havia feito no bitbucket.

Isso fará com que as suas pastas volte nas versões anteriores.

Para voltar para a última versão, bastáriamos dar o checkout para a branch principal em que estamos:

- git checkout master

No caso, o git ele permite que vc navege pela linha temporal de forma a exibir as modificações ou acessar as informações do passado.

## Aula 14 - Desfazendo mudanças - Parte 1:
Existe casos em que a alteração que foi feito por vc não seja acetável.

Então precisamos ter que voltar à versão anterior, ou seja, desfazer as mudanças que foram feitas.

O comando para isso seria o seguinte:

- git checkout (nome do arquivo com a sua extensão)

Todas as suas alterações vão ser perdidas e o arquivo voltará à última versão em que foi salva.

No caso, para salvar o arquivo que foi voltado, bastaria dar os passos git add e git commit.

Agora, se por acaso vc criou algum arquivo novo e foi visto que esse arquivo não era necessário, podemos colocar o segunite comando:

- git clean -f - excluirá todos os arquivos que não estão sobre rastreamento de forma forçado.

Existem casos em que fizemos muitas e muitas alterações e no final nada do que foi feito adiantou e vc queira voltar à estaca inicial, ou seja, à última versão/formato em que estava o seu projeto.

Para dar essa limpa geral, bastaria rodar em sequência os seguintes comandos:

- git checkout .

- git clean -f

Ou seja, isso dará uma limpa geral no teu projeto e voltará ao último formato em que o projeto se encontrava.

## Aula 15 - Desfazendo mudanças - Parte 2:

    https://github.com/DevMasterTeam/Udemy-Git/blob/master/Se%C3%A7%C3%A3o%2004%20-%20Comandos%20B%C3%A1sicos/(Slide)%20Desfazendo%20mudan%C3%A7as.pdf

Existem casos em que vc acaba realizando alterações e dando um git add nela, ou seja, colocando dentro do rastreamento.

O que poderia acontecer disso, é que a tal rastreamento não era o que vc queria considerar caso vc quiser realizar uma varredura geral das modificações e criações de novos arquivos ou diretórios.

Então, tem um caso em que seria necessário desconsiderar ou apagar o que foi rastreado.

Uma das alternativas para isso seria usar o:

- git rm --cached (nome do arquivo e a sua extensão)

Vc consegue tirar o mesmo fora do rastreamento e em seguida dar o git clean para dar uma varredura geral de arquivos/diretórios criados que não estejam sobre rastreamento.

O que não funcionaria seria vc dar o git add e, em seguida, dar o git clean -f.

Ou seja, o git clean -f, como foi visto, não consegue excluir os arquivos e diretórios que estejam sobre o rastreamento.

Muito menos o git checkout (nome do arquivo e sua extensão) não funcionaria para arquivos que já estão sobre rastreamento.

Agora, suponhamos uma situação em que realizamos o git add e, em seguida, tenhamos commitado o arquivo rastreado.

Ao darmos o git status, vamos ver que, antes onde constava git rm --cached, irá aparecer git restore --staged (nome do arquivo com extensão).

No caso, vamos entender melhor os conceitos:

- git rm - serve para conseguirmos excluir arquivos que foram salvos no repositório.

- git restore - so é capaz de remover um arquivo da área de preparação só se tivermos um histórico antes.

Ou seja, ao realizarmos o git add para um arquivo pela primeira vez, no git status aparecerá git rm, agora depois que fizermos o git add, novamente, em um arquivo que já tenha um histórico de commit nele, irá aparecer o git restore.

No caso, não vai adiantar dar um git restore para um arquivo que sequer tenha alguma histórico de commit sobre ele.

Agora, suponhamos em que vc está em cenário em que vc fez várias modificações no projeto, fez vários testes e teve que add e vc viu que nada disso funcionou e vc quer simplesmente voltar à estaca inicial de onde vc começou.

Fazer passo a passo, usando git rm e git restore, para em seguida fazer git checkout e git clean, é um caminho para vc conseguir voltar à estaca inicial.

Entretanto, existe um outro caminho muito mais rápido para vc fazer isso:

- git reset --hard

Isso vai ignorar tudo que estiver acontecendo e irá voltar ao último commit.
Assim, em seguida bastaria dar o git clean -f, para finalizar e chegar no repositório inicial.

Ou seja, o truque aqui é que vc faça vários testes e rastreie várias e várias vezes, mas em nenhum desses passos vc dê o commit.

Contanto que vc não tenha feito o commit, está tudo ótimo, o git reset --hard irá funcionar muito bem junto com o git clean -f.

## Aula 16 - Ignorando arquivos:

    https://github.com/github/gitignore

Existem pastas que é criado automaticaticamente mediante à um projeto que trabalha no software.

Cujas pastas que não são úteis e não precisam ser versionados.

Para isso existe o conceitos de gitignore que dá para ignorar o arquivo.

No caso, como um experimento vamos criar um arquivo gitignore no nosso repositório.

Com o diretório do projeto que vc trabalha em aberto basta rodar o seguinte:

- touch .gitignore

Isso irá criar um arquivo gitignore.

Ao darmos o git status, vc verá que ele aparece como untracked.

Agora, vamos criar um arquivo bmp e este será o arquivo que será ignorado.

No caso, dentro do seu diretório projeto criemos um arquivo via bitmap:

- Pelo linux, entra no arquivo diretório/projeto pelo terminal e nela insira o comando bitmap

- No file vc salva ela em o nome de abc.

Agora, dando o git status, esse arquivo bmp irá aparecer como untracked.

Agora, no .gitignore vamos colocar o seguinte:

    *.bmp
    #config.txt

O símbolo "*" indica que é para considerar, sem importar o nome, qualquer arquivo que tenha uma extensão x, neste caso o .bmp.

No caso, estou pedindo para ignorar qualquer arquivo que tenha extensão bmp.

Como prova disso, se dermos git status, vamos ver que esse arquivo bmp que criamos não aparece nela.

O mesmo se colocarmos o nome do arquivo com a sua extensão, se fizermos algo do segunite tipo

    abc

    config.txt

Ao darmos o git status, nem o abc e nem o config.txt irá aparecer no status.
Para saber quais tipos de arquivos que podemos ignorar isso estará no link inical dessa aula.

Dentro dela terá a explicação de todos os arquivos que o .gitignore pode considerar.

## Aula 17 - Parar de rastrear um arquivo:
Agora, vamos supor o seguinte cenário.

Primeiro, vamos criar um arquivo html, index.html, e dentro dela colocar apenas o seguinte:

    <html></html>

Agora, ao darmos o git status, vamos ver que ela estará como untracked, então vamos dar o git add para ela.

Em seguida, vamos comitar.

Feito isso, vamos, em seguida, acrentar o head

    <html>
        <head></head>
    </html>

Vamos fazer, novamente, o git status.

Agora, no .gitignore, vamos colocar o *.html para pedir que ignore qualquer arquivo com extensão html.

Novamente, damos o git status para certificarmos se está ou não ignorando.

Pela surpresa, vemos que mesmo colocando essa extensão no gitignore, o index.html é mostrado pelo git status.

O ponto é que o git já conhece esse arquivo.

Já está no radar esse index.html, ou seja, antes mesmo de ter colocado no gitignore para ignorar a tal extensão, esse index.html já estava presente e foi dado o git add nela, então o git não ignorou.

Como prova disso, ao criarmos um outro arquivo html, desta vez, no git status não irá aparecer, pois tais arquivos novos não estão dentro do rastreamento do git.

Mas existe uma forma de conseguirmos dizer ao git em deixar de rastrear um dado arquivo.

- git update-index --skip-worktree (nome do arquivo e sua extensão)

Ao rodarmos isso, podemos tirar o index.html fora do rastreamento do git e isso fará com que o o .gitignore funcione sobe esse arquivo.

Bastar dar o git status para conferirmos isso.

No caso, o git parou de monitorar esse arquiv index.html.

Mas se por acaso vermos que o arquivo que háviamos tirado do rastreamento do git vermos que, na verdade, ela é importante a ser considerado?

Então rodamos o seguinte comando:

- git update-index --no-skip-worktree (nome do arquivo com a sua extensão)

Vamos ver que isso irá reconsiderar o index.html dentro do rastreamento e como prova disso bastaríamos dar o git status.

Um detalhe importante ao realizamos o uso do git update-index --skip-worktree é que estamos considerando que tal arquivo passe a estar fora de coideração à partir desse momento.

Ou seja, o que foi salvo no passado vai ficar salvo no passado, ou seja, se no passado tivermos dado um commit no index.html esse comando de cima não vai apagar esse dado que ficou registrado.

## Aula 18 - Clonando repositório:

    https://github.com/DevMasterTeam/Udemy-Git

Até agora, estamos trabalhando dentro de uma repositório que está salvo localmente, ou seja, na sua máquina.

No caso, chegamos um ponto em que precisamos salvar esse repositório em uma nuvem de forma que permita um trabalho remoto dos projetos.

Então, se tivermos algum repositório em que mais pessoas acessem, haverá casos em que será necessário sincronizarmos tais repositórios baixando-as no sua máquina.

Vamos aprender um comando que permita fazer uma aplicagem do repositório que servirá tanto em repositório remoto quanto para reposiório local.

- git clone (nome do repositório que vc quer clonar) (nome do repositório que vc quer atribuir sobre)

Saindo de um nível do seu diretório/projeto basta rodar o comando acima.

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos$ git clone notes-git gitclone
    Cloning into 'gitclone'...
    done.

Note que, foi possível realizar a clonagem acima e se olharmos no diretório estudos, lá estará o diretório notes-git e o seu clone, gitclone.

Ao entrarmos dentro do repositório gitclone e darmos git log dentro dela, veremos que até os históricos e as informações salvas estão nelas.

O que aconteceu agora é um controle de versão distribuído na prática.

Agora, vamos clonar um repositório remoto, que é o link que criamos acima.

- git clone https://github.com/DevMasterTeam/Udemy-Git.git

Rodamos isso saindo do diretório projeto e estando dentro do diretório estudos.
Assim, conseguimos acessar o repositório na sua máquina local.

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos$ ls
    apps      htmls_e_assets   mmorpg_got                notes-git
    gitclone  instagram_clone  node-mongodb-native-main  Udemy-Git
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos$ cd Udemy-git
    bash: cd: Udemy-git: Ficheiro ou pasta inexistente
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos$ cd Udemy-Git
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/Udemy-Git$ ls
    README.md                             'Seção 09 - Source Control Management'
    'Seção 02 - Sobre controle de versão'  'Seção 10 - Tags'
    'Seção 04 - Comandos Básicos'           Website
    'Seção 07 - Branches'
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/Udemy-Git$ git log
    commit 1ffc94ea819c03248eb8573fe5b3c313b5962282 (HEAD -> master, origin/master, origin/HEAD)
    Author: DevMasterTeam <devmasterteam@gmail.com>
    Date:   Sat Sep 3 00:16:40 2022 -0300

        Adição de link para pasta Website.

    commit 8ddabeaeb7a291797ead7476512e7355aa592f3a
    Author: DevMasterTeam <devmasterteam@gmail.com>
    Date:   Sat Sep 3 00:15:38 2022 -0300

        Organização de pastas. Versionamento de slides. Alteração README.

    commit 5d1c9a89e066adf34e944cbb90f8e4327c9fe9bd
    Author: Gabriel Ferrari Ceron <devmasterteam@gmail.com>
    Date:   Fri Aug 12 21:43:38 2022 -0300

        Adição imagens, readme e license.

    commit 7c198bfd2b99b5d5d0a24252edbb6a782a0f4493
    Author: Gabriel Ferrari Ceron <devmasterteam@gmail.com>
    Date:   Fri Aug 12 21:31:23 2022 -0300

        Primeiro commit. Curso Git.