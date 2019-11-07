## Criando uma pasta

Que tal tentar criar um diretório na sua área de trabalho? Para enxergarmos o nosso diretório com maior facilidade, vamos primeiro sair da pasta do projeto (você pode observar na lista de arquivos da esqueda que temos vaaaarios arquivos que vão dificultar encontrarmos nossa nova pasta). Nós vamos, então, subir um nível de pasta, ou seja, vamos de `/workspace/railsgirls/railsgirls` para `/workspace/railsgirls` com o comando a seguir:

```sh
$ cd ..
```

Se repetirmos o comando anterior `pwd` devemos ter uma resposta diferente:

```sh
$ pwd
/workspace/railsgirls
```

**Nota:** Você pode perceber que o texto que temos logo antes do `$` também muda. No Gitpod, sempre sabemos onde estamos na hierarquia de pastas olhando para o caminho logo após do nome de usuário (`gitpod`) e antes do `$`. Fácil, não?

Agora que saímos da pasta com diversos arquivos, vamos criar uma nova pasta. Você pode fazer assim:

```sh
$ mkdir umapasta
```

Este comando cria uma pasta com o nome **umapasta** no diretório em que você está (/workspace/railsgirls/railsgirls). Após executar este comando, a pasta deve ter sido criada. Vamos verificar se a pasta está lá?