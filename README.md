 Versão em português
---
 FIRMINO GUERRA
---

# Get Next Line

Ler uma linha de um descritor de arquivo é bastante tedioso.

## Sumário

1. [Objetivos](#objetivos)
2. [Instruções Comuns](#instruções-comuns)
3. [Parte Obrigatória](#parte-obrigatória)
4. [Parte Bônus](#parte-bônus)
5. [Envio e Avaliação por Pares](#envio-e-avaliação-por-pares)

---

## Objetivos

Este projeto não só permitirá que você adicione uma função muito conveniente à sua coleção, mas também o ajudará a aprender um conceito altamente interessante na programação em C: variáveis estáticas.

---

## Instruções Comuns

- Seu projeto deve ser escrito em C.
- Seu projeto deve estar em conformidade com a Norm. Se você tiver arquivos/funções bônus, eles estão incluídos na verificação de normas e você receberá 0 se houver um erro de norma.
- Suas funções não devem terminar inesperadamente (erro de segmentação, erro de barramento, liberação dupla, etc.), além de comportamentos indefinidos. Se isso acontecer, seu projeto será considerado não funcional e receberá 0 durante a avaliação.
- Toda a memória alocada na heap deve ser liberada adequadamente quando necessário. Vazamentos não serão tolerados.
- Se o enunciado exigir, você deve submeter um Makefile que compile seus arquivos de origem para a saída requerida com as flags -Wall, -Wextra e -Werror, use cc, e seu Makefile não deve relinkar.
- Seu Makefile deve conter pelo menos as regras `$(NAME)`, `all`, `clean`, `fclean` e `re`.
- Para entregar bônus ao seu projeto, você deve incluir uma regra `bonus` no seu Makefile, que adicionará todos os vários cabeçalhos, bibliotecas ou funções que são proibidos na parte principal do projeto. Os bônus devem estar em um arquivo separado `_bonus.{c/h}` se o enunciado não especificar outra coisa. A avaliação da parte obrigatória e bônus é feita separadamente.
- Se seu projeto permitir o uso da sua libft, você deve copiar suas fontes e o Makefile associado para uma pasta `libft` com o Makefile associado. O Makefile do seu projeto deve compilar a biblioteca usando seu Makefile, e depois compilar o projeto.
- Encorajamos você a criar programas de teste para seu projeto, mesmo que esse trabalho não precise ser enviado e não será avaliado. Isso lhe dará a chance de testar facilmente seu trabalho e o trabalho dos seus colegas. Esses testes serão especialmente úteis durante sua defesa. De fato, durante a defesa, você está livre para usar seus testes e/ou os testes do colega que está avaliando.
- Envie seu trabalho para o repositório git atribuído. Somente o trabalho no repositório git será avaliado. Se Deepthought for atribuído para avaliar seu trabalho, isso será feito após suas avaliações por pares. Se ocorrer um erro em qualquer seção do seu trabalho durante a avaliação do Deepthought, a avaliação será interrompida.

---

## Parte Obrigatória

### Nome da Função
`get_next_line`

### Protótipo
`char *get_next_line(int fd);`

### Arquivos a Serem Entregues
- `get_next_line.c`
- `get_next_line_utils.c`
- `get_next_line.h`

### Parâmetros
- `fd`: O descritor de arquivo a ser lido.

### Valor de Retorno
- Linha Lida: comportamento correto.
- `NULL`: Não há mais nada para ler ou ocorreu um erro.

### Funções Externas
- `read`
- `malloc`
- `free`

### Descrição
Escreva uma função que retorne uma linha lida de um descritor de arquivo:
- Chamadas repetidas (por exemplo, usando um loop) para sua função `get_next_line()` devem permitir que você leia o arquivo apontado pelo descritor de arquivo, uma linha de cada vez.
- Sua função deve retornar a linha que foi lida.
- Se não houver mais nada para ler ou se ocorreu um erro, ela deve retornar `NULL`.
- Certifique-se de que sua função funcione como esperado tanto ao ler um arquivo quanto ao ler da entrada padrão.
- Note que a linha retornada deve incluir o caractere de terminação `\n`, exceto se o fim do arquivo for alcançado e não terminar com um caractere `\n`.
- Seu arquivo de cabeçalho `get_next_line.h` deve conter pelo menos o protótipo da função `get_next_line()`.
- Adicione todas as funções auxiliares que precisar no arquivo `get_next_line_utils.c`. Um bom ponto de partida seria entender o que é uma variável estática.

### Opções de Compilação
- Você precisará definir o tamanho do buffer para a função `read()` com a opção `-D BUFFER_SIZE=n`.
- O valor do tamanho do buffer será modificado pelos avaliadores e pela Moulinette para testar seu código.
- Devemos ser capazes de compilar este projeto com e sem a flag `-D BUFFER_SIZE` além das flags usuais. Você pode escolher o valor padrão de sua escolha.
- Você deve compilar seu código da seguinte forma (usando um tamanho de buffer de 42 como exemplo):
  ```bash
  cc -Wall -Wextra -Werror -D BUFFER_SIZE=42 <arquivos>.c
  ```

### Comportamento Indefinido
- Consideramos que `get_next_line()` tem um comportamento indefinido se o arquivo apontado pelo descritor de arquivo mudou desde a última chamada enquanto `read()` não alcançou o fim do arquivo.
- Também consideramos que `get_next_line()` tem um comportamento indefinido ao ler um arquivo binário. No entanto, você pode implementar uma forma lógica de lidar com esse comportamento se desejar.

### Perguntas para Reflexão
- Sua função ainda funciona se o valor de `BUFFER_SIZE` for 9999? E se for 1? 10000000? Você sabe por quê?
- Tente ler o mínimo possível cada vez que `get_next_line()` for chamada. Se você encontrar uma nova linha, deve retornar a linha atual.
- Não leia o arquivo inteiro e depois processe cada linha.

### Proibido
- Não é permitido usar sua libft neste projeto.
- `lseek()` é proibido.
- Variáveis globais são proibidas.

---

## Parte Bônus

Este projeto é direto e não permite bônus complexos. No entanto, confiamos em sua criatividade. Se você completou a parte obrigatória, experimente esta parte bônus.

### Requisitos da Parte Bônus
- Desenvolva `get_next_line()` usando apenas uma variável estática.
- Sua função `get_next_line()` pode gerenciar múltiplos descritores de arquivo ao mesmo tempo. Por exemplo, se você puder ler dos descritores de arquivo 3, 4 e 5, deve ser capaz de ler de um descritor diferente por chamada sem perder o thread de leitura de cada descritor ou retornar uma linha de outro descritor.
  - Isso significa que você deve ser capaz de chamar `get_next_line()` para ler do descritor 3, depois 4, depois 5, depois novamente 3, novamente 4, e assim por diante.
- Adicione o sufixo `_bonus.[c/h]` aos arquivos da parte bônus.
  - Arquivos a serem entregues:
    - `get_next_line_bonus.c`
    - `get_next_line_bonus.h`
    - `get_next_line_utils_bonus.c`
- A parte bônus será avaliada apenas se a parte obrigatória estiver PERFEITA. Perfeito significa que a parte obrigatória foi realizada integralmente e funciona sem falhas. Se você não passar todos os requisitos obrigatórios, sua parte bônus não será avaliada.

---

## Envio e Avaliação por Pares

Entregue sua tarefa no repositório git atribuído como de costume. Somente o trabalho dentro do seu repositório será avaliado durante a defesa. Não hesite em verificar novamente os nomes dos seus arquivos para garantir que estejam corretos.

### Considerações ao Escrever Seus Testes
1. Tanto o tamanho do buffer quanto o tamanho da linha podem ser de valores muito diferentes.
2. Um descritor de arquivo não aponta apenas para arquivos regulares.

Seja inteligente e faça uma verificação cruzada com seus colegas. Prepare um conjunto completo de testes diversos para a defesa.

Uma vez aprovado, não hesite em adicionar seu `get_next_line()` à sua libft.

---
