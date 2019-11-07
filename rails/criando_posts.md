# Vamos criar alguns posts, para ver o que acontece?

Agora podemos ver a tela dos nossos posts! Mas ainda não cadastramos nenhum, vamos fazer isso?

Acesse o blog pelo navegador.

Agora podemos clicar em **New Post** e vamos ir para outra tela, como a imagem abaixo.
Podemos preencher os campos com as informações do post e clicar no botão **Create Post**

![Novo post](../images/rails/novo_post.png)

Após clicar no botão **Create Post**, vamos ir para uma página e vai ter a lista com os post que criamos.

### Erro com o Authenticity Token

Caso você encontrar o erro abaixo, vamos ter que fazer uma pequena alteração no código.

![Erro do token de autenticação](../images/rails/authenticity_token_error.png)

Este erro ocorre porque estamos acessando uma aplicação que está rodando numa máquina em outro domínio. Para resolvermos isso para os fins deste tutorial, vamos acessar o arquivo `app/controllers/posts_controller.rb`

Na segunda linha, vamos adicionar o seguinte código:

```ruby
  skip_before_action :verify_authenticity_token
```

Em seguida, vamos reiniciar o servidor e vamos criar um post novamente.

Ué? Não aparece nada!

Se você atualizar a tela, verá que o post foi criado. Mas não queremos ter que fazer isso todas as vezes não é mesmo? Então vamos fazer algumas modificações para que o projeto redirecione para a URL correta da nossa página inicial.

### Configurando o host

Primeiro vamos abrir o arquivo `config/environments/development.rb`. Este arquivo contém diversas configurações para que possamos executar localmente o projeto.

Na linha 3, vamos adicionar o seguinte texto:

```ruby
config.hosts << ENV['RAILS_ALLOWED_HOST'].gsub('https://', '') if ENV['RAILS_ALLOWED_HOST']
```

Esta linha adiciona aos hosts possíveis todos os hosts existentes na variável RAILS_ALLOWED_HOST. A função `gsub` apenas substitui o `https://` com um texto vazio.

Vamos salvar o arquivo e a partir de agora vamos iniciar o servidor com o seguinte comando:

```ruby
RAILS_ALLOWED_HOST=$(gp url 3000) bundle exec rails s -b 0.0.0.0 -p 3000
```

Mas que coisa complicada! Calma, vamos por partes:

`RAILS_ALLOWED_HOST` é a variável que estamos utilizando para identificar os hosts aceitos pela aplicaçao. Em seguida, com `=$(gp url 3000)`, estamos atribuindo um valor a ela. `gp url 3000` é um comando do `Gitpod`. Ele pega a url que estamos usando para enxergar a aplicação no browser e indica a porta 3000. Em seguida, usamos o comando rails que a gente já conhece `bundle exec rails s -b 0.0.0.0 -p 3000` usando o `-b` para indicar o IP (no caso estamos dizendo que não queremos localhost) e `-p` para indicar a porta.

A partir de agora vamos ser sempre redirecionados para a URL correta.

![Post criado](../images/rails/post_criado.png)

A tela vai ter os dados do post que acabamos de criar, e uma mensagem de que foi criado com sucesso.

**Mas a mensagem está em inglês, assim como um monte de outras coisas.**

Vamos mudar isso?

### Vamos começar pelas mensagens

Vamos começar a mexer no código agora :D

Vamos abrir o arquivo `posts_controlles.rb`, que é o arquivo que controla todas as ações sobre os posts (lembra que comentamos sobre isso ao criar a rota?). Ele está em `app/controllers/posts_controller.rb`

Esse arquivo tem vários _métodos_ (lembra como são métodos no ruby?), que estão separados nas ações de criar (_create_), atualizar (_update_), excluir (_destroy_), _index_ (lembra a ação que colocamos no routes.rb?) - esta será a ação que lista todos nossos posts, _show_ (mostrar o post).

Todas essas _ações_, são métodos padrões que o Rails cria automático para nós, quando executamos aquele primeiro comando para criar o Post.

Agora, vamos procurar no arquivo onde estão as mensagens que aparecem, quando criamos ou atualizamos um post.
Por exemplo, você pode procurar o método `create`, deve ser algo como o código abaixo:

```ruby
def create
    @post = Post.new(post_params)

    respond_to do |format|
      if @post.save
        format.html { redirect_to @post, notice: 'Post was successfully created.' }
        format.json { render :show, status: :created, location: @post }
      else
        format.html { render :new }
        format.json { render json: @post.errors, status: :unprocessable_entity }
      end
    end
  end
```

Esse é o método chamado quando clicamos no botão **Create post**.
Ele cria um post novo, com os dados que colocamos nos campos e retorna o html que mostra o post, informando a mensagem. Vamos primeiro mudar a mensagem de sucesso. Você pode procurar o método `create`, na linha onde está escrito

```ruby
format.html { redirect_to @post, notice: 'Post was successfully created.' }
```

Vamos alterar para

```ruby
format.html { redirect_to @post, notice: 'O post foi criado com sucesso.' }
```

O método todo deve ficar mais ou menos assim:

```ruby
def create
    @post = Post.new(post_params)

    respond_to do |format|
      if @post.save
        format.html { redirect_to @post, notice: 'O post foi criado com sucesso.' }
        format.json { render :show, status: :created, location: @post }
      else
        format.html { render :new }
        format.json { render json: @post.errors, status: :unprocessable_entity }
      end
    end
  end
```

Agora é a sua vez, pode fazer o mesmo no método **update** e **destroy** :D

### Vamos testar a mensagem nova?

Vamos acessar no navegador a mesma url que foi usada antes :)

Vamos criar um post novo, e ver o que acontece.

![Post criado com mensagem em português](../images/rails/post_criado_portugues.png)

Yeyy, nossa mensagem está em português!


### Continuando...

Precisamos conversar um pouquinho sobre outraaaa linguagem, **HTML**. Vai ser rapidinho ;P
