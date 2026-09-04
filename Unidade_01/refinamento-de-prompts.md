# Atividade - Refinamento de Prompts

## Identificação
- Nome: Gabriella Dias
- Turma: Ciência da Computação - D1
- Data: 03/09
- Ferramenta de IA utilizada: Google Gemini

---

## Problema escolhido

### Contexto
Como estudante de Ciência da Computação, é comum encontrar dificuldade para entender **recursão** logo no primeiro contato: o conceito parece abstrato, e explicações genéricas de IA generativa tendem a repetir a definição de livro-texto sem construir uma intuição real sobre o assunto.

### Problema
Como obter, com o apoio de uma IA generativa, uma explicação de recursão que seja realmente didática para um estudante iniciante — e não apenas uma definição tecnicamente correta, porém pouco compreensível?

### Objetivo
Investigar como a formulação do prompt (papel, contexto, público, formato, restrições e critérios de qualidade) influencia a qualidade, a clareza e a utilidade pedagógica da explicação gerada pela IA.

---

## Prompt 1

### Prompt
```text
Explique recursão em programação.
```

### Resultado
> A recursão, em programação, é uma técnica onde uma função chama a si mesma para resolver um problema. Em vez de usar loops tradicionais (`for` ou `while`), a função quebra um problema grande em partes menores e idênticas, resolvendo-as até chegar a um ponto de parada.
>
> Uma boa analogia é a das bonecas russas (Matrioshkas): você abre uma boneca para encontrar outra menor dentro, e repete o processo até encontrar a menor boneca de todas, que não pode mais ser aberta.
>
> **A Anatomia da Recursão**
>
> Toda função recursiva precisa obrigatoriamente de duas partes para não rodar infinitamente e travar o computador:
> 1. **Caso Base (Condição de Parada):** a regra que diz quando a função deve parar de chamar a si mesma. É o problema mais simples possível de resolver.
> 2. **Passo Recursivo:** onde a função chama a si mesma, passando um dado modificado que a deixe um passo mais próxima do Caso Base.
>
> **Exemplo Prático: Fatorial**
> ```python
> def fatorial(n):
>     # 1. Caso Base: Se o número for 0 ou 1, o fatorial é 1.
>     if n == 0 or n == 1:
>         return 1
>     # 2. Passo Recursivo: Multiplica o número pelo fatorial do número anterior.
>     else:
>         return n * fatorial(n - 1)
>
> print(fatorial(3)) # O resultado será 6
> ```
>
> **O que acontece nos bastidores (Passo a Passo)**
>
> Quando você roda `fatorial(3)`, o computador "empilha" as tarefas até chegar ao caso base:
> 1. `fatorial(3)` não é o caso base. Calcula `3 * fatorial(2)` (espera o resultado).
> 2. `fatorial(2)` não é o caso base. Calcula `2 * fatorial(1)` (espera o resultado).
> 3. `fatorial(1)` é o caso base! Retorna `1`.
>
> Agora que o computador encontrou um valor real, ele volta resolvendo as pendências (desempilhando): `fatorial(2)` resolve `2 * 1 = 2`; `fatorial(3)` resolve `3 * 2 = 6`. Resultado final: 6.

### Análise
- **O que funcionou:** mesmo sem nenhuma instrução de formato, a resposta já veio estruturada em seções, com analogia (bonecas russas) e um passo a passo da pilha de chamadas — mais completa do que o esperado para um prompt tão curto.
- **O que faltou:** não há indicação de público (fica implícito que o leitor já programa, mas não se sabe o nível); não há comparação com a versão iterativa do mesmo problema; não há menção a um erro comum nem ao "estouro de pilha"; não há nenhuma forma de verificar se o leitor entendeu.
- **O que ficou genérico:** a resposta assume um nível médio de conhecimento sem declarar isso — funcionaria bem para quem já programa, mas pode ser rápida demais para um iniciante absoluto.
- **O que poderia ser melhor:** comparação explícita recursão vs. iteração, um erro comum de iniciante e algum critério de verificação de aprendizagem.

---

## Prompt 2

### Alterações realizadas
- Papel: professor especializado em algoritmos e estruturas de dados
- Contexto: estudantes do 2º semestre, já conhecem laços e funções, nunca viram recursão
- Objetivo: compreensão do funcionamento, não só da definição
- Público: iniciantes em recursão (mas não em programação)
- Formato: subtítulos e exemplo comentado
- Restrições: limite de palavras, linguagem acessível
- Critérios: comparação explícita entre recursão e iteração, e um erro comum

### Prompt
```text
Atue como professor de Ciência da Computação especializado em
Algoritmos e Estruturas de Dados.

Explique o conceito de recursão para estudantes de graduação que
já conhecem estruturas condicionais, laços de repetição (for/while)
e funções, mas ainda não estudaram recursão.

Apresente:
1. uma definição simples;
2. os dois elementos essenciais de toda função recursiva
   (caso base e caso recursivo);
3. um exemplo comentado em Python (cálculo de fatorial);
4. uma comparação entre a versão recursiva e a versão iterativa
   do mesmo problema;
5. um erro comum cometido por iniciantes ao escrever funções
   recursivas.

Utilize linguagem acessível, organize a resposta com subtítulos
e limite o texto a aproximadamente 400 palavras.
```

### Resultado
> **O que é Recursão?**
>
> Em Ciência da Computação, a recursão ocorre quando uma função resolve um problema chamando a si mesma. Em vez de usar um laço de repetição (como `for` ou `while`) para processar dados repetidamente, a função resolve apenas uma pequena parte do problema e "delega" o restante para uma nova cópia de si mesma.
>
> **Os Dois Elementos Essenciais**
> 1. **Caso Base (Condição de Parada):** a versão mais simples do problema, resolvida diretamente, sem novas chamadas. Diz à função quando ela deve parar.
> 2. **Caso Recursivo:** onde a função chama a si mesma, sempre alterando os argumentos de entrada para ficarem um passo mais próximos do Caso Base.
>
> **Exemplo Prático: Cálculo de Fatorial**
> ```python
> def fatorial(n):
>     # 1. Caso Base: O fatorial de 0 ou 1 é sempre 1
>     if n <= 1:
>         return 1
>     # 2. Caso Recursivo: n multiplicado pelo fatorial de (n-1)
>     else:
>         return n * fatorial(n - 1)
>
> print(fatorial(3)) # Resultado: 6
> ```
> Quando chamamos `fatorial(3)`, o computador empilha as tarefas: a função executa `3 * fatorial(2)`; `fatorial(2)` executa `2 * fatorial(1)`; `fatorial(1)` atinge o caso base e retorna `1`. Em seguida, o computador "desempilha", resolvendo as multiplicações pendentes: `2 * 1 = 2` e, finalmente, `3 * 2 = 6`.
>
> **Recursão vs. Iteração**
> O mesmo fatorial poderia ser resolvido de forma iterativa, usando um laço `for` para multiplicar os números e acumular o resultado em uma variável.
> - **Iterativo:** geralmente mais eficiente em processamento e memória, pois reaproveita o mesmo espaço durante o loop.
> - **Recursivo:** pode consumir mais memória RAM (cada chamada é salva na pilha de execução), mas frequentemente resulta em código mais limpo e elegante. Brilha em problemas complexos, como navegar por pastas do computador ou percorrer Árvores e Grafos, onde `while`/`for` seria muito trabalhoso.
>
> **O Erro Mais Comum: Estouro de Pilha**
> Esquecer de programar o caso base (ou escrever um caso recursivo que nunca chega até ele). Se esquecêssemos o `if n <= 1`, a função chamaria `fatorial(0)`, `fatorial(-1)`, `fatorial(-2)` infinitamente. Como o computador guarda na memória cada chamada pendente, a memória eventualmente lota e o programa trava — o famoso *Stack Overflow*.

### Análise das melhorias
A resposta ficou mais adequada ao público (parte explicitamente do que o estudante já sabe) e trouxe a comparação recursão/iteração e o erro comum, que estavam ausentes no Prompt 1. Por outro lado, um resultado inesperado: a **analogia das bonecas russas**, que havia surgido espontaneamente no Prompt 1, **desapareceu** no Prompt 2 — o prompt não pediu analogia, e a IA não a manteve. O passo a passo numerado da pilha de chamadas também ficou mais resumido do que no Prompt 1. Ou seja, pedir mais estrutura não significa reter automaticamente tudo o que era bom na resposta anterior: é preciso pedir explicitamente o que se quer manter.

---

## Comparação

| Critério | Prompt 1 | Prompt 2 |
|---|---:|---:|
| Clareza | 4 | 4 |
| Precisão | 5 | 5 |
| Relevância | 3 | 4 |
| Organização | 4 | 4 |
| Adequação ao público | 2 | 4 |
| Atendimento ao objetivo | 3 | 4 |
| Utilidade prática | 3 | 4 |

---

## Prompt 3

### O que ainda precisava melhorar?
O Prompt 2 é tecnicamente correto, bem organizado e adequado ao público, mas perdeu a analogia intuitiva que havia no Prompt 1, não trouxe uma tabela comparativa visual entre recursão e iteração, não indicou quando recursão *não* é a melhor escolha, e não fechou com nenhuma forma de verificar se o estudante entendeu.

### Hipótese
Acredito que a resposta ficará melhor porque, ao pedir explicitamente a analogia, uma tabela comparativa, uma situação em que recursão não é recomendada e perguntas de verificação, a IA será obrigada a reunir em uma única resposta tudo o que apareceu de bom (e faltou) nas duas tentativas anteriores.

### Prompt
```text
Atue como professor de Ciência da Computação especializado em
Algoritmos e Estruturas de Dados.

CONTEXTO:
Os estudantes estão no segundo semestre de Ciência da Computação,
já programam em Python, conhecem laços de repetição e funções,
mas nunca implementaram uma função recursiva.

OBJETIVO:
Fazer com que os estudantes compreendam intuitivamente a
funcionamento da recursão e saibam identificar quando utilizá-la.

TAREFA:
Explique o conceito de recursão apresentando:
1. definição em linguagem simples;
2. uma analogia com uma situação cotidiana (por exemplo, bonecas
   russas ou dois espelhos posicionados um de frente para o outro);
3. os dois elementos essenciais: caso base e caso recursivo;
4. um exemplo comentado em Python (cálculo de fatorial),
   mostrando como fica a pilha de chamadas;
5. uma comparação entre a versão recursiva e a versão iterativa
   do mesmo problema;
6. um erro comum cometido por iniciantes (esquecer o caso base)
   e sua consequência (estouro de pilha);
7. uma situação em que a recursão não seria a melhor solução.

FORMATO:
Organize a resposta com subtítulos e uma tabela comparando
recursão e iteração (vantagens, desvantagens, uso de memória).

RESTRIÇÕES:
- máximo de 500 palavras;
- utilizar apenas Python nos exemplos;
- explicar qualquer termo técnico utilizado
  (por exemplo, "pilha de chamadas").

CRITÉRIO DE QUALIDADE:
Ao final da explicação, um estudante iniciante deverá conseguir
explicar recursão com suas próprias palavras e identificar, em um
problema novo, se ele deveria usar recursão ou iteração.

Finalize apresentando duas perguntas para verificar a compreensão
do estudante.
```

### Resultado
> **O que é Recursão?**
>
> Em programação, a recursão ocorre quando uma função resolve um problema chamando a si mesma. Em vez de usar um laço de repetição (como `for` ou `while`), a função pega o problema original, resolve uma pequena parte dele e "delega" o resto para uma nova cópia de si mesma.
>
> **A Analogia das Bonecas Russas**
>
> Pense nas Matrioshkas: para descobrir quantas bonecas existem no total, você abre a maior e encontra uma menor dentro. Você repete o processo de abrir a boneca (o **caso recursivo**) até chegar à menor boneca de todas, que é maciça e não pode mais ser aberta (o **caso base**).
>
> **Os Dois Elementos Essenciais**
> - **Caso Base:** a condição de parada — a versão mais simples do problema, resolvida diretamente.
> - **Caso Recursivo:** a parte em que a função chama a si mesma com um argumento modificado, aproximando-se do Caso Base.
>
> **Exemplo em Python: Fatorial**
> ```python
> def fatorial(n):
>     # 1. Caso Base: O problema mais simples
>     if n <= 1:
>         return 1
>     # 2. Caso Recursivo: Chama a si mesma com (n - 1)
>     else:
>         return n * fatorial(n - 1)
>
> print(fatorial(3))
> ```
>
> **A Pilha de Chamadas (Call Stack)**
>
> Quando rodamos `fatorial(3)`, o computador usa a pilha de chamadas — uma área de memória que organiza quais funções estão em andamento — para pausar as tarefas inacabadas:
> 1. `fatorial(3)` pausa e chama `fatorial(2)`.
> 2. `fatorial(2)` pausa e chama `fatorial(1)`.
> 3. `fatorial(1)` atinge o Caso Base e retorna `1`.
>
> Agora o computador desempilha, resolvendo as multiplicações pausadas: `1 * 2 = 2` e, finalmente, `2 * 3 = 6`.
>
> **Recursão vs. Iteração**
>
> | Característica | Recursão | Iteração (for / while) |
> |---|---|---|
> | Vantagens | Código limpo e elegante; ideal para dividir problemas complexos. | Mais rápida na execução. |
> | Desvantagens | Mais difícil de debugar para iniciantes. | O código pode ficar longo e complexo em estruturas de dados difíceis. |
> | Uso de memória | Alto (cada chamada pausada gasta espaço na memória). | Baixo (reutiliza a mesma variável). |
>
> **O Perigo do Estouro de Pilha**
>
> O erro mais comum dos iniciantes é esquecer o Caso Base. Se tirarmos o `if n <= 1` do código, a função continuará chamando `fatorial(0)`, `fatorial(-1)`, `fatorial(-2)` infinitamente. Como cada chamada consome um pedaço da memória, o computador eventualmente fica sem espaço e trava. Esse colapso é chamado de *Stack Overflow* (Estouro de Pilha).
>
> **Quando NÃO usar recursão**
>
> A recursão não é recomendada para tarefas simples e lineares. Se você quer apenas imprimir os números de 1 a 100 na tela ou somar os valores de uma lista simples, usar um laço `for` é muito mais inteligente, rápido e economiza memória.
>
> **Verifique seu entendimento:**
> 1. Se você esquecer de incluir um "caso base" na sua função recursiva, o que acontecerá com a memória do computador ao executá-la?
> 2. Ao ler um arquivo que contém dezenas de pastas, e cada pasta tem outras subpastas dentro (como as bonecas russas), você usaria recursão ou um laço `while` para listar todos os arquivos? Por quê?

### Comparação com o Prompt 2
O Prompt 3 recuperou a analogia das bonecas russas que havia se perdido no Prompt 2, trouxe de volta o passo a passo numerado da pilha de chamadas (mais claro que a versão resumida do Prompt 2), acrescentou a tabela comparativa visual, a seção "quando não usar recursão" e as duas perguntas de verificação. É o único dos três que reúne, ao mesmo tempo, intuição (analogia), rigor técnico (pilha de chamadas, comparação) e fechamento pedagógico (perguntas). Cada elemento pedido teve reflexo direto e identificável na resposta.

---

## Comparação final

| Critério | Prompt 1 | Prompt 2 | Prompt 3 |
|---|---:|---:|---:|
| Clareza | 4 | 4 | 5 |
| Precisão | 5 | 5 | 5 |
| Relevância | 3 | 4 | 5 |
| Organização | 4 | 4 | 5 |
| Adequação ao público | 2 | 4 | 5 |
| Atendimento ao objetivo | 3 | 4 | 5 |
| Utilidade prática | 3 | 4 | 5 |
| **Total** | **24** | **29** | **35** |

---

## Validação

Antes de considerar o conteúdo confiável, conferi:
- **Conceitos:** a definição de recursão, caso base/caso recursivo e pilha de chamadas correspondem ao que é apresentado em materiais de Estruturas de Dados e Algoritmos amplamente utilizados no curso, nas três respostas.
- **Código:** conferi manualmente o código de `fatorial(n)` nas três versões — todas calculam corretamente `fatorial(3) = 6`, e a condição de caso base (`n == 0 or n == 1` / `n <= 1`) está correta e consistente entre as respostas.
- **Passo a passo da pilha de chamadas:** o detalhamento apresentado nos Prompts 1 e 3 (`fatorial(3) → fatorial(2) → fatorial(1)`, depois desempilhando `1 → 2 → 6`) está correto e bate com o comportamento real de uma execução em Python.
- **Afirmações sem fonte:** nenhuma das respostas trouxe estatísticas, nomes de autores ou "fatos" que precisassem de checagem externa — é um conteúdo predominantemente conceitual.
- **Ponto que merece atenção:** a tabela do Prompt 3, ao ser copiada do Gemini, veio sem as quebras de coluna corretas (texto colado em bloco); tive que reconstruir a tabela manualmente a partir do conteúdo. Isso reforça a importância de conferir também a **formatação**, e não só o conteúdo, antes de usar uma resposta de IA diretamente.
- **Generalização de risco:** a afirmação de que a versão iterativa é "geralmente mais eficiente" (Prompt 2) e "mais rápida na execução" (Prompt 3) é razoável, mas depende do contexto (linguagem, limite de recursão configurado, otimizações como recursão de cauda em outras linguagens) — vale aprofundar antes de tratá-la como regra absoluta.

---

## Reflexão

### 1. Qual foi a principal diferença entre os prompts?
O Prompt 1 pedia apenas uma "explicação", sem indicar público, formato ou profundidade — e mesmo assim o Gemini já trouxe analogia e estrutura por conta própria. O Prompt 2 definiu papel, contexto, público, estrutura e restrições, o que tornou a resposta mais adequada ao público-alvo, mas custou a analogia que existia antes. O Prompt 3 reuniu o melhor dos dois anteriores e ainda acrescentou tabela, "quando não usar" e perguntas de verificação.

### 2. Quais elementos tiveram maior impacto?
A definição de **público** (Prompt 2) foi o que mais mudou a adequação da resposta. Mas o achado mais interessante foi outro: pedir **estrutura** não garante manter o que já era bom — a analogia sumiu no Prompt 2 e só voltou no Prompt 3 porque foi pedida explicitamente. Isso mostra que refinar um prompt exige dizer também o que **deve continuar presente**, não apenas o que precisa ser acrescentado.

### 3. Um prompt mais longo necessariamente produz uma resposta melhor? Justifique.
Não necessariamente. O Prompt 1, mesmo curto, já trouxe uma resposta rica (analogia + passo a passo da pilha). O ganho do Prompt 2 e do Prompt 3 não veio do tamanho do prompt, e sim de pedir elementos específicos (comparação, tabela, perguntas) que o modelo não incluiria por padrão sozinho — e, no caso da analogia, de garantir explicitamente que algo bom da versão anterior não se perdesse.

### 4. O que acontece quando o objetivo não está claramente definido?
A IA preenche a lacuna com suposições — no caso do Prompt 1, ela decidiu por conta própria incluir uma analogia e um passo a passo, o que foi uma sorte, mas não haveria garantia disso. Sem objetivo claro, o resultado fica sujeito à "criatividade" do modelo, que pode ou não coincidir com o que o usuário realmente precisa.

### 5. Quais informações você considera indispensáveis para elaborar um bom prompt?
Público-alvo, objetivo específico, formato esperado, e — um aprendizado desta atividade — o que deve ser **preservado** de uma resposta anterior ao refinar o prompt, além do que deve ser adicionado.

### 6. Como o refinamento de prompts pode ser útil para um profissional de Ciência da Computação?
Na prática profissional, prompts mal formulados geram retrabalho — respostas genéricas que precisam ser reescritas, documentação fora do público-alvo, tabelas ou formatos que se perdem entre uma iteração e outra. Saber refinar prompts de forma estruturada, e saber o que reforçar a cada nova versão, economiza tempo ao usar IA como apoio em tarefas como automação, documentação técnica ou geração de código.

### 7. Que riscos podem surgir quando confiamos em uma resposta da IA sem avaliar sua qualidade?
Aceitar generalizações como regras absolutas (ex.: "iteração é sempre mais rápida"), usar uma tabela ou formatação que veio corrompida na cópia sem perceber, ou assumir que um elemento bom (como a analogia) sempre vai aparecer, quando na prática ele depende do que foi pedido.

### 8. Houve alguma situação em que o Prompt 3 ficou pior que o Prompt 2? Se sim, explique.
Não em termos de conteúdo — o Prompt 3 manteve tudo que o Prompt 2 tinha de bom e ainda recuperou a analogia. A única ressalva é de formatação: a tabela veio malformada na cópia do Gemini e precisou ser reconstruída manualmente, algo que não aconteceu com o texto mais simples do Prompt 2.

### 9. Existe um ponto em que adicionar mais instruções começa a prejudicar a resposta?
Sim, embora não tenha acontecido de forma grave neste laboratório. O risco aparece quando instruções competem entre si (ex.: pedir "resposta muito detalhada" e um limite de palavras baixo ao mesmo tempo) ou quando o número de elementos obrigatórios é tão grande que a resposta vira uma lista de tópicos soltos em vez de um texto coeso — algo que quase aconteceu no Prompt 3, que tem sete itens de tarefa mais formato, restrições e critério de qualidade.

### 10. O que você faria para verificar se a resposta tecnicamente está correta?
Executaria o código de exemplo em um interpretador Python real, compararia a definição com a bibliografia da disciplina (livros de Algoritmos e Estruturas de Dados) e, em caso de dúvida sobre a comparação recursão/iteração, testaria os dois casos com entradas maiores para observar o comportamento real (tempo de execução, uso de memória, limite de recursão do Python).

---

## Take Away

> Um bom prompt não é simplesmente um prompt longo. Ele precisa **ser específico sobre quem vai responder, para quem, com qual objetivo, em qual formato — e também sobre o que deve ser preservado das tentativas anteriores, para que o refinamento não jogue fora o que já estava bom.**

---

## Cinco recomendações

1. Antes de escrever o prompt, defina o público que vai receber a resposta — isso muda tudo, do vocabulário ao nível de profundidade.
2. Prefira pedir estrutura (tópicos, tabelas, exemplos) a pedir adjetivos vagos como "completo" ou "detalhado".
3. Ao refinar um prompt, diga explicitamente o que deve continuar presente da resposta anterior, não só o que precisa ser acrescentado — um elemento bom pode desaparecer se não for pedido de novo.
4. Trate a primeira resposta como um rascunho, não como resultado final: analise criticamente antes de refinar.
5. Nunca utilize uma resposta de IA sem verificar pelo menos os pontos centrais (conceitos, código, dados) e também a formatação (tabelas e listas podem vir corrompidas ao copiar).

---

## Desafio final

Cinco perguntas para diagnosticar o problema antes de modificar o prompt do colega:

```text
1. O prompt deixava claro para quem a resposta deveria ser escrita?
2. O objetivo da tarefa estava explícito, ou apenas implícito?
3. A resposta estava incorreta de fato, ou apenas não era o que ele esperava?
4. Ele verificou a informação em alguma fonte antes de considerá-la "errada"?
5. O prompt continha instruções contraditórias entre si (ex.: "curto" e "muito detalhado")?
```

### Pergunta final
O problema pode estar em qualquer um dos quatro pontos — no prompt (falta de contexto/objetivo), na resposta da IA (erro conceitual real), nas informações usadas (dados desatualizados ou incorretos) ou na avaliação do usuário (esperar algo que nunca foi pedido, ou não perceber que a formatação se perdeu na cópia). Neste laboratório, o Prompt 1 já surpreendeu positivamente, o Prompt 2 perdeu um elemento bom por não pedi-lo explicitamente, e o Prompt 3 mostrou que mesmo uma resposta tecnicamente correta e completa ainda pode ter problemas de formatação que exigem checagem manual — ou seja, um prompt melhor reduz, mas não elimina, a necessidade de validar o resultado.
