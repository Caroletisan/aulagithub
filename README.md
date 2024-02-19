<h1 align="center">ENGENHARIA DE DADOS E BIG DATA</h1>

<p align="center">🚀 Ambiente git para versionamento de código do projeto</p>

<h2 href="#git-init">1 - Iniciando um Repositório</h2>
<pre class=" language-bash" tabindex="0">
    <code class=" language-bash">$ git init
</code></pre>

<h2>2 - adicionando um repositório remoto</h2>
<pre class=" language-bash" tabindex="0">
    <code class=" language-bash">$ git remote add origin LINK_DO_REPS
</code></pre>

<h2>3 - Listando Arquivos Modificados</h2>

<pre class=" language-bash" tabindex="0"><code class=" language-bash">$ git status
</code></pre>

<h3>4 - Arquivos não monitorados</h3>

<p>Se o arquivo foi modificado mas você ainda não executou <code>git add</code>, um simples <code>git checkout</code> removerá as alterações, deixando o arquivo como ele estava no último <code>commit</code>. Passe o nome do arquivo a ter as alterações desfeitas ou <code>.</code> para desfazer as alterações em todos os arquivos modificados. Muito útil se você está apenas experimentando um código mas não quer que ele seja salvo.</p>

<pre class=" language-bash" tabindex="0"><code class=" language-bash">git checkout .
</code></pre>

<p>Esse comando não apaga novos arquivos. Para apagar novos arquivos que ainda não foram adicionados ao Stage, execute:</p>

<pre class=" language-bash" tabindex="0"><code class=" language-bash">git clean -df
</code></pre>

<h3>5 - Removendo arquivos do Stage</h3>

<p>Se você executou <code>git add</code> e quer desfazer, use o <code>reset</code>.</p>

<pre class=" language-bash" tabindex="0"><code class=" language-bash">git reset
</code></pre>

<p>Para desfazer as modificações, após o <code>reset</code> use o <code>checkout</code> ou <code>clean</code> mostrados anteriormente.</p>

<h3>6 - Desfazendo o último commit</h3>

<p>Caso você tenha feito alterações e já tenha chegado a realizar um <em>commit</em>, para desfazer é necessário usar o <code>revert</code>.</p>

<pre class=" language-bash" tabindex="0"><code class=" language-bash">git revert HEAD
</code></pre>

<p><b>OBS.:</b> Será criado um novo commit indicando que o último commit foi desfeito. lembre-se também que esse comando apaga novos arquivos.</p>

<h2>7 - Renomear Commit</h2>

<pre class=" language-bash" tabindex="0"><code class=" language-bash">$ git commit --amend
</code></pre>

<h2>8 - Listando Branches ("-a" informa as branchs do repositório remoto)</h2>

<pre class=" language-bash" tabindex="0"><code class=" language-bash">$ git branch -a
</code></pre>

<h2>9 - Indo para outra branch</h2>

<pre class=" language-bash" tabindex="0"><code class=" language-bash">$ git checkout minha-branch
</code></pre>

<p>Se você adicionar <code>-b</code>, uma nova <em>branch</em> será criada.</p>

<pre class=" language-bash" tabindex="0"><code class=" language-bash">$ git checkout -b minha-nova-branch
</code></pre>

<h2>10 - Excluindo branches</h2>

<p>Para excluir uma branch local basta executar o comando <code>branch</code> com <code>-d</code> ou <code>-D</code>, passando o nome da branch que você quer apagar.</p>

<pre><code class="language-bash">git branch -d nome-da-branch
git branch -D nome-da-branch
</code></pre>

<p>A opção <code>-d</code> é mais segura, pois ela só apaga a branch se você já tiver feito merge ou enviado as alterações para seu repositório remoto, evitando perda de código.</p>

<p>A opção <code>-D</code> ignora o estado da sua branch, forçando a sua remoção.</p>

<p>Esse comando apaga apenas a branch local, não removendo branches remotas.</p>

<h2>11 - Renomeando branches</h2>

<p>Para renomear a sua atual branch local, execute o comando <code>branch</code> com a opção <code>-m</code>, passando o novo nome.</p>

<pre><code class="language-bash">git branch -m novo-nome-da-branch
</code></pre>

<p>Se você estiver em uma branch e quiser renomear outra, você deve passar primeiro o nome atual da branch que quer renomear:</p>
<pre><code class="language-bash">git branch -m nome-atual novo-nome
</code></pre>

<h2>12 - Branch Órfã</h2>

<p>Uma branch órfã tem esse nome porque ela não está ligada à branch principal, então seus históricos não são compartilhados.</p>

<pre><code class="language-bash">          i---j---k     &lt;== branch 'minha branch'
         /
a---b---c---d---h---l   &lt;== branch 'main'
     \         /
      e---f---g         &lt;== branch 'minha outra branch'
	  
1---2---3---4			&lt;== branch `órfã`
</code></pre>

<p>Isso pode ser útil quando você quer colocar mais de um projeto em um mesmo repositório. Um bom exemplo é quando você tem um projeto no Github e quer criar um site para divulgar o seu projeto. A aplicação e o site são coisas diferentes, portanto os códigos deles devem ser versionados separadamente. Ter ambos em um mesmo repositório simplifica o gerenciamento.</p>

<p>Para criar uma branch órfã basta usar o comando:</p>

<pre><code class="language-bash">git checkout --orphan minha-branch-orfa
</code></pre>

<h2>13 - Visualizando o Histórico de Commits</h2>

<pre><code class="language-bash">$ git log
</code></pre>

<p>Você ainda pode adicionar mais parâmetros a esse comando, como: <code>-p meus-arquivos</code>, você pode indicar nomes de arquivo ou de um diretório para ver o histórico apenas de um grupo de arquivos ao invés do projeto inteiro, <code>--autor=nome-autor</code>, para filtrar um autor, <code>$ git log --after=&quot;MMM DD YYYY&quot; </code>, ou <code>
$ git log --before=&quot;MMM DD YYYY&quot;</code>, para mostrar o histórico de commits feitos antes ou após uma data (exemplo do formato usado nas datas: “Jul 07 2019”), <code>git log --grep produtos</code>, para mostra o histórico de commits filtrado por uma mensagem, com esse comando teremos o histórico de commits em que a mensagem do commit possua a palavra “produtos”, o que passamos pode ser uma expressão regular, e podemos passar mais de uma: <pre><code class="language-bash">// procurar por &quot;produtos&quot; OU &quot;usuarios&quot;
$ git log --grep produtos --grep usuarios

// procurar por &quot;produtos&quot; E &quot;usuarios&quot;
$ git log --grep produtos --and --grep usuarios
</code></pre>
</p>

<h2>14 - Exibir branches em um modo mais legível</h2>
<p>É possível mandar imprimir o histórico exibindo as branches do repositório com algo mais legível e com cores com um comando. Teremos um resultado parecido com esse:</p>

<pre><code class="language-bash">* a102055 (HEAD -&gt; main) commit 8
| * 196d28e (branch-2) commit 7
| * 07e073c commit 3
| * 2b077ca new fie
| | * c1369d8 (branch-3) commit 6
| | * d11bdcd commit 5
| |/
|/|
* | 2b22b75 commit 2
|/
* d5a12b0 .gitignore
* 9535426 -- commit 1
</code></pre>

<p>O comando é um pouco comprido:</p>

<pre><code class="language-bash">git log --all --decorate --oneline --graph
</code></pre>

<p>Para decorar tudo o que devemos escrever depois de <code>log</code>, lembre-se de <strong>A DOG</strong></p>

<ul>
<li>–<strong>a</strong>ll</li>
<li>–<strong>d</strong>ecorate</li>
<li>–<strong>o</strong>neline</li>
<li>–<strong>g</strong>raph</li>
</ul>

<h2>15 - Atalhos Personalizados</h2>

<p>Podemos criar atalhos para não ficar escrevendo comandos grandes como o do exempo anterior.</p>

<h2>16 - Criando atalhos personalizados</h2>

<p>Para criar atalhos personalizados, basta adicionar uma configuração, passando o nome que você quiser para o <code>alias</code>.</p>

<p>Por exemplo, se eu quiser que o comando ensinado anteriormente fosse chamado a partir do atalho <code>dog</code>:</p>

<pre><code class="language-bash">//deixar o comando disponível apenas no repositório atual
git config alias.dog &quot;log --all --decorate --oneline --graph&quot;
//deixar o comando global em sua máquina, ficando disponível para qualquer repositório
git config --global alias.dog &quot;log --all --decorate --oneline --graph&quot;
</code></pre>

<p>Como os comandos serão do Git, não precisamos ficar chamando-o. Note que o comando passado para o atalho não inicia com <code>git</code>.</p>

<p>Para remover os atalhos basta executar:</p>

<pre><code class="language-bash">//atalhos locais
git config --unset alias.dog
//atalhos globais
git config --global --unset alias.dog
</code></pre>

<p>Agora podemos ter o comando do exemplo anterior apenas executando <code>$ git dog</code>.</p>

<h3>17 - Listando atalhos personalizados</h3>

<p>Para exibir uma lista de atalhos personalizados, podemos executar o comando <code>git config -l</code>, que lista todas as configurações do seu Git. O problema é que esse simples comando vai listar todas as configurações. Podemos fazer um comando mais sofisticado para ele listar apenas os nossos atalhos personalizados e ainda organizá-los em ordem alfabética:</p>

<pre><code class="language-bash">git config -l | grep ^alias\. | cut -c 7- | sort
</code></pre>

<p>O comando é grande, mas tudo bem, pois agora você sabe criar atalhos, não é mesmo? Podemos, por exemplo, criar um atalho com o nome <code>alias</code>:</p>

<pre><code class="language-bash">git config alias.alias &quot;! git config -l | grep ^alias\. | cut -c 7- | sort&quot;
</code></pre>

<p>Por comandos como <code>grep</code> e <code>sort</code> não serem do Git, tivemos que iniciar a linha de comando com <code>!</code>. Perceba que por causa disso, nossa primeira instrução teve que chamar o Git.</p>

<p>O <code>$ git config -l</code> lista as configurações do Git. Pegamos o retorno e passamos ao comando <code>$ grep</code>, que serve para fazer busca de textos. Como queremos os atalhos, que vimos que começa com “alias”, mandamos o <code>grep</code> buscar por tudo que começa com <code>alias.</code>. Para termos uma lista mais limpa, usamos o comando <code>cut</code> para remover a parte “alias.” do nome dos atalhos. Por fim, usamos o comando <code>sort</code> para ordenar nossos atalhos em ordem alfabética.</p>

<h2>18 - Trabalhando em mais de uma coisa sem fazer commit</h2>

<p>Pode haver momentos em que você precisa parar o que está fazendo e começar a trabalhar em outra tarefa. Porém, pode não ser bom fazer o commit de algo que ainda não foi finalizado para depois voltar nele, resultando em um commit que ficará no histórico mas que possui um código que não funciona. Nós podemos salvar essas alterações feitas mesmo sem precisar realizar um commit para depois voltar a trabalhar nela, o que é chamado de <em>Stash</em> (algo como “esconder” ou “acumular”).</p>

<p>Ao fazer isso, seu repositório voltará ao estado do último commit, e as alterações feitas anteriormente estarão “escondidas”.</p>

<h3>19 - Salvando modificações em um Stash</h3>

<p>Simplesmente execute o comando <code>stash</code></p>

<pre><code class="language-bash">$ git stash
</code></pre>

<p>Você ainda pode colocar um nome nesse stash:</p>

<pre><code class="language-bash">$ git stash push -m meu-novo-stash
</code></pre>

<h3>20 - Listando Stashes</h3>

<p>Você pode fazer vários stashes. Para listá-los, execute o comando:</p>
<pre><code class="language-bash">$ git stash list
</code></pre>

<h3>21 - Recuperando modificações</h3>
<p>Se algo foi salvo no stash, basta executar o seguinte comando para recuperar as alterações que foram jogadas lá:</p>

<pre><code class="language-bash">$ git stash apply
</code></pre>

<p>Isso vai recuperar o código do stash mais recente. Se quiser recuperar um stash mais antigo, basta ver o número do stash que aparece quando o listamos e passar para o seguinte comando:</p>
<pre><code class="language-bash">$ git stash apply stash@{2}
</code></pre>

<h3>22 -  Removendo Stashes</h3>

<p>Quando nós recuperamos alterações de um stash, ele continua guardado. Para apagá-lo da pilha, execute o comando <code>drop</code> junto ao nome do stash que você quer remover:</p>

<pre><code class="language-bash">$ git stash drop stash@{5}
</code></pre>

<p>Se você quiser recuperar o código de um stash e já apagá-lo, pode usar o comando <code>pop</code> no lugar do <code>apply</code>.</p>

<h2>23 - Juntando alguns pedaços do trabalho</h2>

<p>Pode ser que você esteja trabalhando em uma <em>branch</em> e queira fazer o <em>merge</em> do código dela com outra <em>branch</em>, mas não quer juntar o trabalho inteiro, apenas um commit específico. Isso é possível com o <code>Cherry Pick</code>.</p>

<pre><code class="language-bash">git cherry-pick id-do-commit
</code></pre>
