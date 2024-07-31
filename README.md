# Get Next Line

## Resumo

Este projeto envolve a programação de uma função que retorna uma linha lida de um descritor de arquivo.

**Versão:** 12

## Conteúdos

- [I Objetivos](#i-objetivos)
- [II Instruções Comuns](#ii-instruções-comuns)
- [III Parte Obrigatória](#iii-parte-obrigatória)
- [IV Parte Bônus](#iv-parte-bônus)
- [V Submissão e Avaliação por Pares](#v-submissão-e-avaliação-por-pares)

---

## I Objetivos

Este projeto não só permitirá que você adicione uma função muito conveniente à sua coleção, mas também introduzirá um conceito altamente interessante na programação em C: variáveis estáticas.

---

## II Instruções Comuns

- Seu projeto deve ser escrito em C.
- Seu projeto deve estar de acordo com a Norme. Se você tiver arquivos/funções bônus, eles serão incluídos na verificação de normas e você receberá nota 0 se houver um erro de norma.
- Suas funções não devem terminar inesperadamente (falha de segmentação, erro de barramento, liberação dupla, etc.), exceto para comportamentos indefinidos. Se isso acontecer, seu projeto será considerado não funcional e receberá nota 0 durante a avaliação.
- Toda memória alocada no heap deve ser liberada corretamente quando necessário. Não serão tolerados vazamentos de memória.
- Se o assunto exigir, você deve enviar um Makefile que compile seus arquivos-fonte com as flags `-Wall`, `-Wextra` e `-Werror`, usar `cc` e garantir que seu Makefile não relinka.
- Seu Makefile deve conter pelo menos as regras `$(NAME)`, `all`, `clean`, `fclean` e `re`.
- Para incluir bônus em seu projeto, você deve adicionar uma regra `bonus` ao seu Makefile. Essa regra deve incluir todos os diversos cabeçalhos, bibliotecas ou funções que são proibidos na parte principal do projeto. Os bônus devem estar em um arquivo separado `_bonus.{c/h}` se não for especificado de outra forma. As partes obrigatória e bônus são avaliadas separadamente.
- Se seu projeto permitir usar sua `libft`, você deve copiar seus fontes e Makefile para uma pasta `libft`. O Makefile do seu projeto deve compilar a biblioteca usando seu Makefile e depois compilar o projeto.
- Recomendamos criar programas de teste para seu projeto, embora esse trabalho não precise ser enviado nem avaliado. Isso ajudará você a testar seu trabalho e o trabalho de seus pares. Esses testes serão especialmente úteis durante a defesa. Durante a defesa, você pode usar seus testes e/ou os testes do par que está avaliando.
- Submeta seu trabalho no repositório git atribuído. Apenas o trabalho no repositório git será avaliado. Se o Deepthought for atribuído para avaliar seu trabalho, isso será feito após suas avaliações por pares. Se um erro ocorrer em qualquer seção do seu trabalho durante a avaliação do Deepthought, a avaliação será interrompida.

---

## III Parte Obrigatória

**Nome da Função:** `get_next_line`

**Protótipo:** `char *get_next_line(int fd);`

**Arquivos a Submeter:** `get_next_line.c`, `get_next_line_utils.c`, `get_next_line.h`

**Parâmetros:**
- `fd`: O descritor de arquivo de onde ler

**Valor de Retorno:**
- **Linha Lida:** Comportamento correto
- **NULL:** Se não houver mais nada a ler ou se ocorreu um erro

**Funções Externas:** `read`, `malloc`, `free`

**Descrição:**
- Escreva uma função que retorna uma linha lida de um descritor de arquivo.
- Chamadas repetidas (por exemplo, usando um loop) para sua função `get_next_line()` devem permitir que você leia o arquivo de texto apontado pelo descritor de arquivo, uma linha por vez.
- Sua função deve retornar a linha que foi lida. Se não houver mais nada para ler ou se ocorrer um erro, deve retornar NULL.
- Certifique-se de que sua função funciona como esperado tanto ao ler um arquivo quanto ao ler da entrada padrão.
- Note que a linha retornada deve incluir o caractere de terminação `\n`, exceto se o final do arquivo foi alcançado e não termina com um caractere `\n`.
- Seu arquivo de cabeçalho `get_next_line.h` deve conter pelo menos o protótipo da função `get_next_line()`.
- Adicione todas as funções auxiliares necessárias no arquivo `get_next_line_utils.c`. Um bom começo seria entender o que é uma variável estática.
- Como você precisará ler arquivos na `get_next_line()`, adicione a opção `-D BUFFER_SIZE=n` na chamada do seu compilador para definir o tamanho do buffer para `read()`. Esse valor será modificado pelos avaliadores e pela Moulinette para testar seu código.
- Você deve compilar este projeto com e sem a flag `-D BUFFER_SIZE` além das flags usuais. Você pode escolher o valor padrão de sua escolha. Por exemplo:

  ```bash
  cc -Wall -Wextra -Werror -D BUFFER_SIZE=42 <arquivos>.c

