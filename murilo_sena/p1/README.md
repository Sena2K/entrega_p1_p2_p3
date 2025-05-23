Trabalho - Compilador e Máquina Virtual Neander

Autor: Murilo dos Santos Sena

Descrição

Este projeto consiste em um compilador, um assembler e um executor (simulador) para a linguagem fictícia .lpn, gerando código assembly intermediário e executável binário para uma arquitetura simplificada baseada no Neander.

Estrutura do Projeto

compilador.c: Lê um arquivo .lpn, faz análise léxica e sintática, gera uma Árvore Sintática Abstrata (AST) e produz um arquivo .asm (assembly Neander).

assembler.c: Converte o arquivo .asm para um binário .bin, traduzindo cada instrução e simbolizando os nomes.

executor.c: Simula a execução do binário na arquitetura Neander, mostrando a memória e resultado final.

Compilação

Para compilar todos os componentes do projeto, basta executar:

make

Execução

1. Compilar o programa .lpn

./compilador programa.lpn

Isso gera o programa.asm.

2. Montar o arquivo .asm com o assembler

./assembler programa.asm programa.bin

3. Executar o binário gerado

./executor

O executor imprime a memória antes e depois da execução, e exibe o valor final armazenado em RES.

Exemplo de programa.lpn

PROGRAMA "ExprMult":
INICIO
  a = 2
  b = 2
  c = 4
  RES = a + b * c
FIM

Resultado esperado: 2 + 2*4 = 10

O compilador é simples e não implementa tratamento de erros avançado.

Multiplicações e divisões com variáveis dependem do valor estar definido em tempo de compilação.

Divisão por zero não é permitida e é tratada com uma mensagem de erro.

Labels são resolvidos apenas com base na primeira passagem (sem suporte a forward references complexas).

A memória é limitada a 512 bytes, o que restringe a complexidade do programa.

Overflow de Memória: Certifique-se de que programas com muitas variáveis ou instruções não excedam MEMORYSIZE (516 bytes).

O compilador não suporta operações diretamente com números (como RES = 5 * 5). Para realizar operações com constantes, você deve atribuí-las previamente a variáveis, como:

A = 5
B = 5
RES = A * B

Operações com números negativos ainda não são totalmente suportadas em todos os contextos. Isso pode resultar em comportamento indefinido ou erros.

Observação Final

Este trabalho demonstra o entendimento dos principais estágios de um compilador (lex, parse, geração de código intermediário), integração com montagem binária e execução em arquitetura simplificada, aplicando os conhecimentos em sistemas, C e organização de computadores.

