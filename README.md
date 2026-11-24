# Comparativo de Busca no Quebra-Cabeça de 8 Peças

Repositório do projeto final da disciplina de Inteligência Artificial (IFS – Campus Itabaiana), **em desenvolvimento** para comparar o desempenho entre algoritmos de busca cega e busca heurística aplicados ao quebra-cabeça de 8 peças.

- **Instituição:** Instituto Federal de Sergipe (IFS) – Campus Itabaiana (CCOMP)
- **Disciplina:** Inteligência Artificial
- **Autores:** José Marco Melo Nascimento
- **Status:** Em desenvolvimento (Entrega 1 – Definição e ambiente)

---

## Sobre o projeto

O quebra-cabeça de 8 peças consiste em um tabuleiro 3x3 com oito peças numeradas e um espaço vazio. O objetivo é reorganizar uma configuração inicial embaralhada até atingir o estado final abaixo, deslizando uma peça por vez para o espaço livre:

```text
1 2 3
4 5 6
7 8 _

```

Toda a lógica de busca está sendo escrita do zero em Python, sem bibliotecas prontas para grafos ou algoritmos de busca, permitindo instrumentar e comparar o custo computacional de cada abordagem.

### Escopo previsto

* Modelagem de estados, ações válidas e verificação de objetivo em grade 3x3.
* Validação prévia de solvabilidade (metade das configurações possíveis do tabuleiro não possui solução).
* Implementação da **Busca em Largura (BFS)** como estratégia de busca cega.
* Implementação do **A*** com duas funções heurísticas: **peças fora do lugar** e **distância de Manhattan**.
* Coleta de métricas por execução: nós expandidos, nós gerados, tempo de execução e tamanho do caminho.
* Interface via terminal e testes unitários para a lógica principal.

*Observação: por explorar os níveis em largura sem heurística, a BFS tende a consumir bastante memória em instâncias mais profundas.*

---

## Arquitetura planejada

A modelagem foi definida em orientação a objetos para separar a representação do problema, os algoritmos e a entrada/saída no terminal (classes a serem implementadas a partir da Entrega 2):

| Classe | Papel no sistema |
| --- | --- |
| `Estado` | Configuração do tabuleiro, geração de sucessores, teste de objetivo e verificação de solvabilidade. |
| `No` | Nó da árvore de busca (`estado`, `pai`, `acao` e custo acumulado `g`). |
| `Heuristica` | Classe base abstrata que define o contrato `calcular(estado) -> int`. |
| `PecasForaDoLugar` | Heurística que conta quantas peças estão fora de suas posições finais. |
| `DistanciaManhattan` | Heurística que soma a distância ortogonal de cada peça até sua posição objetivo. |
| `AlgoritmoBusca` | Classe base abstrata com a interface `resolver(estado_inicial) -> Resultado`. |
| `BuscaLargura` | Implementação da Busca em Largura (BFS). |
| `AEstrela` | Implementação do A* utilizando `f(n) = g(n) + h(n)`. |
| `Resultado` | Armazenamento do caminho encontrado, contadores de nós e tempo gasto. |
| `Interface` | Gerenciamento da interação no terminal de forma desacoplada da lógica de busca. |

O diagrama de classes (UML) ficará disponível no diretório [`docs/`]().

---

## Estrutura alvo do repositório

```text
comparativo-busca-quebra-cabeca-8/
├── docs/
│   └── definicao.pdf
├── src/
│   ├── busca.py
│   ├── estado.py
│   ├── heuristicas.py
│   ├── interface.py
│   ├── main.py
│   ├── no.py
│   └── resultado.py
├── tests/
│   └── test_hello.py
├── README.md
└── requirements.txt

```

Os arquivos de código-fonte e testes serão preenchidos gradualmente ao longo das entregas.

---

## Cronograma de entregas

| Entrega | Data | Escopo | Status |
| --- | --- | --- | --- |
| 1 | 26/11/2026 | Definição do problema, UML e configuração do repositório | Em andamento |
| 2 | 03/12/2026 | Classes base (`Estado`, `No`, `Resultado`) e testes iniciais | Pendente |
| 3 | 10/12/2026 | Implementação de BFS, A*, heurísticas e testes ampliados | Pendente |
| 4 | A confirmar | Refatoração, coleta de resultados, relatório e apresentação | Pendente |

---

## Resultados

Seção reservada para a Entrega 4, onde serão incluídos exemplos de execução, a tabela comparativa entre BFS e A* (com ambas as heurísticas) e a análise de limitações e casos de falha observados.

---

## Integridade acadêmica

O núcleo dos algoritmos de busca e a modelagem do problema serão desenvolvidos integralmente pelo autor. Ferramentas de IA generativa atuam apenas como apoio pontual para consultas conceituais e revisão, em estrita conformidade com as diretrizes do projeto.

## Referências

* RUSSELL, Stuart; NORVIG, Peter. *Inteligência Artificial: Uma Abordagem Moderna*. 4. ed. Rio de Janeiro: Elsevier.
passar a impressão de que os algoritmos já estão prontos.
