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

# Percorrendo e Acessando Vetores em C

## Passo 1 — Entendendo o vetor

Observe o vetor abaixo:

```c
int numeros[5] = {10, 20, 30, 40, 50};
```

Esse vetor possui:

- Nome: `numeros`
- Tipo: `int`
- Quantidade de posições: `5`

---

# Passo 2 — Entendendo os índices

Cada posição do vetor possui um índice.

Os índices começam em `0`.

| Índice | Valor |
|---|---|
| 0 | 10 |
| 1 | 20 |
| 2 | 30 |
| 3 | 40 |
| 4 | 50 |

---

#  Passo 3 — Acessando posições específicas

Para acessar um elemento do vetor, utilizamos:

```c
nome_do_vetor[indice]
```

## Exemplo

```c
printf("%d", numeros[0]);
```

Saída:

```txt
10
```

Outro exemplo:

```c
printf("%d", numeros[2]);
```

Saída:

```txt
30
```

---

# Passo 4 — Código completo acessando posições

```c
#include <stdio.h>

int main() {

    int numeros[5] = {10, 20, 30, 40, 50};

    printf("Primeiro elemento: %d\n", numeros[0]);
    printf("Terceiro elemento: %d\n", numeros[2]);

    return 0;
}
```

---

# Passo 5 — Problema do acesso manual

Imagine um vetor com 100 posições.

Fazer isso manualmente seria inviável:

```c
printf("%d", numeros[0]);
printf("%d", numeros[1]);
printf("%d", numeros[2]);
printf("%d", numeros[3]);
...
```

Para resolver isso, utilizamos estruturas de repetição.

---

#  Passo 6 — Percorrendo o vetor com `for`

O laço `for` permite acessar todas as posições automaticamente.

## Estrutura

```c
for(inicialização; condição; incremento) {

}
```

---

#  Passo 7 — Percorrendo todas as posições

```c
#include <stdio.h>

int main() {

    int numeros[5] = {10, 20, 30, 40, 50};

    for(int i = 0; i < 5; i++) {

        printf("%d\n", numeros[i]);

    }

    return 0;
}
```

---

# Passo 8 — Entendendo o `for`

## Inicialização

```c
int i = 0;
```

O índice começa na posição `0`.

---

## Condição

```c
i < 5
```

O laço continuará enquanto `i` for menor que `5`.

---

## Incremento

```c
i++
```

A cada repetição, o índice aumenta em `1`.

---

# Passo 9 — Como o vetor é percorrido

| Valor de `i` | Posição acessada | Valor |
|---|---|---|
| 0 | numeros[0] | 10 |
| 1 | numeros[1] | 20 |
| 2 | numeros[2] | 30 |
| 3 | numeros[3] | 40 |
| 4 | numeros[4] | 50 |

---

# Passo 10 — Saída do programa

```txt
10
20
30
40
50
```

---

#  Resumo

## Para acessar uma posição específica

```c
numeros[indice]
```

## Para percorrer todo o vetor

Utilizamos um `for`.

```c
for(int i = 0; i < tamanho; i++)
```

O índice `i` percorre todas as posições do vetor.

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