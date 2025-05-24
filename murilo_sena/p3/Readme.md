# p3

Este projeto é composto por dois arquivos principais em C:

- `bfc.c`: Compilador de expressões matemáticas simples para Brainfuck.
- `bfe.c`: Interpretador de Brainfuck.

> **Importante**: O compilador (`bfc.c`) **não executa divisões corretamente**. A lógica para divisão está presente no código, mas o resultado final gerado em Brainfuck **não representa uma divisão funcional ou precisa**.

## Como funciona

### `bfc.c`

O `bfc.c` recebe uma expressão no formato:

variavel = termo1 + termo2 - termo3 * termo4 ...


E gera um código Brainfuck correspondente, exibido na saída padrão. Cada termo pode ser:
- Um número inteiro
- Uma multiplicação (`a * b`)
- Uma divisão (`a / b`) – **não funcional!**

Exemplo:

```bash
echo "x = 5 + 3 * 2" | ./bfc


Gera o código Brainfuck correspondente à expressão.

bfe.c
O bfe.c interpreta o código Brainfuck gerado pelo bfc.c.

Exemplo de uso combinado:

```bash

echo "x = 5 + 3" | ./bfc | ./bfe

Observações
Suporta até 100 termos por expressão.

Cada termo pode conter multiplicações.

A divisão não funciona corretamente.

O nome da variável é apenas decorativo (não altera o resultado).
