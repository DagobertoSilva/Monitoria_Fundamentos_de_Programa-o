# Vetores em Funções e Vetores Dinâmicos em C

# Motivação do Problema

Até agora aprendemos vetores de tamanho fixo.

Exemplo:

```c
int numeros[5];
```

Isso funciona bem quando sabemos antecipadamente quantos elementos serão armazenados.

Mas imagine um sistema onde:

- o usuário pode cadastrar quantos alunos quiser;
- o número de notas pode variar;
- um arquivo possui tamanho desconhecido;
- um sistema precise crescer dinamicamente.

Além disso, imagine que queremos reutilizar código.

Observe:

```c
#include <stdio.h>

int main() {

    int numeros[5];

    for(int i = 0; i < 5; i++) {
        scanf("%d", &numeros[i]);
    }

    for(int i = 0; i < 5; i++) {
        printf("%d\n", numeros[i]);
    }

    return 0;
}
```

Agora imagine repetir essa lógica várias vezes.

Isso deixaria o código:

- repetitivo;
- difícil de manter;
- menos organizado.

Para resolver esse problema, usamos:

1. **Vetores em funções**
2. **Vetores dinâmicos (alocação dinâmica com ponteiros)**

imagine receber oo pedido para criar 3 vetores preencher e mostrar os valores todos

```c
#include <stdio.h>

int main() {

    int vetor1[5];
    int vetor2[5];
    int vetor3[5];
//RECEBENDO VETORES------------------------------------------
    for(int i = 0; i < 5; i++) {
        scanf("%d", &vetor1[i]);
    }

    for(int i = 0; i < 5; i++) {
        scanf("%d", &vetor2[i]);
    }
    
    for(int i = 0; i < 5; i++) {
        scanf("%d", &vetor3[i]);
    }
//--------------------------------------------
    printf("\n\n");
//IMPRIMINDO VETORES------------------------------------------
    for(int i = 0; i < 5; i++) {
        printf("Numeros[%d]: %d\n\n", i, vetor1[i]);
    }
    printf("\n\n");

    for(int i = 0; i < 5; i++) {
        printf("Numeros[%d]: %d\n", i, vetor2[i]);
    }
printf("\n\n");

    for(int i = 0; i < 5; i++) {
        printf("Numeros[%d]: %d\n", i, vetor3[i]);
    }
//----------------------------------------------------
    return 0;
}
```

*BEM CANSATIVO NÃO?!*
---

# Revisão Rápida — Vetores

Antes de avançar, vamos lembrar o conceito básico.

Um vetor é uma estrutura de dados que armazena:

- vários elementos;
- do mesmo tipo;
- em posições contínuas da memória.

Exemplo:

```c
int numeros[5] = {10, 20, 30, 40, 50};
```

Representação:

| Índice | Valor |
|---|---:|
| 0 | 10 |
| 1 | 20 |
| 2 | 30 |
| 3 | 40 |
| 4 | 50 |

Lembre-se:

```txt
índice inicial = 0
último índice = tamanho - 1
```

---

# Vetores em Funções

## Motivação

Imagine um programa que precise imprimir vários vetores.

Sem função:

```c
for(int i = 0; i < 5; i++) {
    printf("%d ", numeros[i]);
}
```

Depois novamente:

```c
for(int i = 0; i < 5; i++) {
    printf("%d ", outroVetor[i]);
}
```

Estamos repetindo código.

Uma solução melhor é criar uma função.

---

# Criando uma Função para Mostrar um Vetor

## Exemplo

```c
#include <stdio.h>

void mostrarVetor(int vetor[5]) {

    for(int i = 0; i < 5; i++) {
        printf("%d ", vetor[i]);
    }

}

int main() {

    int numeros[5] = {10, 20, 30, 40, 50};

    mostrarVetor(numeros);

    return 0;
}
```

---

# Entendendo o Código

Observe:

```c
void mostrarVetor(int vetor[5])
```

Temos:

- `void` → não retorna valor;
- `mostrarVetor` → nome da função;
- `int vetor[5]` → vetor recebido como parâmetro.

---

# O Que Acontece na Memória?

Quando fazemos:

```c
mostrarVetor(numeros);
```

O vetor é passado para a função.

Mas existe um detalhe muito importante.

O vetor **não é copiado completamente**.

Na prática, a função recebe um endereço de memória.

Ou seja:

```txt
numeros
```

equivale aproximadamente a:

```txt
&numeros[0]
```

Vamos supor:

| Índice | Valor | Endereço |
|---|---:|---:|
| 0 | 10 | 1000 |
| 1 | 20 | 1004 |
| 2 | 30 | 1008 |
| 3 | 40 | 1012 |
| 4 | 50 | 1016 |

Quando fazemos:

```c
mostrarVetor(numeros);
```

O endereço enviado é:

```txt
1000
```

Ou seja, o endereço do primeiro elemento.

---

# Vetor em Função é Ponteiro

Essa é uma das coisas mais importantes de C.

Observe:

Estas duas funções são equivalentes:

```c
void mostrar(int vetor[5])
```

e

```c
void mostrar(int *vetor)
```

Ambas funcionam da mesma maneira.

Isso acontece porque:

```txt
vetor → endereço do primeiro elemento
```

---

# Exemplo com Ponteiro

```c
#include <stdio.h>

void mostrar(int *vetor) {

    for(int i = 0; i < 5; i++) {
        printf("%d\n", vetor[i]);
    }

}

int main() {

    int numeros[5] = {10, 20, 30, 40, 50};

    mostrar(numeros);

    return 0;
}
```

Resultado:

```txt
10
20
30
40
50
```

---

# Alterando um Vetor Dentro da Função

Como a função recebe um endereço de memória, conseguimos modificar o vetor original.

## Exemplo

```c
#include <stdio.h>

void alterar(int vetor[]) {

    vetor[0] = 999;

}

int main() {

    int numeros[5] = {10, 20, 30};

    alterar(numeros);

    printf("%d", numeros[0]);

    return 0;
}
```

Saída:

```txt
999
```

---

# Por Que Isso Acontece?

Porque a função está acessando a mesma região de memória.

Representação:

Antes:

| Índice | Valor |
|---|---:|
| 0 | 10 |
| 1 | 20 |
| 2 | 30 |

Depois da função:

| Índice | Valor |
|---|---:|
| 0 | 999 |
| 1 | 20 |
| 2 | 30 |

---

# Problema do Tamanho do Vetor

Observe:

```c
void mostrar(int vetor[])
```

Como descobrir quantos elementos existem?

Muitos iniciantes tentam:

```c
sizeof(vetor)
```

Mas isso está errado.

Dentro da função:

```c
vetor
```

vira um ponteiro.

Então:

```c
sizeof(vetor)
```

retorna o tamanho do ponteiro.

Não o tamanho do vetor.

---

# Forma Correta

Passar o tamanho como parâmetro.

```c
void mostrar(int vetor[], int tamanho)
```

Exemplo:

```c
#include <stdio.h>

void mostrar(int vetor[], int tamanho) {

    for(int i = 0; i < tamanho; i++) {
        printf("%d ", vetor[i]);
    }

}

int main() {

    int numeros[] = {10,20,30,40,50};

    int tamanho =
        sizeof(numeros) /
        sizeof(numeros[0]);

    mostrar(numeros, tamanho);

    return 0;
}
```

---

# Exercício Mental

Observe:

```c
int numeros[5];
```

No `main`:

```c
sizeof(numeros)
```

resultado:

```txt
20
```

Dentro da função:

```c
sizeof(vetor)
```

resultado comum:

```txt
8
```

(ou 4 em alguns sistemas)

Porque agora é um ponteiro.

---

# Função para Somar Vetor

```c
#include <stdio.h>

int soma(int vetor[], int tamanho) {

    int soma = 0;

    for(int i = 0; i < tamanho; i++) {
        soma += vetor[i];
    }

    return soma;
}

int main() {

    int numeros[] = {10,20,30};

    int tamanho =
        sizeof(numeros)
        / sizeof(numeros[0]);

    printf("%d",
           soma(numeros, tamanho));

    return 0;
}
```

Saída:

```txt
60
```

# Funções com Vetores, Ponteiros e Alocação Dinâmica de Memória em C

# Motivação do Problema

Até agora aprendemos vetores comuns.

Exemplo:

```c
int numeros[5] = {10, 20, 30, 40, 50};
```

Também aprendemos que funções ajudam a evitar repetição de código.

Mas surge uma dúvida muito importante:

```txt
Como passar vetores para funções?
```

Além disso:

```txt
Como criar vetores cujo tamanho é definido pelo usuário?
```

Imagine um sistema de notas.

O usuário pode cadastrar:

- 10 alunos;
- 100 alunos;
- 1000 alunos.

Não faz sentido escrever:

```c
int notas[1000];
```

se nem sabemos quantos dados existirão.

A solução envolve dois conceitos extremamente importantes:

1. Vetores passados para funções com ponteiros
2. Alocação dinâmica de memória

---

# Revisando Vetores

Exemplo:

```c
int numeros[5] = {10,20,30,40,50};
```

Representação:

| Índice | Valor |
|---|---:|
| 0 | 10 |
| 1 | 20 |
| 2 | 30 |
| 3 | 40 |
| 4 | 50 |

Na memória (exemplo):

| Índice | Valor | Endereço |
|---|---:|---:|
| 0 | 10 | 1000 |
| 1 | 20 | 1004 |
| 2 | 30 | 1008 |
| 3 | 40 | 1012 |
| 4 | 50 | 1016 |

Observe algo importante:

Os elementos ficam em posições contínuas da memória.

---

# Vetor e Ponteiro

Em C, o nome do vetor representa o endereço do primeiro elemento.

Ou seja:

```c
numeros
```

equivale aproximadamente a:

```c
&numeros[0]
```

Exemplo:

```c
printf("%p\n", numeros);
printf("%p\n", &numeros[0]);
```

Saída:

```txt
0x1000
0x1000
```

Mesmo endereço.

---

# Passando Vetores para Funções

Observe:

```c
void mostrar(int vetor[]) {

}
```

ou

```c
void mostrar(int *vetor) {

}
```

As duas formas funcionam.

Porque:

```txt
vetor → endereço do primeiro elemento
```

Na prática:

```txt
vetor[] = ponteiro
```

---

# Exemplo 1 — Mostrando um Vetor

```c
#include <stdio.h>

void mostrar(int vetor[], int tamanho) {

    for(int i = 0; i < tamanho; i++) {

        printf("%d ", vetor[i]);

    }

}

int main() {

    int numeros[] = {10,20,30,40,50};

    int tamanho =
        sizeof(numeros)
        / sizeof(numeros[0]);

    mostrar(numeros, tamanho);

    return 0;
}
```

Saída:

```txt
10 20 30 40 50
```

---

# Entendendo a Função

Observe:

```c
mostrar(numeros, tamanho);
```

O que está sendo enviado?

Na prática:

```txt
endereço do primeiro elemento
```

Representação:

```txt
numeros → 1000
```

A função recebe:

```c
int vetor[]
```

ou

```c
int *vetor
```

Então:

```txt
vetor = 1000
```

Agora ela consegue acessar:

```c
vetor[0]
vetor[1]
vetor[2]
```

---

# Vetor Passado por Ponteiro

Observe:

```c
void mostrar(int *vetor, int tamanho)
```

Código completo:

```c
#include <stdio.h>

void mostrar(int *vetor, int tamanho) {

    for(int i = 0; i < tamanho; i++) {

        printf("%d ", vetor[i]);

    }

}

int main() {

    int numeros[] = {10,20,30,40,50};

    mostrar(numeros, 5);

    return 0;
}
```

Resultado:

```txt
10 20 30 40 50
```

---

# Alterando Vetor Dentro da Função

Como a função recebe um endereço, conseguimos modificar o vetor original.

Exemplo:

```c
#include <stdio.h>

void dobrar(int *vetor, int tamanho) {

    for(int i = 0; i < tamanho; i++) {

        vetor[i] *= 2;

    }

}

int main() {

    int numeros[] = {10,20,30};

    dobrar(numeros, 3);

    for(int i = 0; i < 3; i++) {

        printf("%d ", numeros[i]);

    }

    return 0;
}
```

Saída:

```txt
20 40 60
```

---

# O Problema do `sizeof`

Muitos iniciantes fazem isto:

```c
void mostrar(int vetor[]) {

    int tamanho =
        sizeof(vetor)/ sizeof(vetor[0]);

}
```

Errado.

---

# Por Que Está Errado?

Dentro da função:

```txt
vetor vira ponteiro
```

Então:

```c
sizeof(vetor)
```

retorna:

```txt
tamanho do ponteiro
```

Não o tamanho real do vetor.

---

# Forma Correta

Sempre passar o tamanho.

```c
void mostrar(int vetor[], int tamanho)
```

Exemplo:

```c
mostrar(numeros, tamanho);
```

---

# Aritmética de Ponteiros

Como vetor é ponteiro:

```c
vetor[i]
```

equivale a:

```c
*(vetor + i)
```

Exemplo:

```c
#include <stdio.h>

int main() {

    int numeros[] = {10,20,30};

    printf("%d\n", numeros[1]);

    printf("%d\n", *(numeros + 1));

    return 0;
}
```

Saída:

```txt
20
20
```

---

