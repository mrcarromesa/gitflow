# Rebase

- Obter logs:

```shell
git log --oneline
```

---

- Remover um arquivo do Staging area:

```shell
git reset PATH_FILE
```

ou para todos

```shell
git reset HEAD -- .
```

- Realizar o rebase:

Utilizando o comando de log:

```shell
git log --oneline
```

vamos obter os commits

devemos contar quantos queremos unir:

![varios commits](./images/varios_commits.png)

e unir de forma interativa com o seguinte comando:

```shell
git rebase -i HEAD~Quantidade de commits
```

```shell
git rebase -i HEAD~3
```

Ou se for para voltar até o primeiro commit só executar o comando:

```shell
git rebase -i --root
```

podemos utilizar os comandos p e s

![varios commits](./images/comandos.png)

onde p é o commit que queremos preservar e o s é os que queremos espremer

porfim resultando em um único commit:

![varios commits](./images/resultado.png)