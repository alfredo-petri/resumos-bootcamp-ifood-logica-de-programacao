
# Principais comandos GIT BASH

Todos comandos abaixo listados podem ser encontrados na [documentação oficial git](https://git-scm.com/doc).

## Comandos para configurar o GIT

**Locais de armazenamento de váriaveis de configurações**  

**--global** - local usado para alterar configurações do usuário que está usando o git e o **git hub**.

**--system** - local usado para alterar configurações do sistema operacional, o que envolve todos os usuários.

**--local** - local usado para alterar configurações de um determinado repositório local **git**.

**Comandos**

**git config** -  este comando é para configurar o git, deve ser usado em conjunto com um dos locais acima ou mais algum comando. 

**git config --global user.name "exemplo-nome"** - este comando define o nome que será usado nos commits a partir do momento desta definição, caso este seja alterado futuramente os nomes dos comites anteriores não serão modificados.

**git config --global user.email definir-email@exemplo.com** - este comando define o email que será usado nos commits a partir do momento desta definição, caso este seja alterado futuramente os emails dos comites anteriores não serão modificados.

**git config --global init.defautBranch exemplo-nome** - este comando define o nome da branch principal do repositório, normalmente utiliza-se o nome main como nome da branch principal.  

O comando **git config --list** -  lista todas as configurações feitas, também podemos definir um local específico, como: **--global**. Então ao utilizarmos o comando **git config --global --list** teremos acesso a todas as configurações feitas no usuário.

Existem mais configurações que podem ser feitas, abaixo serão listados alguns **links de referência=** 

- [configurações básicas - referência](https://git-scm.com/docs/git-config)
- [configurações básicas - ebook](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)

## Conexão com o Github

Existem 3 formas seguras de realizar autenticacação entre o git e o github: 
* leia mais sobre [autenticação via token](https://docs.github.com/pt/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)
* leia mais sobre [autenticação via chave SSH](https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
* leia mais sobre [autenticação em 2 fatores (senha + outra etapa)](https://docs.github.com/pt/authentication/securing-your-account-with-two-factor-authentication-2fa/configuring-two-factor-authentication)


## Comandos para manipulação de arquivos e pastas no terminal

**cd** - este comando usado para acessar um diretório, temos algumas opções de como usar o comando **cd**:

- usando somente o comando **cd** será acessado o diretório raiz do usuario local.
- para acessar a um determinado diretório deve-se especificar o caminho do mesmo. Ex: **~/desktop/projects**
- para retornar a uma pasta de um nível anterior usamos **cd ..**

**ls** - este comando usado para listar o conteúdo de um diretório.

**mkdir** - este comando cria um novo diretório no local especificado. Após o comando definimos o nome do novo diretório. Ex: **mkdir nova-pasta**

**cat** - este comando exibe o conteudo de um arquivo

**touch** - este comando pode ser usado para criar um novo arquivo, após o comando definimos o nome e extensão do novo arquivo. Ex: **touch novo-arquivo.txt**

**mv** - este comando pode ser usado para mover ou renomear um arquivo. Para mover um arquivo devemos indicar o caminho atual do mesmo e seguida o caminho de destino. Ex: **mv teste/arquivo.txt nova-pasta/arquivo.txt**. Para renomear um arquivo usamos o comando logo em seguida devemos informar o nome e extensão do arquivo que desejamos alterar após isso definimos o novo nome e extensão do arquivo. Ex: **mv arquivo.txt arquivo-novo.txt**

**rm** - este comando remove um arquivo do diretório/repositório, após o comando devemos informar o nome e extensão do arquivo que desejamos excluir. Ex: **rm diretório/arquivo.txt**


## Comandos para controlar os repositórios versionados

### Comandos para git (repositório local)

**git init** - cria um novo repositório no git, para isso precisa estar localizado dentro do diretório ou então indicar o caminho do diretório que se deseja versionar.

**git status** - verifica o status do repositório, da dicas sobre o que pode ser feito a segui, cita alguns comandos uteis.

**git add** - adiciona todas as alterações (criação de novos arquivos ou pastas, ou modificação dos ja existentes) feitas no repositório à área de staging.

**Obs:** podem ser adicionados arquivos especificos através do comando **git add nome-do-arquivo-1, nome-do-arquivo-2, etc...** ou adicionar todos de uma vez através do comando **git add .**

**git commit** - adiciona todas as alterações (criação de novos arquivos ou pastas, ou modificação dos ja existentes) que estão na área de staging ao repositório local.  Pode-se também adicionar uma mensagem ao commit pelo comando **git commit -m "exemplo de mensagem ou descrição das alterações feitas"**

**gitignore** - é um  arquivo que contém lista de arquivos e pastas que devem ser ignorados nos commits realizados, para isso basta criar o arquivo através do comando **touch .gitignore** e em seguida abrir o arquivo e criar uma lista dos nomes dos arquivos e pastas à serem ignorados, cada linha do **.gitignore** representa um arquivo ou pasta que deve ser ignorado, as linhas vazias não surtem efeito.

**git log** - exibi o histórico de commits realizados no repositório.

### Desfazendo alterações GIT (repositório local)

**rm -rf .git** - este comando é usado caso algum diretório tenha sido versionado por engano é possivel remover este versionamento. Para isso deve-se entrar na pasta raiz do diretório que esta versionado e entao usar o comando **rm -rf .git

**git restore** - este comando restaura um arquivo ao estado do último commit. Este é um comando muito útil para desfazer alterações incorretas. **Obs:** deve-se ter muito cuidado ao utilizar este comando, pois ele descarta todas as alterações feitas no arquivo.

**git commit --amend -m""** - este comando é utilizado para alterar a mensagem usada no ultimo commit realizado, para isso deve-se usar o comando **git commit --amend -m""** entre os parenteses deve-se colocar a nova mensagem. EX: **git commit --amend -m"nova-mensagem"**. 

**git reset** - este comando é usado quando desejamos voltar ao estado de um dos commits anteriores. o comando **git reset** possui 3 modos: **--soft, --mixed, --hard**


Modo | Descrição
:---:|:---|
--soft | ao utilizar o **git reset soft** o diretório retorna ao estado do commit selecionado, mas os arquivos e alterações que foram feitos posteriormente à aquele commit são enviados a staged area.
--mixed | este é o modo padrão portanto pode-se usar tanto **git reset mixed** quanto apenas **git reset**, nesta opção o diretório retorna ao estado do commit selecionado, mas os arquivos e alterações que foram feitos posteriormente à aquele commit são enviados a untracked area. 
--hard | ao utilizar o comando **git reset hard** o diretório retorna ao estado do commit selecionado, todos os arquivos e alterações que foram feitos posteriormente à aquele commit são elimidados.

Ao aplicar este comando deve-se utilizar o comando seguido do modo e por fim o hash (chave) do commit alvo. EX: **git reset "modo" "hash"**.

A imagem abaixo exemplifica o comando sendo usado no modo padrão:

![gitigore](https://github.com/alfredo-petri/resumos-bootcamp-ifood-logica-de-programacao/blob/main/git-e-github/gitignore.png)

A linha em destaque é o **hash** do commit.

**Obs:** Caso deseje ver o histórico das alterações feitas pelo **git reset** basta utilizar o comando **git reflog**.

### Comandos para GitHub (repositório remoto)

**git remote add origin** - adiciona um caminho para o repositório remoto, para isso é preciso copiar o caminho do repositório existente no github. Ex: **git remote add origin https://github.com/nome-da-conta/nome-do-repositorio.git**

**Obs:** dependendo das configurações do repositório no github pode ser necessário utilizar algum metodo adicional de autenticação, como os acima mencionados  

**git remote -v** exibi o caminho do repositório remoto ao qual o seu repositório local está vinculado.

**git push** - envia todas as alterações presentes no repositório local para o repositorio remoto, para isso a conexão entre os repositórios deve ter sido estabelecida anteriormente através do comando acima.

**git clone** - usado para adicionar uma cópia do conteudo de algum repositório remoto ao seu repositório local, para isso é preciso copiar o caminho do repositório existente no github. Ex: **git clone https://github.com/nome-da-conta/nome-do-repositorio.git** também pode ser alterado nome do diretório ao copia-lo para o repositório remoto, para isso é necessario especificar o novo nome após a url no comando git clone. Ex: **git clone https://github.com/nome-da-conta/nome-do-repositorio.git novo-nome** 

**Obs:** dependendo das configurações do repositório no github pode ser necessário utilizar algum metodo adicional de autenticação, como os acima mencionados  

**git pull** - baixa as alterações que constam no diretório remoto para o diretório local mesclando ambos.

**git fetch** - baixa as alterações que constam no diretório remoto para o diretório local sem mesclar as informações.

### Trabalhando com Branches no GitHub

Os comandos a seguir são muitos utilizados quando se trabalha em uma equipe de desenvolvimento, envolvendo mais pessoas que irão manipular o diretório, ou podem simplesmente ser usados para criar/testar uma nova funcionalidade do projeto, consertar umbug, etc, sem afetar os arquivos principais do projeto.

**git checkout 'nome-branch'** - este comando alterna entre as branches existentes no repositório, para isso devemos informar o nome da branch a qual desejamos acessar.

**git checkout -b 'nome-nova-branch'** - este comando cria uma nova branch com o nome definido no comando e em seguida alterna para esta branch.

**git branch** - este comando lista todas as branchs existentes no repositório.

**git branch -v** - este comando lista os ultimos commits de todas as branchs existentes no repositório.

**git merge** - este comando mescla uma determinada branch à nossa branch principal, para isso deve-se aplicar o comando seguido do nome da branch que será mesclada à branch principal. Ex: **git merge nome-da-branch**.

**git branch -d** - este comando exclui uma determinada branch, ara isso deve-se aplicar o comando seguido do nome da branch que será excluida. Ex: **git merge nome-da-branch**.

**git diff** - este comando exibe as diferenças entre o conteudo de 2 branchs, para isso deve-se executar o comando seguido dos nomes das branchs que seram comparadas. Ex **git diff branch1 branch2**.

Em algumas situações deseja-se clonar apenas o conteudo de uma determinada branch. Para isso utiliza-se o comando **git clone** (acima mencionado) seguido da **url** do repositório remoto, em seguida especificamos a branch que desejamos clonar através do comando **--branch** seguido do nome da branch e por fim indicamos que deseja-se clonar apenas o conteudo desta branch através do comando --single-branch. Ex: **git clone url --branch nome-da-branch --single-branch**.

**git stash** - este comando arquiva modificações feitas em uma branch.

**git stash list** - este comando lista todas as modificações arquivadas.

**git stash pop** - este comando restaura a modificação mais recente que foi arquivada e em seguida apaga a mesma da lista de modificações arquivadas.

**git stash apply** - este comando restaura a modificação mais recente que foi arquivada, mas mantém a mesma na lista de modificações arquivadas.

Para obter mais informações sobre branchs acesse a documentação oficial a partir de um dos links abaixo: 

- [Branching and Merging (refences)](https://git-scm.com/docs)
- [Git Branching (e-book)](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)
