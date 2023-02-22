# Seção 05 - Github:

## Aula 01 - Introdução ao GitHub:
Crie a sua primeira conta com o plano gratuito:

    https://github.com/

## Aula 02 - Criando Repositório:
Vamos criar o nosso primeiro repositório.

O nome para o repositório precisa ser único.

Essa parte não tem jeito, é melhor aprender vendo o vídeo.

## Aula 03 - Endereço do Repositório:
No caso, vamos aprender a verificar qual é o endereço do repositório que tivemos acesso.

Uma via simples de vermos isso é verificando o code do repositório que vc criou no github.

Entretanto, para um repositório que vc tem em sua máquina existe uma forma de verificarmos se esse repositório ele é de origme remoto ou não.

- git remote -v

Basta jogar esse comando acessando o repositório existente em sua máquina pelo terminal.

No caso, o diretório/repositório Udemy-Git que havíamos baixado de um repositório github, ao rodarmos o comando acima, ela exibe tais dados

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/Udemy-Git$ git remote -v
    origin	https://github.com/DevMasterTeam/Udemy-Git.git (fetch)
    origin	https://github.com/DevMasterTeam/Udemy-Git.git (push)

Indicando a origem em que esse reposítorio veio.

Já no notes-git que temos feito criado na máquina local, ao rodarmos o comando acima, ele não é exibido nada.

Agora, podemos realizar o seguinte.

Criamos o diretório temp no diretório estudos e acessamos ela.
Nela rodamos o git init.

Em seguida, rodamos o git remote -v, que não aparecerá nada.

Isso indica, assim como para notes-git, que esse repositório não tem um repositório remoto associado.

Mas podemos mudar isso fazendo o seguinte:

- git remote add origin (url do repositório remoto)

Daí teremos o seguinte, a url foi pego do reposítorio que foi criado.

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos$ mkdir temp
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos$ cd temp
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/temp$ git init
    Repositório vazio Git inicializado em  /home/leonardo/Documentos/estudos/temp/.git/
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/temp$ git remote -v
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/temp$ git remote add origin https://github.com/DevMasterTeam/Udemy-Git.git^C
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/temp$ git remote add origin https://github.com/HelloWounderworld/notes-git.git
    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/temp$ git remote -v
    origin	https://github.com/HelloWounderworld/notes-git.git (fetch)
    origin	https://github.com/HelloWounderworld/notes-git.git (push)

Agora uma observação ao "origin" que aparece antes de indicar a url destino.

Esse "origin" ele é um padrão para indicar de quem veio. Podemos personalizar esse "origin".

No caso, quando colocamos "git remote add (origem de quem veio) (url do repositório remoto)", vc consegue mostrar de quem veio esse repositório remoto.

No caso, a vantagem disso é que ela permite que seja apontado para diversos tipos de repositórios.

Ou seja, a partir de um repositório x que está na máquina local, podemos apontar esse repositório para y e z, donde os dois são remotos, de tal forma que a alteração que foi feito no repositório x pode ser enviado no y para realizar testes e depois, visto que está tudo funcionando, ser enviado no repositório z.

Até para o caso quando for alterado o nome do repositório remoto onde vc irá querer dar o push.

Vc consegue atualizar o novo nome que foi dado ao repositório da seguinte forma

- git remote sert-url (origem de quem veio) (url do repositório remoto)

O comando acima irá alterar a url do repositório de origem.

## Aula 04 - Salvando mudanças no servidor:
Vamos clonar o repositório que criamos no github.

Vimos que, agora, o github está criando a branch padrão como main.

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git branch
    * main

Agora, vamos copiar e colar todas as coisas que tem no repositório Udemy-Git que havíamos baixado antes.

Em seguida, vamos dar o git add e git commit, quando dou o commit é o momento em que todos os meus arquivos são versionados.

Agora, vamos precisar enviar esse versionamento para o repositório do github.
Precisamos ver se é possível darmos o push.

Para isso, vamos precisar dar o git status para verificarmos se isso é possível.

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git status
    On branch main
    Your branch is ahead of 'origin/main' by 1 commit.
    (use "git push" to publish your local commits)

    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
        modified:   Notas-Aula

    no changes added to commit (use "git add" and/or "git commit -a")

Então, damos o git push, visto que a msg acima exibido.

Motivos de não estar sendo possível dar o push:

    https://danizavtz.com.br/git-github-the-requested-url-returned-error-403/

Para resolvermos esse problema, vamos ter que realizar o mesmo procedimento que é feito no Bitbucket:

    https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

Feito as burocracias acima e dado o push, irá aparecer a seguinte msg

    leonardo@leonardo-Dell-G15-5520:~/Documentos/estudos/notes-git$ git push
    Enumerating objects: 5, done.
    Counting objects: 100% (5/5), done.
    Delta compression using up to 16 threads
    Compressing objects: 100% (3/3), done.
    Writing objects: 100% (3/3), 880 bytes | 880.00 KiB/s, done.
    Total 3 (delta 2), reused 0 (delta 0)
    remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
    To github.com:HelloWounderworld/notes-git.git
    b2c9f7f..82864fb  main -> main

Isso indicará que deu certo o push.

Uma outra funcionalidade que vem no git, ao realizar a sua instalação, é o git credentials manager.

Nela vc pode configurar o usuário e a senha, para que nas próximas vezes em que vc der o push não ter que dar o trabalho de ficar toda hora digitando.

Agora, pelo Github, podemos verificar o nosso histórico de commits desse repositório em que estamos trabalhando e os tipos de arquivos que estão sendo ou não adicionados ou removidos.

## Aula 05 - Baixando a última versão do repositório:
Suponhamos uma situação em que o projeto que vc havía baixado para sua máquina local e que vc estava realizando as devidas modificações sobre elas, esteja desatualizado.

Ou seja, enquanto vc estava realizando as mudanças uma outra pessoa havia dado um push no mesmo repositório remoto em que vc baixou na sua máquina na mesma branch.

Vamos precisar atualizar esse projeto em que vc está mexendo.

No caso, pelo Github, vamos alterar o arquivo main.html, onde está o texto "Lorem ipsum dolor sit amet, consectetur adipiscing elit.", vamos substituir por "Aprendendo Git".

Visto que agora o projeto que vc tem na sua máquina do mesmo repositório está desatualizado, vamos precisar atualiza-la.

Para isso o comando seria o seguinte:

- git pull

Note que, ao darmos esse comando acima, temos a seguinte msg.

    remote: Enumerating objects: 7, done.
    remote: Counting objects: 100% (7/7), done.
    remote: Compressing objects: 100% (4/4), done.
    remote: Total 4 (delta 3), reused 0 (delta 0), pack-reused 0
    Unpacking objects: 100% (4/4), 773 bytes | 257.00 KiB/s, done.
    From github.com:HelloWounderworld/notes-git
    82864fb..3b0342a  main       -> origin/main
    Updating 82864fb..3b0342a
    Fast-forward
    Website/main.html | 4 ++--
    1 file changed, 2 insertions(+), 2 deletions(-)

Ao mesmo tempo, ao vermos o arquivo main.html, nela estará mostrando a alteração feita.

## Aula 06 - Star, observe e fork:
Leitura:

    https://www.analyticsvidhya.com/blog/2021/07/analyzing-popular-repositories-on-github/

    https://pt.stackoverflow.com/questions/143458/o-que-essas-palavras-significam-no-git-github-fork-clone-track

    https://docs.github.com/pt/get-started/exploring-projects-on-github/saving-repositories-with-stars

    https://git-scm.com/book/pt-br/v2/GitHub-Contribuindo-em-um-projeto

## Aula 07 - Pull request:
Leitura para conceito:

    https://docs.github.com/pt/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request

Basicamente, ele serve para submeter as suas mudanças para um projeto que vc estiver trabalhando do outro.

A submissão irá passar por análise do dono do projeto se ele irá ou não aceitar tal mudança.

No caso, o pull request é uma forma de vc conseguir realizar alguma contribuição para o trabalho de outra pessoa.

Basicamente, é isso que pode enriquecer drásticamente o seu currículo, pois se vc realizar alguma contribuição para um projeto bem grande, mesmo não tendo nenhum retorno financeiro para ti, isso irá pesar muito no seu currículo.

## Aula 08 - Issue, milestones, labels:
Leituras:

- Issue:

    https://pt.stackoverflow.com/questions/101706/pra-que-serve-o-issue-no-github

    https://docs.github.com/pt/issues/tracking-your-work-with-issues/creating-an-issue
    
    https://imasters.com.br/desenvolvimento/5-dicas-sobre-issues-e-comentarios-no-github
    
- Milestones:

    https://pt.stackoverflow.com/questions/160607/para-que-serve-o-campo-milestone-no-github#:~:text=A%20funcionalidade%20milestone%20(etapa%20em,para%20a%20etapa%20estar%20completa.

    https://docs.github.com/pt/issues/using-labels-and-milestones-to-track-work/creating-and-editing-milestones-for-issues-and-pull-requests

    https://eltonminetto.dev/post/2017-11-13-boas-praticas-tarefas-pr-commits/
    
- Labels:

    https://docs.github.com/pt/issues/using-labels-and-milestones-to-track-work/managing-labels

    https://docs.github.com/pt/rest/issues/labels?apiVersion=2022-11-28

## Aula 09 - Arquivo READ.me:

    https://dillinger.io/

No link acima estará as funcionalidades mais comuns de se utilizarem ao arquivo README.md para possibilitar que vc personalize o seu READ.me para finalidades que vc queria.
Vale salientar que o arquivo READ.me, ela serve como uma espécie de apresentação do projeto, sobre vc em sí, etc...

Um bom portifólio de github, implica em vc ter um bom READ.me para apresentação.

## Aula 10 - Chave SSH:
Isso foi resolvido na aula 04 dessa seção.