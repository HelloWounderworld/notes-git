# Seção 12 - Comandos Intermediários e Avançados:

## Aula 01 - Revertendo Commits:
Dizemos que fizemos um commit com problema. Ou seja, acabei commitando algo que não deveria ter commitado.

Bom, uma alternativa é rodar um git diff nesse commit e ver quais alterações foram feitas e desfazer as alterações feitas manualmente, uma por uma. Claro, em um contexto em que há uma carga de alteração extremamente alta fica inviável esse tipo de processso de reversão.

Bom, nesse caso, vc pode usar o seguinte comando

    git revert

Pois, imagina em um contexto em que vc sobe algo em produção e isso acabou quebrando o site. Se isso acontece a ideia é que vc volte o quanto antes possível na forma anterior, em vez de ficar verificando uma por uma as alterações pelo git diff, o que não seria conveniente em uma urgência. Para isso, vc usar o git revert da seguinte forma

    git revert HEAD

Ao colocarmos esse comando, temos que entender que ela não irá simplesmente voltar à versão anterior, mas, sim, ele irá criar um novo commit com os contéudos de uma versão anterior acima da versão bugada que vc commitou.

Agora, se vc quiser reverter o que já foi revertido, basta jogar

    git revert HEAD --no-edit

Ao darmos o "git log --online" vamos ver que foi dado uma reversão do commit que foi revertido.

## Aula 02 - Desfazendo Commits:
Agora, vamos ver como desfazer os commits.

Primeiro, vamos entender quais as diferenças entre reverter commits e desfazer um commit.

Enquanto que o git revert ele apenas reverte mantendo os outros commites que vc fez no histórico, ao contrário disso, desfazer o commit, literalmente, vc tira do commit que vc fez apagando ela do histórico, como se nunca tivesse existido.

No caso, se quisermos, literalmente, apagar o nosso atual commit e voltar à uma versão anterior, bastaria jogar

    git reset --hard HEAD

Mas lembrando que precisamos colocar o número nisso.

Assim, se vc quiser desfazer uma série de commits anteriores, vc pode colocar o seguinte

    git reset --hard HEAD~n

sendo "n" é um número natural não nulo indicando a quantidade de commits anteriores que vc queira desfazer.

Se colocarmos, por exemplo, o seguinte

    git reset --hard HEAD~1

ao darmos "git log --online" vc verá que o commit em que vc estava não existe mais e vc voltou à exatamente um commit anterior,nem colocando o git diff vc não conseguirá verificar as alterações.

DEixa eu te ensinar um macete de caso vc quiser commitar sem a necessidade de ter que fazer o passo do "git add ."

    git commit -a -m "bla bla bla"

O "-a" acima ele serve para já add e, em seguida, commitar com a msg.

Agora, visto que vc commitou como acima e vc quer desfazer o commit mas sem perder as alterações que vc fez. Então, bastaria rodar o seguinte

    git reset --mixed HEAD~n

O comando acima nos permitirá desfazer o commit do histórico, mas o conteúdo que foi alterado não será desfeito tbm. Ao rodarmos o comando acima, bastaria vc dar um "git diff" para verificar que, de fato, as alterações que vc fez não foi perdida, mas ao darmos "git log --online" vamos ver que o commit foi desfeito. Além disso, ao darmos o git status vc verá que estamos no estágio em que precisamos dar o "git add ." caso as nossas alterações sejam commitadas de novo.

Agora, suponhamos que queremos não somente apagar um commit do histórico, mas tbm não perder as alterações, mas não queremos chgar no estágio em ter que dar o "git add ." de novo. Ou seja, que ele fique no modo monitorado já. Então para isso bastaria jogar o seguinte

    git reset --soft HEAD~n

Ao darmos o "git status" vamos ver que as alterações que vc fez não foi perdida e ela já está sobre o radar. Mas ao darmos "git log --online" vamos ver que o commit seu já foi apagado do histórico.

## Aula 03, 04 e 05 - Forçando envio de mudanças - Parte 1, 2 e 3:
Quando desfazemos os commit, como foi abordado na última aula, só que esse commit era uma que foi dado o push para o repositório remoto, a próximo push que vc realizar acaba não sendo possível dar o push padrão. Pois o que vai acontecer é que estaríamos enviando um outro commit que está ligado, por exemplo, à um commit anterior do commit que havía sido apagado, coisa que na estrutura de commit não estará sendo exibido dessa forma na parte remota.

Para esses tipos de situações vamos precisar forçar o envio de mudanças

    git push --force

Mas lembre-se que o comando acima é extremamente delicado e precisa de muito, mas muito, cuidado para a sua utilização. Motivo disso, seria pelo fato de que o histórico/log do git do repositório será inteiramente mudado para o histórico/log local. Por isso, para vc usar esse comando, vc precisaria ter certeza e absoluta que a estrutura do histórico local seu está certo e é o que deve ser constado no histórico do repositório. Toda essa explicação se deve, pelo fato, de que se nessa mudança brusca, no histórico de commits do repositório remoto tiver algum dado importante, correrá o risco de que alguns dados de relevância acabam sendo aniquilado sem condições de resgatá-las.

Ainda mais quando vc estiver usando um repositório em conjunto com várias pessoas, esse comando coloca em risco de perder dados até de outras pessoas integrantes do seu grupo. Ou um outro problema que pode acontecer seria de que se um dos integrantes do grupo, ter feito um "git clone" do repositório antes do push. Isso significa que o histórico/log desse integrante está na forma de antes e ter dado o push force. O que isso pode resultar??

Bom, basicamente, seria que o fato de o histórico desse integrante estar como antes de ter dado o git force, ao ela dar um "git push" padrão, novamente, poderá sobrescrever completamente o histórico de git remoto trazendo as mudanças que haviam dado problema antes e, cujo o commit, havía sido desfeito. Ou seja, nisso fará com que, agora, o histórico da pessoa que havía dado o "git push --force" entre, novamente, em conflito com o formato do histórico que está no repositório remoto.

Bom, visto quais problemas poderia acontecer acima, então sempre que for usar um "git push --force" em um repositório que tem muita gente usando ela, seria de boas práticas ocorrer alguma regra de negócio que comunique à todos sobre essa mudança brusca que ocorreu e que todos consigam atualizar o seu histórico de git como consta no repositório remoto.

Agora, vamos imaginar o seguinte cenário. Suponhamos que ocorreu alguma alteração diretamente no repositório remoto, ou seja, uma pessoa alterou algum arquivo ou diretório que está no repositório remoto diretamente e foi feito um commit remotamente. E vc sem ter a ciência disso vc está realizando uma alteração localmente e pretende mandar essa alteração para o repositório remoto. Bom, como no seu histórico tem um commit que não está presente como no repositório remoto, claro que ao dar o "git push" isso implicará em um erro. Uma forma bem violento de resolver esse cenário a pessoa que realizou a alteração local dar um "git push --force". Entretanto, isso poderá trazer problemas futuros nas regras de negócio do projeto ou até mesmo um conflito com o próprio integrante do grupo. Logo, existe um outro comando que força a sobrescrição, mas de forma mais amigável, que antes mesmo de realizar a tal alteração brusca ela verifica se essa alteração brusca não colocará em risco de perder algum dado ou se há algum conflito de dados importantes. O comando seria

    git push --force-with-lease

Bom, basicamente, essa sobrescrição ocorrerá somente em situações em que foi visto que nenhum dado será perdido.

Logo, no cenário em que descrevi acima, se por acaso usarmos esse comando acima, "git push --force-with-lease", o processo não será bem sucedido, pois como foi descrito, como há um commit no histório remoto que não está no históŕico local, se aceitarmos a sobrescrição brusca, isso implicará em perda de dados. Logo, para resolver esse problema, seria legal realizar os passos

    git pull => git push --force-with-lease

Ao realizarmos isso no cenário acima, vamos ver que não haverá nenhum problema, pois, primeiro, vc atualizou o seu histórico de git e ainda foi necessário realizar o merge para só depois disso vc realizar o push forçado.

Obs: Reforçamos que o estudante, se necessário, reforce os estudos feito sobre esse conceito que foi abordado, pois, por ela ser algo bem delicado, é bem importante que esse conceito esteja bem firme na cabeça do estudante para que ele consiga seguir as boas práticas.

Seguir o link de leitura

    https://www.atlassian.com/br/git/tutorials/syncing/git-push
    https://git-scm.com/docs/git-push/pt_BR
    https://dev.to/paulogoncalvesbh/pare-de-usar-git-push-force-4ngd
    https://github.com/PauloGoncalvesBH/treinamento-git#puxando-as-altera%C3%A7%C3%B5es-pull
    https://pt.stackoverflow.com/questions/458820/como-reverter-o-git-push-force

## Aula 06 e 07 - Rebase - Parte 1 e 2:
Seguir o link de leitura

    https://www.simplilearn.com/git-rebase-vs-merge-article#:~:text=The%20Workings%20of%20Git%20Rebase%20and%20Merge,-Git%20rebase%20takes&text=In%20the%20process%2C%20rebase%20flattens,history%20of%20the%20source%20branch.
    https://www.treinaweb.com.br/blog/git-merge-e-git-rebase-quando-usa-los

O rebase ele serve, basicamente, muito parecido com uma espécie de merge. Ou seja, ele serve para vc conseguir mesclar os feitos de duas branches. Entretanto, um detalhe que precisamos tomar muito cuidado seria que, além da mesclagem das alterações feitas, ela mescla tbm o histórico inteiro da outra branch pra uma outra branch, ou seja, está ocorrendo uma unificação de duas branches.

Bom, o rebase, ao usarmos ele, precisamos tomar muit, mas muito, cuidado tbm, pois ela é de um uso muito delicado. O fato de ocorrer essa unificação de duas branches, isso significa que corre o risco de ocorrer algum conflito. Mas conflito em que sentido?

O tipo de conflito que acontece seria análogo ao que aparece no merge. Ou seja, o formato como é exibido o conflito é muito similar ao merge, donde a pessoa teria que realizar a mesclagem manual verificando o que fica e o quê não ficará na alteração.

Depois de feito as mudanças manuais bastaria vc dar o

    git rebase --continue

para dar continuidade no processo de unificação das branches.

Caso vc opte por não querer mais fazer o "git rebase" bastaria rodar

    git rebase --abort

Isso irá mostrar tbm em que ponto ocorreu o conflito.

## Aula 08 - Rebase - Pull:
Seguir o link para leitura

    https://pt.stackoverflow.com/questions/279562/qual-a-diferen%C3%A7a-entre-git-pull-e-git-pull-rebase
    https://www.gitkraken.com/learn/git/git-rebase
    https://sdq.kastel.kit.edu/wiki/Git_pull_--rebase_vs._--merge
    https://www.golinuxcloud.com/git-pull-vs-git-pull-rebase/

Basicamente, o rebase pull ele serve para caso o histórico seu da branch local não estiver atualizado com o histórico da branch remota, vc consiga realizar uma sobrescrição das coisas que foram feita na branch remota sobre a sua banch local sem perder as alterações que ocorreram tanto por do remoto quanto local. Isso serve tbm para que no histórico da branch não apareça nenhuma msg de foi feito um merge, pois, as vezes, isso pode poluir visualmente do que foi feito no histórico. Claro, todo rolê vai acontecer na mesma branch.

## Aula 09 - Recriando branch baseada no servidor:
Esse caso serve para dar um reset geral no histórico da sua branch local.

Basicamente, o cenário é o seguinte. Suponhamos que no histórico da sua branch local temos um commit que foi apagado em um push forçado por outra pessoa e vc não saiba disso. Claro que ao realizar alguma alteração sua e quando vc for dar o "git push" isso não ocorrerá e, além disso, se vc dar o "git pull" isso implicaria em merge e esse processo estaria sendo exibido no histórico da sua branch local o que continua tendo conflito com o histórico da branch remota.

Daí, a solução mais rápida para esse caso é vc dando um reset geral. Ou seja, basicamente, vc só dar um "git clone" onde puxará todo o histórico igualzinho ao que está no remoto e seguir os passos adiante. Mas suponha que nem isso vc não possa fazer? Então para isso, vc preciaria realizar os seguintes passos

    git checkout -b (nome da branch nova - primeiro tu cria uma nova branch)
    git branch -D (nome da branch que vc quer dar o reset geral)
    git fetch origin (nome da branch remota que vc quer puxar tudo)

Bom, até esse ponto, vc terá baixado tudo, inclusive o histórico, da branch remota que vc queria para à branch nova que vc criou. Mas, o que vc quer mesmo é que essas informações que vc baixou sejam exibidas na mesma branch com o mesmo nome localmente. Para isso, vc só precisaria fazer 

    git checkou (o mesmo nome da branch remota que vc baixou a informação)

Daí, automaticamente, o que foi baixado de informação da branch remota, será transferida para a branch que vc criou localmente com o mesmo nome da branch remota. Para a confirmação disso, bastaria dar "git pull" para verificar que, de fato, está tudo igualzinho ao branch remota.

## Aula 10 - Rebase - Squash:
Seguir o link de leitura

    https://medium.com/cwi-software/utilizando-rebase-e-squash-para-melhorar-o-hist%C3%B3rico-do-git-fdb2d952c09c#:~:text=Em%20vez%20de%20criar%20um,hist%C3%B3rico%20de%20commits%20%C3%A9%20reescrito.
    https://thoughtbot.com/blog/git-interactive-rebase-squash-amend-rewriting-history

O rebase com o squash ela serve para resolver a seguinte situação. Suponhamos que vc estava realizando as alterações no projeto e cada alteração vc fazia um "git commit". Daí, ao olharmos o histórico, um passo antes de darmos o "push", vc percebe que todos os commits que vc havía dado, em vez de ter dado commit pedaço por pedaço, vc poderia juntar todas elas. Exatamente para esse tipo de cenário que podemos usar o rebase e squash para conseguirmos resolver isso sem a necessidade de termos que fazer um amend o ou um reset brusco.

O comando, basicamente, é o seguinte

    git rebase --interactive HEAD~n

sendo "n" um natural não nulo menor ou igual à quantidade de commits do histórico. Feito isso, isso irá abrir um editor de códigos donde aparecerá os commits. Em cada numeração do commits teremos o "pick", bastaria substiturmos essas palavras para "squash" exceto o commit que estiver na primeira linha. Daí, feito isso, bastaria salvar e fechar o arquivo. Disso, irá abrir um um outro arquivo que vai indicar se não ficará confuso, "This is the commit message #2" (algo do tipo), daí bastaria vc apagar os títulos de commits junto essa msg e deixar somente o título do commit da primeira linha, que foi o único que vc não mudou para "squash". Assim, basta salvar e fechar. Bom, se tudo ocorrer certo, aparecerá uma msg no bash dizendo "Successfully rebased and updated (path)". Daí, para confirmar que de fato os commits foram fundidos, bastaria dar

    git diff (número do commit que foi fundido)

Nela será exibido as alterações dos outros gits que vc fez e que foi fundido ao primeiro git.

Basicamente, o que aconteceu em todo esse processo foi que quando unificamos os commits foi criado um outro novo commit e isso implica, até pela funcionalidade do rebase, na alteração do timeline do projeto. Ou seja, se por acaso vc estiver utilizando a branch com outras pessoas e quiser realizar essa junção dos commits, vc estará alterando inteiramente o histórico do projeto e ao dar o push force, vc estará caindo novamente no problema de correr o risco de perda de dados dos seus outros coleguinhas. Daí, o recomendável seria que sempre que vc for fazer isso, antes mesmo de executar o processo parear junto com os seus coleguinhas para combinar o jogo.

## Aula 11 - Cherry pick:
Seguir o link de leitura

    https://coodesh.com/blog/candidates/aprenda-o-que-e-cherry-pick-do-git-e-como-aplicar-para-agilizar-seus-projetos/
    https://blog.geekhunter.com.br/git-cherry-pick-o-que-e-quando-usar/
    https://git-scm.com/docs/git-cherry-pick
    https://www.atlassian.com/git/tutorials/cherry-pick

O cherry pick ele serve para vc conseguir trazer um determinado commit de uma branch para uma outra branch específica. O comando basicamente é o seguinte

    git cherry-pick (número no commit)

Isso fará com que em uma determinada branch específica que vc criou o commit acima seja mergiado para vc conseguir dar procedimento à partir desse ponto. Basicamente, ela serve como um processo de isolamento de um determinado commit para visualizar o que foi feito ou dar continuidade à partir disso em diante.

## Aula 12 - git bisect:
Seguir o link de leitura

    https://git-scm.com/docs/git-bisect/pt_BR#:~:text=Cada%20vez%20que%20o%20comando,commit%20que%20introduziu%20a%20propriedade.
    https://www.rafaelhdr.com.br/blog/git/usando-git-bisect-para-descobrir-origem-de-bug
    https://imasters.com.br/desenvolvimento/dica-git-da-semana-git-bisect

O comando bisect ele nos ajuda a encontrar, muitas vezes a raíz do problema, ou seja, esse comando ele serve para verificar qual foi a primeira vez em que um determinado problema começou a acontecer.

Basicamente, a busca que ela faz é via binário, muito parecido com a demonstração do teorema de bolzano-weiestrass.

O comando é o seguinte

    git bisect

Em seguida, ela pergunta "status: waiting for both  good and bad commits", nisso vc terá que escolher o "good" com o número do commit em que vc quer começar a pegar e que o erro que vc viu no commit acima não estava mais acontecendo.

    git bisect good (número do commit1)

Em seguida, vc coloca "bad" e o número do commit onde estava acontecendo o tal problema

    git bisect bad (número do commit2)

Feito isso, vc estabelece um intervalo entre commit1 e commit2 donde ocorrá a busca binária, seguindo a ideia do bolzano-weiestrass.

Ou seja, devemos entender para estabelecer o intervalo, seria "good" para commit1 que é onde não estava mais acontecendo nenhum problema e "bad" para o commit2 onde mostra o problema sendo que

    commit1 < commit2 - Do ponto de vista da ordem de aparição na fila

Isso refinaria a busca e facilitaria em saber qual foi a primeira aparição do erro.

No caso, feito os passos acima, ele irá exibir o título de um dos commits que vc salvou que está dentro desse intervalo. Em seguida, a ideia para refinar mais ainda é verificar se esse commit ele é de fato o que aparece o erro. Se não aparece vc digita

    git bisect good - Serve como o axioma da escolha da demonstração do bolzano-weiestrass para vc escolher um termo da sequência.

E isso irá fazer uma nova busca binária de forma mais refinada. E, o processo se repete de forma finita até que o commite que a busca binária exibe é de fato a primeira vez em que o erro acontece. Quando aparecer a primeira vez em que o erro aparece, aí sim vc digita

    git bisect bad

E em seguida, se, de fato, for esse commit que vc quer, basta vc digitar

    git bisect good

Daí, ele exibirá o histórico em que foi feito o commit e o número da mesma. Ou seja, assim, bastaria vc guardar o número do commit, visto que vc encontrou o commit que faz aparecer o erro. Em seguida, para sairmos da investigação, bastaria vc digitar

    git bisect reset

## Aula 13 - Fetch:
Seguir o link de leitura

    https://www.freecodecamp.org/portuguese/news/git-fetch-x-git-pull-qual-e-a-diferenca-entre-os-dois-comandos/
    https://metring.com.br/para-que-serve-o-git-fetch-vs-pull
    https://git-scm.com/docs/git-fetch/pt_BR

O git fetch ele tem uma similaridade com o git pull. A diferença é que se tivermos um commit no repositório remoto que não tenhamos no nosso histórico de commits local e darmos o git fetch, ele nos trará a atualização, mas ainda não irá sobrescrever o nosso histórico atualizando ela. No caso, feito um git fecth, bastaria vc dar "git branch -a" para mostrar tudo o que o git fetch nos trouxe e darmos o "git log --online" para ver que, de fato, o commit que está no repositório não foi atualizado no histórico local.

Basicamente, o "git pull" ele é uma composição do "git fech" e "git merge", sendo que quando damos o git pull não sabemos exatamente o que está vindo para ser feito o merge. Por isso, o "git fetch" ele serve primeiro para trazer as atualizações sem dar o merge para te dar possibilidade de verificar o que está vindo para a atualização. Dado o "git fetch" podemos em seguida dar o "git branch -a" para ver a path em que foi trago do repositório remoto e, em seguida, darmos o "git diff (path do que foi trago no repositório remoto)" para ele exibir o que será trago de atualização e te dar a opçõa de se vc prefere dar o merge ou não.
