# Vetores em Programação

##  Motivação do Problema

Em programação, muitas vezes precisamos armazenar vários valores do mesmo tipo.  
Imagine um sistema que precise guardar as notas de 30 alunos. Criar uma variável para cada nota seria trabalhoso e pouco eficiente:

```c
float nota1, nota2, nota3, nota4...
```

Para resolver esse problema, utilizamos **vetores**.

Os vetores permitem armazenar vários dados em uma única estrutura, facilitando a organização, manipulação e processamento das informações.

---

# Conceito de Vetores

Um **vetor** é uma estrutura de dados que armazena vários elementos do mesmo tipo em posições contínuas de memória.

Cada elemento do vetor possui um índice, que representa sua posição.

### Características principais

- Armazena múltiplos valores
- Todos os elementos possuem o mesmo tipo
- O acesso é feito através de índices
- Os índices normalmente começam em `0`

---

#  Estrutura de um Vetor

## Declaração

Em linguagem C, a estrutura básica de um vetor é:

```c
tipo nome_do_vetor[tamanho];
```

## Exemplo

```c
#include <stdio.h>

int main(){

    int numeros[5];
    return 0;

}
```

Nesse exemplo:

- `int` → tipo dos elementos
- `numeros` → nome do vetor
- `[5]` → quantidade de posições

### Representação do vetor

| Índice | Valor |
|---|---|
| 0 | |
| 1 | |
| 2 | |
| 3 | |
| 4 | |

---

# Exemplo de Vetor

```c
#include <stdio.h>

int main() {

    int numeros[5] = {10, 20, 30, 40, 50};

    printf("Primeiro elemento: %d\n", numeros[0]);
    printf("Terceiro elemento: %d\n", numeros[2]);

    return 0;
}
```

## Saída

```txt
Primeiro elemento: 10
Terceiro elemento: 30
```

---

# Exercício

## Exercício 1

Faça um programa em C que:

1. Crie um vetor de 5 posições do tipo inteiro
2. Solicite ao usuário que digite os valores
3. Exiba todos os valores armazenados no vetor

### Exemplo de saída

```txt
Digite o valor da posição 0: 10
Digite o valor da posição 1: 20
Digite o valor da posição 2: 30
Digite o valor da posição 3: 40
Digite o valor da posição 4: 50

Valores armazenados:
10 20 30 40 50
```