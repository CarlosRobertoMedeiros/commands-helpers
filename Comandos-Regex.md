# COMANDOS Regex - Expressoes Regulares📣

## PESQUISAS NO TERMINAL LINUX - GREP - GLOBAL REGULAR EXPRESSION PRINT

```bash
# Alvo (Target) -> Regex Engine (Java, C#, Js,PHP, C, Pyton-- "Flavors") <- Pattern (regex)
#                               |
#                       Resultado (Match)

man grep # Apresenta a documentacao no manual
grep 'padrao_regex' caminho_do_arquivo.txt
grep Anna <path>/arquivo.csv  # Pesquisa dentro do arquivo.csv a linha que contem o nome Anna
grep -n Anna <path>/arquivo.csv  # Pesquisa dentro do arquivo.csv a linha que contem o nome Anna e retorna tbm o numero da linha

sed 's/padrao_regex/novo_texto/g' caminho_do_arquivo.txt
sed 's/azul/vermelho/' caminho_do_arquivo.txt # Substitui todas as palavras azul por vermelho no caminho indicado

awk '/UP/ {print $1}' servidores.txt # /UP/: Filtra as linhas que contem a palavra UP (o padrao regex). {print $1}: Exibe apenas a primeira coluna de cada linha que corresponde ao filtro.
```



## PESQUISAS USANDO JS
```bash
const fs = require('fs')
const bancoCsv = 'database.csv'
const banco = fs.readFileSync(bancoCsv,"utf-8")

# Busca por nome Anna
const regex = /Anna/

const matchRegex = banco.match(regex)
console.log(matchRegex)


# Busca por telefone
#Exemplos (99) 99999-9999 ola (99) 9999-9999
const valores = "(99) 99999-9999 ola (99) 9999-9999"
const regexTelefone = /\(\d{2}\)\s\d{4,5}-\d{4}/g

const matchRegexTelefone = valores.match(regexTelefone)
console.log(matchRegexTelefone)


# Busca por cpf
const valoresCpf = "999.999.999-99 ola (99) 88888888888"
const regexCpf = /\d{3}[.-]?\d{3}[.-]?\d{3}[.-]?\d{2}/g

const matchRegexCpf = valoresCpf.match(regexCpf)
console.log(matchRegexCpf)

# Busca por Data de Nascimento
const valoresDtNasc = "12/12/2000 ola (99) 12.12.2000"
const regexDtNasc = /(\d{2}\/\d{2}\/\d{4}|\d{2}\/\d{2}\/\d{4})/g;

const matchRegexDtNasc = valoresDtNasc.match(regexDtNasc)
console.log(matchRegexDtNasc)

# Usando classes com busca de caracteres para dois nomes
# Procura todas as letras e as acentuadas tambem
const valoresNomes = "Data de Carlos Roberto Bezerra Filho 112 21 Antonio Nunes"
const patternNomes = /[A-Za-zÀ-ÿ]+\s[A-Za-zÀ-ÿ]+/g

const matchRegexNomes = valoresNomes.match(patternNomes)
console.log(matchRegexNomes)


# Criando grupos de captura
const valoresNomes = "Data de, Carlos Roberto, \n Bezerra Filho, 112 21 \n Antonio Nunes"
const patternNomes = /^([A-Za-zÀ-ÿ]+)(\s[A-Za-zÀ-ÿ])+/gm

const matchRegexNomes = valoresNomes.match(patternNomes)
console.log(matchRegexNomes)
```




