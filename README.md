# Estrutura de Dados e Algoritmos em C#

Este repositório documenta minha jornada de aprendizado em Estruturas de Dados, focando não apenas na sintaxe do C#, mas na engenharia de software e análise de complexidade (Big O Notation).

## 1. Análise de Complexidade (Big O)

Antes de escrever código, é crucial entender como ele se comporta conforme o volume de dados cresce. Não medimos velocidade em segundos, mas em **passos de execução**.

| Notação | Nome | Descrição | Exemplo Prático |
| :--- | :--- | :--- | :--- |
| **$O(1)$** | Constante | O tempo é o mesmo, não importa o tamanho da entrada. | Acessar um índice de Array (`arr[5]`). |
| **$O(\log n)$** | Logarítmico | O tempo cresce muito pouco; corta o problema pela metade a cada passo. | Busca Binária. |
| **$O(n)$** | Linear | O tempo cresce proporcionalmente aos dados (10 itens = 10 passos). | Loop `foreach` simples. |
| **$O(n^2)$** | Quadrático | O desempenho degrada exponencialmente. Evitar em grandes volumes. | Loops aninhados (um `for` dentro de outro). |

---

## 2. Arrays (Vetores)

A estrutura de dados mais fundamental. No C#, arrays são objetos alocados na Heap, mas seus elementos são armazenados em um bloco **contíguo** de memória.

### Características
* **Tamanho Fixo:** Uma vez criado (`new int[5]`), não pode aumentar ou diminuir.
* **Acesso Rápido:** Como a memória é contígua, o acesso matemático ao endereço é instantâneo.
* **Tipagem Forte:** Armazena apenas um tipo de dado definido.

### Análise de Performance

| Operação | Complexidade | Explicação |
| :--- | :---: | :--- |
| **Acesso (Leitura/Escrita)** | **$O(1)$** | O computador calcula o endereço de memória exato. É instantâneo. |
| **Busca (Search)** | **$O(n)$** | Para achar um valor, é necessário verificar elemento por elemento (no pior caso). |
| **Inserção/Remoção** | **N/A** | Não é possível alterar o tamanho sem criar um novo array e copiar os dados ($O(n)$). |

### Exemplo em C#

```csharp
public void ExemploArray()
{
    // Declaração e Alocação na Memória
    int[] pontuacoes = new int[5] { 10, 20, 30, 40, 50 };

    // 1. Acesso Direto - O(1)
    // O computador vai direto ao endereço de memória. Super rápido.
    int primeiraPontuacao = pontuacoes[0]; 
    pontuacoes[4] = 100;

    // 2. Busca Linear - O(n)
    // O computador não sabe onde está o valor '30'.
    // Ele precisa testar o índice 0, depois 1, depois 2...
    int valorProcurado = 30;
    bool encontrado = false;

    for (int i = 0; i < pontuacoes.Length; i++)
    {
        if (pontuacoes[i] == valorProcurado)
        {
            encontrado = true;
            break; // O(n) no pior caso (se o item estiver no fim ou não existir)
        }
    }
}
