# Stash

- Para verificar o que tem no stash

Executar o comando:

```shell
git stash list
```

- Caso não tenha nada salvo ele não irá exibir nada

- Um cenário para utilizar o stash:
- Estamos em uma dada branch, 
- E precisamos parar o que estavamos fazendo e mudar para outra feature ou branch,
- podemos utilizar então o stash o qual irá armazenar localmente as alterações, e voltar a branch para o estado anterior, ou seja não irá levar os arquivos e/ou alterações juntos para nova branch

- Para tal executamos o comando:

```shell
git add .
```

```shell
git stash
```

- E quando voltarmos para o trabalho novamente podemos utilizar o comando list novamente para listar os stashs feitos

```shell
git stash list
```

- caso só tenhamos apenas 1 só utilizar o comando:

```shell
git stash apply
```

- ou se tivermos mais de um podemos escolher passando esse valor após o apply:

```shell
git stash apply stash@{NUMBER_HERE}
```

- Poderiamos utilizar o commit normal? Sim
- Porém dessa forma se não temos nenhum commit marco interessante para fazer podemos utilizar o stash, o ideal é não utilizar o commit como ctrl + S, para tal utilizar o stash, e deixar para o commit o que de fato for um marco na história do nosso código!