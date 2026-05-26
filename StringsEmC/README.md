# Strings em C

## Motivação do Problema

Em muitos programas precisamos trabalhar com textos, como:

- Nome de usuários
- Mensagens
- Senhas
- Frases
- Endereços

Na linguagem C, não existe um tipo específico chamado `string` como em outras linguagens.

Para armazenar textos, utilizamos **vetores de caracteres**.

---

# Conceito de Strings

Uma **string** em C é um vetor do tipo `char`.

Cada posição do vetor armazena um caractere.

## Exemplo

```c
char nome[20];
```

Nesse exemplo:

- `char` → tipo dos elementos
- `nome` → nome da string
- `[20]` → quantidade máxima de caracteres

---

# Como as Strings Funcionam

Uma string é formada por caracteres armazenados sequencialmente na memória.

O final da string é marcado automaticamente pelo caractere especial:

```c
'\0'
```

Esse caractere é chamado de:

- caractere nulo
- terminador de string

---

# Representação da String

## Exemplo

```c
char nome[] = "Ana";
```

Na memória:

| Índice | Valor |
|---|---|
| 0 | 'A' |
| 1 | 'n' |
| 2 | 'a' |
| 3 | '\0' |

⚠️ O `'\0'` é obrigatório para indicar o final da string.

---

# Declarando Strings

## Forma 1 — Vetor de caracteres

```c
char nome[20];
```

---

## Forma 2 — Inicializando diretamente

```c
char nome[] = "Carlos";
```

---

# Lendo Strings

## Utilizando `scanf`

```c
scanf("%s", nome);
```

## Exemplo

```c
#include <stdio.h>

int main() {

    char nome[20];

    printf("Digite seu nome: ");
    scanf("%s", nome);

    printf("Nome digitado: %s\n", nome);

    return 0;
}
```

---

# Problema do `scanf`

O `scanf("%s")` lê apenas até o primeiro espaço.

## Exemplo

Entrada:

```txt
João Silva
```

Saída armazenada:

```txt
João
```

---

# Utilizando `fgets`

Para ler frases completas utilizamos:

```c
fgets()
```

---

# Exemplo

```c
#include <stdio.h>

int main() {

    char nome[50];

    printf("Digite seu nome completo: ");

    fgets(nome, 50, stdin);

    printf("Nome: %s", nome);

    return 0;
}
```

---

# Acessando Caracteres

Como strings são vetores, podemos acessar posições usando índices.

## Exemplo

```c
char nome[] = "Maria";

printf("%c\n", nome[0]);
printf("%c\n", nome[1]);
```

## Saída

```txt
M
a
```

---

# Alterando Caracteres

## Exemplo

```c
char nome[] = "Maria";

nome[0] = 'P';

printf("%s", nome);
```

## Saída

```txt
Paria
```

---

# Percorrendo uma String

Podemos utilizar `for`.

## Exemplo

```c
#include <stdio.h>

int main() {

    char nome[] = "Carlos";

    for(int i = 0; nome[i] != '\0'; i++) {

        printf("%c\n", nome[i]);

    }

    return 0;
}
```

---

# Entendendo o `'\0'`

O laço continua até encontrar:

```c
'\0'
```

Isso indica o final da string.

---

# Funções para Strings

Para utilizar funções de strings:

```c
#include <string.h>
```

---

# Função `strlen`

Retorna o tamanho da string.

## Exemplo

```c
#include <stdio.h>
#include <string.h>

int main() {

    char nome[] = "Carlos";

    printf("%lu", strlen(nome));

    return 0;
}
```

## Saída

```txt
6
```

⚠️ O `'\0'` não entra na contagem.

---

# Função `strcpy`

Copia uma string para outra.

## Exemplo

```c
#include <stdio.h>
#include <string.h>

int main() {

    char origem[] = "Olá";
    char destino[20];

    strcpy(destino, origem);

    printf("%s", destino);

    return 0;
}
```

---

# Função `strcat`

Concatena strings.

## Exemplo

```c
#include <stdio.h>
#include <string.h>

int main() {

    char nome[30] = "João ";
    char sobrenome[] = "Silva";

    strcat(nome, sobrenome);

    printf("%s", nome);

    return 0;
}
```

## Saída

```txt
João Silva
```

---

# Função `strcmp`

Compara duas strings.

## Exemplo

```c
#include <stdio.h>
#include <string.h>

int main() {

    char a[] = "abc";
    char b[] = "abc";

    printf("%d", strcmp(a, b));

    return 0;
}
```

## Resultado

```txt
0
```

Quando o resultado é:

- `0` → strings iguais
- diferente de `0` → strings diferentes

---

# Memória nas Strings

Cada caractere ocupa normalmente:

```txt
1 byte
```

## Exemplo

```c
char nome[] = "Ana";
```

Na memória:

| Índice | Valor | Endereço |
|---|---|---|
| 0 | 'A' | 1000 |
| 1 | 'n' | 1001 |
| 2 | 'a' | 1002 |
| 3 | '\0' | 1003 |

---

# Limitações das Strings

- Tamanho fixo
- Pode ocorrer overflow
- Necessário controlar o `'\0'`
- Funções exigem cuidado

---

# Erro Comum — Overflow

## Exemplo incorreto

```c
char nome[5];

scanf("%s", nome);
```

Se o usuário digitar:

```txt
Dagoberto
```

O vetor não terá espaço suficiente.

Isso pode causar:

- comportamento indefinido
- travamentos
- corrupção de memória

---

# Exemplo Completo

```c
#include <stdio.h>
#include <string.h>

int main() {

    char nome[50];

    printf("Digite seu nome: ");

    fgets(nome, 50, stdin);

    printf("Nome digitado: %s", nome);

    printf("Quantidade de caracteres: %lu\n", strlen(nome));

    return 0;
}
```

---

# Resumo Geral

| Característica | Informação |
|---|---|
| Tipo utilizado | `char` |
| Estrutura | Vetor |
| Final da string | `'\0'` |
| Índice inicial | 0 |
| Entrada simples | `scanf` |
| Entrada completa | `fgets` |
| Biblioteca | `string.h` |

---

# Exercícios

## Exercício 1

Faça um programa que leia um nome e exiba na tela.

---

## Exercício 2

Leia uma frase completa utilizando `fgets`.

---

## Exercício 3

Mostre cada caractere da string em uma linha diferente.

---

## Exercício 4

Conte quantos caracteres existem em uma string.

---

## Exercício 5

Leia dois nomes e compare utilizando `strcmp`.

---

## Exercício 6

Concatene nome e sobrenome utilizando `strcat`.

---

## Exercício 7

Faça um programa que substitua a primeira letra de uma string.

---

## Exercício 8

Conte quantas vogais existem em uma string.

---

## Exercício 9

Inverta uma string.

---

## Exercício 10

Verifique se uma palavra é palíndromo.