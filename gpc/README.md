# Assinatura de commits com gpg

- Primeiro precisamos instalar para tal utilize o seguinte comando para macos:

```shell
brew install gnupg gnupg2
```

- Para verificar se já existe alguma chave criada utilizamos o comando:

```shell
gpg --list-secret-keys --keyid-form LONG
```

- Caso retorno vazio significa que não temos.

- Nesse caso podemos iniciar o processo de criação:

```shell
gpg --full-generate-key
```

- E podemos escolher qual o tipo de chave a ser utilizada.

- Podemos escolher a padrão que seria a RSA

- O tamanho de 4096

- e escolher por quanto tempo essa chave será válida

- podemos colocar um ano!

- Verificar se está tudo ok e digitar O para continuar

- Gerar a senha e confirmar

- no final ele diz qual pasta que ficará salvo a chave!

- Em geral fica em: ~/.gnupg/

- Agora podemos executar esse comando para listar nossa chave criada:

```shell
gpg --list-secret-keys --keyid-form LONG
```

- apresentará algumas informações... uma delas é o sec que terá o rsa4096/ID_DA_CHAVE só copiara apenas o id que está após a barra "/"

- utilizar o comando para obter a public key:

```shell
gpg --armor --export ID_DA_CHAVE_AQUI
```

- Com isso irá mostrar a chave publica, devemos copiar o valor 
- acessar o github 
- ir em configurações > SSH e gpg keys adicionar uma nova GPG key colar a chave publica no campo indicado e adicionar!

- Toda vez que eu fizer algum commit, o git irá validar a chave publica com a privada e se bater siginfica que está tudo certo e que sou eu mesmo que está realizando o commit

---

- Precisamos fazer mais uma coisa antes de prosseguir, com o id da chave vamos configurar o nosso git config utilizando esse comando:

```shell
git config --global user.signigkey ID_DA_CHAVE
```

- No arquivo ~/.zshrc adicionar o seguinte:

```shell
export GPG_TTY=$(tty)
```

- Se eu desejar assinar o commit de um repositório especifico basta eu ir na pasta desse repositorio e no terminal executar o comando:

```shell
git config commit.gpgsign true
```

- Se eu desejar assinar de todos basta executar o comando:

```shell
git config --global commit.gpgsign true
```

- E para tags é o mesmo principio:

```shell
git config --global tag.gpgSign true
```

- Caso não deseje assinar todos os commits mas apenas alguns pode utilizar o -S ao realizar o commit:

```shell
git commit -S -m 'Msg'
```

- Para verificar se o commit foi assinado podemos utilizar o seguinte comando:

```shell
git log --show-signature -1
```

-----

## Linux/WSL2

- Fazer isso apenas se não funcionar logo de cara o armazenamento da senha.
- Caso a senha não seja armazenada e fique solicitando toda vez a cada commit pode realizar o seguinte:

- Editar o arquivo ~/.gnupg/gpg.conf

- Adicionar o seguinte:

```shell
use-agent
```

- E por fim executar o comando:

```shell
gpgconf --launch gpg-agent
```

- E o agente irá rodar!

- Dessa forma ele não irá ficar pedindo a senha toda hora!

