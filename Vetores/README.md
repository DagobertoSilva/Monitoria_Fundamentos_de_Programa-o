# Vetores em Programação

##  Motivação do Problema

Em programação, muitas vezes precisamos armazenar vários valores do mesmo tipo.  
Imagine um sistema que precise guardar as notas de 30 alunos. Criar uma variável para cada nota seria trabalhoso e pouco eficiente:

```c
float nota1, nota2, nota3, nota4...
```

```c
#include <stdio.h>

int main(){
    float nota1, nota2, nota3, nota4,nota5, nota6, nota7, nota8, nota9, nota10;

    scanf("%f", &nota1);
    scanf("%f", &nota2);
    scanf("%f", &nota3);
    scanf("%f", &nota4);
    scanf("%f", &nota5);
    scanf("%f", &nota6);
    scanf("%f", &nota7);
    scanf("%f", &nota8);
    scanf("%f", &nota9);
    scanf("%f", &nota10);

    return 0;
}
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

⚠️ O último índice sempre será:

```c
tamanho - 1
```

---

#  Inicialização de Vetores

## Inicializando na declaração

```c
int numeros[5] = {10, 20, 30, 40, 50};
```

---

## Inicialização parcial

```c
int numeros[5] = {10, 20};
```

As posições restantes recebem `0`.

---

## Vetor sem tamanho definido

```c
int numeros[] = {1, 2, 3, 4};
```

O compilador calcula automaticamente o tamanho.

---

#  Acessando Elementos

## Sintaxe

```c
vetor[indice]
```

## Exemplo

```c
int numeros[5] = {10, 20};
printf("%d", numeros[0]);
```

Saída:

```txt
10
```

---

# Alterando Valores

Podemos modificar posições específicas.

## Exemplo

```c
int numeros[2] = {10, 20};
printf("%d\n", numeros[1]);
numeros[1] = 100;
printf("%d\n", numeros[1]);
```

---

#  Percorrendo Vetores

O mais comum é utilizar o `for`.

## Exemplo

```c
for(int i = 0; i < 5; i++) {

    printf("%d\n", numeros[i]);

}
```

---

#  Entrada de Dados em Vetores

## Exemplo

```c
for(int i = 0; i < 5; i++) {

    scanf("%d", &numeros[i]);

}
```

---

#  Saída de Dados

## Exemplo

```c
for(int i = 0; i < 5; i++) {

    printf("%d\n", numeros[i]);

}
```

---

# Memória no Vetor

Os elementos ficam armazenados em posições contínuas da memória.

## Exemplo

| Índice | Valor | Endereço |
|---|---|---|
| 0 | 10 | 1000 |
| 1 | 20 | 1004 |
| 2 | 30 | 1008 |

---

#  Tamanho do Vetor

## Obtendo o tamanho

```c
sizeof(vetor) / sizeof(vetor[0])
```

## Exemplo

```c
int tamanho = sizeof(numeros) / sizeof(numeros[0]);
```
Essa expressão é muito utilizada em C para descobrir quantos elementos existem em um vetor.

---

#  Entendendo o `sizeof`

O operador `sizeof` retorna a quantidade de bytes ocupada por algo na memória.

---

#  Exemplo

```c
int numeros[5];
```

Sabemos que:

- Um `int` normalmente ocupa `4 bytes`
- O vetor possui `5 elementos`

Logo:

```txt
5 × 4 = 20 bytes
```

Então:

```c
sizeof(numeros)
```

retorna:

```txt
20
```

---

#  Pegando o tamanho de um elemento

Agora observe:

```c
sizeof(numeros[0])
```

`numeros[0]` representa apenas um elemento do vetor.

Como ele é um `int`, normalmente ocupa:

```txt
4 bytes
```

---

#  Fazendo a divisão

Temos:

```c
sizeof(numeros) / sizeof(numeros[0])
```

Substituindo pelos valores:

```txt
20 / 4 = 5
```

Resultado:

```txt
5 elementos
```

---

---

#  Tipos de Vetores

## Vetor de inteiros

```c
int numeros[5];
```

---

## Vetor de float

```c
float notas[10];
```

---

## Vetor de char

```c
char letras[20];
```

---

#  Strings

Strings em C são vetores de caracteres.

## Exemplo

```c
char nome[20];
```

---

# Limitações dos Vetores

- Tamanho fixo
- Não podem armazenar tipos diferentes
- Não aumentam automaticamente
- Acesso inválido pode causar erros

---

#  Erro Comum — Acesso Fora do Vetor

## Exemplo incorreto

```c
numeros[5] = {10, 20, 30, 40, 50};
numeros[10] = 5;
```

Se o vetor possui apenas 5 posições, isso gera comportamento indefinido.

---

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

#  Resumo Geral

| Característica | Informação |
|---|---|
| Índice inicial | 0 |
| Tipo dos elementos | Iguais |
| Tamanho | Fixo |
| Acesso | Por índice |
| Estrutura mais usada | `for` |
| Memória | Contínua |

# Exercícios

## Exercícios 1

Faça um programa em C que:

1. Crie um vetor de 5 posições do tipo inteiro e Solicite ao usuário que digite os valores
2. Exiba todos os valores armazenados no vetor
3. Ler 10 números e mostrar todos
4. Calcular a média de um vetor
5. Encontrar o maior valor
6. Encontrar o menor valor
7. Somar todos os elementos
8. Contar números pares
9. Inverter os elementos do vetor
10. Buscar um valor dentro do vetor


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