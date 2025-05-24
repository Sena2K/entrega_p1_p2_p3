
---

## Índice

1. [Visão Geral](#visão-geral)  
2. [Estrutura do Projeto](#estrutura-do-projeto)  
3. [Como Compilar](#como-compilar)  
4. [Como Executar](#como-executar)  
5. [Funcionamento do Lexer](#funcionamento-do-lexer)  
6. [Suposições e Limitações](#suposições-e-limitações)  
7. [Propósito Educacional](#propósito-educacional)  
8. [Notas de Uso](#notas-de-uso)

---

## Visão Geral

Este projeto implementa um **analisador léxico (lexer)** para uma linguagem de programação criada para fins didáticos.  
O lexer percorre o arquivo-fonte, identifica **tokens** (palavras-chave, identificadores, números, operadores, símbolos, etc.) e imprime cada token no formato:

Tipo: <código>, Valor: <lexema>

---

## Estrutura do Projeto

| Arquivo        | Descrição                                                                                 |
| -------------- | ----------------------------------------------------------------------------------------- |
| `lexer.c`      | Implementação do lexer e função `main`.                                                   |
| `lexer.h`      | Enum `LexType`, struct `LexToken` e protótipos.                                           |
| `Makefile`     | Regras para compilar (`make`) e limpar (`make clean`).                                    |
| `teste.txt`    | Exemplo de código-fonte para teste (crie ou adapte o seu).                                |

---

## Como Compilar

Pré-requisitos: **GCC** e **make** em ambiente Unix-like.

```bash
# Dentro da pasta do projeto
make           # gera o executável ./lexer
```

Para remover objetos e o binário:

```bash
make clean
```

---

## Como Executar

```bash
./lexer teste.txt
```

Exemplo de saída:

```
Tipo: 1, Valor: PROGRAMA
Tipo: 28, Valor: \n
Tipo: 9, Valor: int
Tipo: 15, Valor: x
Tipo: 18, Valor: =
Tipo: 16, Valor: 42
Tipo: 0, Valor: <EOF>
```

**Erro de uso**  
Se nenhum arquivo for informado ou o arquivo não puder ser aberto, o programa exibe:

```
Uso: ./lexer <arquivo.txt>
```

---

## Funcionamento do Lexer

Ignora espaços/tabs.

Reconhece:

- **Palavras-chave:** `PROGRAMA`, `INICIO`, `FIM`, `SE`, `SENAO`, `ENQUANTO`, `FUNCAO`, `RES`, `int`, `float`, `char`, `void`.
- **Identificadores:** letras seguidas de letras/dígitos (e `_` se definido).
- **Números:** inteiros `42` ou ponto-flutuante `3.14`, suportando sinal e notação científica.
- **Operadores:** `+ - * / = == != < > <= >=`.
- **Símbolos:** `() { } , : " \n`.
- **EOF:** token especial de fim de arquivo.
- **LEX_UNKNOWN:** caractere inesperado.

---

## Suposições e Limitações

- **Validade:** espera código que siga a gramática; não faz verificação sintática completa.
- **Erros:** caracteres desconhecidos são marcados como `LEX_UNKNOWN`; sem mensagens detalhadas.
- **Modo de uso:** apenas via arquivo; não há entrada interativa.
- **Buffer:** cada lexema limitado a 128 caracteres.

---

## Propósito Educacional

O projeto demonstra a etapa de análise léxica em construção de compiladores.  
Serve de base para evoluir para parser, analisador semântico ou gerador de código.

---

## Notas de Uso

Crie um arquivo `teste.txt` com algo como:

```cpp
PROGRAMA "exemplo":
INICIO
int x = 10
SE (x > 5) {
float y = x * 2.5
}
RES = x
FIM
```

Ajuste `lexer.h/.c` para novas palavras-chave ou operadores, conforme sua evolução da linguagem.
