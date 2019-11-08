# Procurando os posts

Agora vamos aprender algo novo do Rails: as `rotas`, que nada mais são do que caminhos que o Rails cria ao criarmos algo novo. Isso tudo acontece naquele primeiro comando que executamos para criar o Post (bundle exec rails scaffold...), lembra?

As rotas, ficam num arquivos chamado `routes.rb`. Você pode encontrar ele na pasta `config`, dentro da pasta do projeto. Vamos abrir esse arquivo, nele, deve haver uma linha com o conteúdo abaixo:

```sh
resources :posts
```

Ok, mas o que isso significa? O Rails já cria muitas coisas para a gente. Nessa linha, ele cria automaticamente todos os caminhos para criarmos, atualizarmos, vermos, e excluirmos um post.

Você pode aprender mais sobre rotas nos seguintes links:
- [https://www.caelum.com.br/apostila-ruby-on-rails/rotas/#8-7-exercicio-rotas](https://www.caelum.com.br/apostila-ruby-on-rails/rotas/#8-7-exercicio-rotas)

- [http://www.devmedia.com.br/introducao-a-rotas-e-responders-no-ruby-on-rails/33521](http://www.devmedia.com.br/introducao-a-rotas-e-responders-no-ruby-on-rails/33521)


Agora, se formos no navegador, naquele endereço que fomos antes, mas adicionando `/posts` no fim, como o exemplo:

```sh
https://3000-ae53535c-e0af-4f52-85ab-413b0022ecff.ws-us02.gitpod.io/posts
```
PS: Lembrando que a parte inicial do link é o da sua aplicação.

Vamos ver a imagem abaixo. Uhuul!! Podemos criar nossos posts agora :D

![Lista de Posts](../images/rails/lista_posts.png)

Mas calma! E se eu quiser que quando eu acessar o site, ele caia direto na tela dos posts ao invés daquela tela do Rails?

Podemos fazer isso também, vamos lá!

### Dizendo pro rails que a primeira tela é a de posts

Vamos abrir o arquivo `routes.rb` de novo. Lembra onde ele está? Em `config/routes.rb`.
Vamos mudar algo nele: Agora, as duas primeiras linhas devem estar assim:

```ruby
Rails.application.routes.draw do
  resources :posts
```

Altere ele para que fique assim:

```ruby
Rails.application.routes.draw do
  root 'posts#index'
  resources :posts
```

Nós adicionamos a linha root `posts#index`, que diz ao Rails que ao acessarmos a url inicial do projeto ele deve enviar para a tela dos posts na ação index (logo falaremos sobre ações :) )

Lembre de reiniciar o seu servidor com Ctrl + C no terminal e em seguida:

```sh
bundle exec rails server
```

### E quando acessamos no navegador agora...

Acessando a url sem o `/posts` no final, vamos ver a tela abaixo!

![Lista de Posts](../images/rails/lista_posts.png)

Lindo!!! Agora o Rails entende que a primeira tela deve ser a de posts :D
