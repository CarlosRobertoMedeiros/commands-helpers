# 🖇️ Comandos LocalStack

## ✒️ Autores
A descrição das funcionalidades foi baseada no perfil de [Daniel-iel](https://github.com/Daniel-iel/LocalStack/blob/main/readme.md), responsável por esta fase do catálogo.

---

## ☁️ Simple Queue Service (SQS)

O primeiro passo ao trabalhar com o SQS é se familiarizar com a [documentação oficial](https://aws.amazon.com/pt/sqs/).

Ao interagir com o comando `aws sqs`, você terá acesso a diversas opções. Embora nem todas sejam utilizadas com frequência, é importante conhecê-las para explorar o potencial completo do serviço.

```shell
add-permission | change-message-visibility | create-queue | delete-message | delete-queue |
get-queue-attributes | list-queues | receive-message | send-message | set-queue-attributes
```

### 🧩 Criando Fila

Cria uma nova fila no Amazon Simple Queue Service (SQS).

```shell
# Fila standard
aws sqs create-queue <nome_da_fila> --endpoint-url http://localhost:4566 --profile <nome_do_profile>

# Fila FIFO
aws sqs create-queue <nome_da_fila>.fifo --endpoint-url http://localhost:4566 --profile <nome_do_profile> --attributes FifoQueue=true
```

> **Nota:** Para filas FIFO, o nome **deve** terminar com `.fifo` e é obrigatório adicionar o atributo `--attributes FifoQueue=true`.

### 🗑️ Deletando Fila

Remove uma fila específica no Amazon SQS.

```shell
aws sqs delete-queue --queue-url <url_da_fila> --endpoint-url http://localhost:4566 --profile <nome_do_profile>
```

### 📬 Enviando Mensagem

Envia uma mensagem para a fila no SQS.

```shell
aws sqs send-message --queue-url <url_da_fila> --message-body "<mensagem>" --endpoint-url http://localhost:4566 --profile <nome_do_profile>
```

> **Dica:** É possível adicionar atributos extras à mensagem usando:
> `--message-attributes '{"AttributeName":{"DataType":"String","StringValue":"AttributeValue"}}'`

---

## 🔔 Simple Notification Service (SNS)

Antes de utilizar o SNS, consulte a [documentação oficial](https://aws.amazon.com/pt/sns/).

```shell
create-topic | delete-topic | list-topics | publish | subscribe | unsubscribe
```

### 🧩 Criando Tópico

Cria um novo tópico SNS.

```shell
# Tópico standard
aws sns create-topic --name <nome_do_tópico> --endpoint-url http://localhost:4566 --profile <nome_do_profile>

# Tópico FIFO
aws sns create-topic --name <nome_do_tópico>.fifo --endpoint-url http://localhost:4566 --profile <nome_do_profile> --attributes FifoTopic=true
```

> **Nota:** Tópicos e filas devem ser do mesmo tipo: FIFO com FIFO e Standard com Standard.

### 🔗 Conectando Fila a um Tópico

Associa uma fila SQS a um tópico SNS.

```shell
aws sns subscribe --topic-arn <arn_do_tópico> --protocol sqs --notification-endpoint <arn_da_fila> --endpoint-url http://localhost:4566 --profile <nome_do_profile>
```

---

## 🪣 Simple Storage Service (S3)

Consulte a [documentação do S3](https://aws.amazon.com/pt/s3/) para conhecer suas funcionalidades.

### 📋 Listando Buckets

```shell
aws s3api list-buckets --endpoint-url http://localhost:4566 --profile <nome_do_profile>
```

### 🧱 Criando Bucket

```shell
aws s3api create-bucket --bucket <nome_do_bucket> --endpoint-url http://localhost:4566 --profile <nome_do_profile>
```

### 📤 Enviando Arquivo

```shell
aws s3api put-object --bucket <nome_do_bucket> --key <path_no_bucket> --body <arquivo_local> --endpoint-url http://localhost:4566 --profile <nome_do_profile>
```

---

## 🔑 Secrets Manager

Antes de usar o Secrets Manager, consulte a [documentação oficial](https://aws.amazon.com/pt/secrets-manager/).

### 🔒 Criando Secret

```shell
aws secretsmanager create-secret --name <nome_da_secret> --secret-string "<valor_do_segredo>" --endpoint-url http://localhost:4566 --profile <nome_do_profile>
```

### 📖 Listando Secrets

```shell
aws secretsmanager list-secrets --endpoint-url http://localhost:4566 --profile <nome_do_profile>
```

### 🧩 Consultando Valor da Secret

```shell
aws secretsmanager get-secret-value --secret-id <nome_da_secret> --endpoint-url http://localhost:4566 --profile <nome_do_profile>
```

---

## 🧑‍💻 Colaboração

Leia o arquivo [COLABORACAO.md](https://gist.github.com/usuario/linkParaInfoSobreContribuicoes) para saber mais sobre o código de conduta e o processo de contribuição.

## 🏷️ Versão

Usamos [SemVer](http://semver.org/) para controle de versão. Veja as [tags do projeto](https://github.com/suas/tags/do/projeto) para versões disponíveis.

## ✍️ Autor

**Carlos Roberto** – *Desenvolvimento e Documentação*

## 📜 Licença

Este projeto está sob a licença especificada em [LICENSE.md](https://github.com/usuario/projeto/licenca).

---

⌨️ Feito com ❤️ por [Carlos Roberto] 😊

