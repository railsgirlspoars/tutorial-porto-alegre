## Limpando

Não queremos deixar uma bagunça, então vamos remover tudo o que fizemos até agora.

Primeiro precisamos voltar para a pasta projects:

```sh
$ cd ..
```

Fazendo cd para .. nós mudaremos do diretório atual para o diretório pai (que significa o diretório que contém o diretório atual).

Veja se você se encontra na pasta projects:

```
$ pwd
/workspace/railsgirls
```

Agora é hora de excluir o diretório **umapasta**.

**Atenção:** A exclusão de arquivos usando del, rmdir ou rm é irrecuperável, significando _Arquivos excluídos vão embora para sempre!_

Então, tenha cuidado com este comando.

```sh
$ rm -r umapasta
```

Pronto! Para ter certeza que a pasta foi excluída, vamos checar:

```sh
$ ls
Dockerfile railsgirls
```

É possível observar que `umapasta` não existe mais. Estamos apenas com o Dockerfile e a pasta do projeto.

Por enquanto é isso!
