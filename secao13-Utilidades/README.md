# Seção 13 - Utilidades:

## Aula 01 - Alias:
Basicamente, o alias ele serve para vc conseguir configurar alguns comandos de git de forma bem mais abreviada.

Seguir link de leitura

    https://gist.github.com/kelvinst/331aff32508e2517afbd
    https://www.git-scm.com/book/en/v2/Git-Basics-Git-Aliases#_git_aliases

## Aula 02 - Grep:
Seguir o link de leitura

    https://git-scm.com/docs/git-grep

O grep ele não é uma linguagem do git, mas, sim, do linux shell. Basicamente, se vc quiser realizar uma busca de um conjunto de nomes usando siglas, vc pode usar o grep.

Por exemplo, suponhamos que tenhamos um conjunto de branchs

    main
    r1-taks1
    r1-taks2
    r1-taks3
    r1-taks4
    r1-taks5

Daí, queremos ver quas branchs existem de "r1", então bastaria rodar

    git branch | grep r1

Lembrando que a sigla, não precisa ser o que inicia, basta que ela esteja contida no nome.

Da mesma forma, para outras formas de git que permite uma listagem, podemos usar o grep para filtrarmos a busca.
