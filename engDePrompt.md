## O que são Large Language Models (LLMs)?
Um Large Language Model (LLM) é um modelo de linguagem que aprende padrões da linguagem humana e as relações entre as palavras.

### Word Embeddings
LLMs utilizam "Word Embeddings", que são representações numéricas de palavras que compreendem a proximidade semântica entre elas. Através dessas representações numéricas, o modelo consegue realizar cálculos e prever as próximas palavras em uma sequência.

Por exemplo, como ilustrado na imagem abaixo, é possível observar a relação entre "homem" e "mulher", ou "rei" e "rainha" no eixo masculino-feminino, e entre verbos como "andando" e "andei", ou "cozinhando" e "cozinhei" no eixo de tempos verbais.

https://github.com/JuniorPlantier/engenhariaDePrompt/img/wordEmbeddings.JPG

### Temperatura do Modelo
A "temperatura" é um conceito que controla a aleatoriedade das respostas de um LLM
* Uma temperatura mais alta resulta em respostas mais variadas.
* Uma temperatura baixa faz com que o modelo tenda a escolher as respostas mais prováveis.

### Tokens
Tokens são as unidades básicas em modelos de linguagem e representam palavras ou subpalavras. Por exemplo, a palavra "infeliz" pode ser dividida em dois tokens: "in" e "feliz".

Você pode usar ferramentas como o tokenizador da OpenAI para ver como as frases são quebradas em tokens:
* [https://platform.openai.com/tokenizer](https://platform.openai.com/tokenizer) [cite: 20]

A imagem abaixo mostra um exemplo de tokenização de uma frase:

![Exemplo de Tokenização](https://raw.githubusercontent.com/seu-usuario/seu-repositorio/main/caminho/para/sua/imagem_tokens.png)
*(Você precisará substituir `https://raw.githubusercontent.com/seu-usuario/seu-repositorio/main/caminho/para/sua/imagem_tokens.png` pelo link direto da sua imagem no GitHub)*

## Princípios da Engenharia de Prompt

A Engenharia de Prompt visa projetar prompts da melhor maneira possível para obter os resultados desejados[cite: 23]. Alguns princípios importantes incluem:
* Ter clareza ao dar as instruções[cite: 24].
* Dividir tarefas complexas em subtarefas menores[cite: 25].
* Pedir para o modelo explicar seus passos antes de dar a resposta[cite: 26].
* Pedir para o modelo dar justificativas de suas respostas[cite: 27].
* Gerar várias respostas diferentes e pedir para o modelo escolher a melhor[cite: 28].

## Técnicas de Prompting

Existem diversas técnicas para interagir com LLMs, cada uma adequada para diferentes cenários:

### Zero-shot, One-shot e Few-shot Prompting

* **Zero-shot prompting**: Consiste em fornecer apenas o comando, sem exemplos[cite: 30].
    * **Quando utilizar**: Exploração inicial de novas tarefas sem exemplos; quando se quer que o modelo generalize; em tarefas simples e bem definidas (ex: categorização de spams óbvios); situações que exigem respostas rápidas em detrimento de precisão; quando fornecer exemplos específicos pode introduzir viés indesejado[cite: 30].
* **One-shot prompting**: Inclui um exemplo do comportamento esperado do modelo, além do comando[cite: 30].
* **Few-shot prompting**: Inclui dois ou mais exemplos do comportamento esperado do modelo, além do comando[cite: 30].
    * **Quando utilizar**: Quando a tarefa requer alta precisão; geração de textos com um formato definido; em categorizações com muita variedade; tarefas com regras complexas[cite: 30].

### Chain-of-Thought (Cadeia de Pensamento)

A técnica Chain-of-Thought (Cadeia de Pensamento) é utilizada em situações que demandam pensamento lógico complexo ou abstrato[cite: 33, 34]. Ela nasceu com base na Few-shot Prompting, onde a cadeia de pensamentos é apresentada na resposta de cada exemplo fornecido, permitindo que o modelo replique a lógica para soluções de problemas mais simbólicos[cite: 35, 36].

**Exemplo:**
**Pergunta**: O Rogério tem 5 bolas de tênis. Ele compra mais 2 caixas de bolas, cada uma com 3 bolas. Quantas bolas de tênis ele tem agora?

**Resposta**: O Rogério inicialmente tinha 5 bolas de tênis. Se cada caixa tem 3 bolas e ele comprou 2 caixas, isso significa que ele comprou mais 6 bolas. Ou seja, no total agora ele tem 5 + 6, que resulta em 11 bolas de tênis. [cite: 37]

**Pergunta**: Havia 23 maçãs no refeitório. Se foram usadas 20 para fazer o almoço e foram compradas mais 6, quantas maçãs eles têm agora? [cite: 37]

**Resposta (Chain-of-Thought)**:
No início, havia 23 maçãs. Se foram usadas 20 para fazer o almoço, sobraram 23-20 = 3 maçãs.
Como foram compradas mais 6 maçãs, agora eles têm 3 + 6 = 9 maçãs no total. [cite: 38]

Esta técnica é descrita em um artigo do Google Research e Google Brain (DeepMind): [Chain-of-Thought Prompting Elicits Reasoning in Large Language Models](https://arxiv.org/abs/2201.11903)[cite: 40, 41, 42].

Um bom prompt utilizando Chain-of-Thought para otimização de algoritmos seria: "Armano pode descrever a arquitetura do projeto, fornecer exemplos dos problemas encontrados na execução e solicitar que o modelo explique passo a passo a análise desses exemplos e como otimizar o desempenho do sistema de busca." [cite: 45]

### Least-to-Most Prompting

Esta técnica envolve quebrar um problema complexo em problemas menores e mais gerenciáveis[cite: 47, 48].

### Chain-of-Verification

A técnica Chain-of-Verification serve para verificar a correção da informação fornecida pelo modelo[cite: 50, 51]. O processo geralmente segue estas etapas:
1.  Prompt e resposta iniciais[cite: 51].
2.  Geração das perguntas de verificação[cite: 51].
3.  Execução das verificações[cite: 51].
4.  Geração da resposta final verificada[cite: 51].

### Self-Consistency

A Self-Consistency é uma técnica que visa mitigar respostas incorretas ou "alucinadas" do modelo[cite: 53, 54]. Para isso, a mesma pergunta é feita várias vezes ao modelo[cite: 55].

## Considerações Finais

Lembre-se de não usar o LLM como um martelo para resolver todos os problemas[cite: 44]. É importante ensinar ao modelo o tom de voz desejado[cite: 43].