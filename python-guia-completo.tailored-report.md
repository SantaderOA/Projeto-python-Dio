# Guia de Referência Completo e Repositório da Linguagem Python

Este repositório documental oferece um mapeamento estruturado e detalhado da linguagem de programação Python (versão 3.x), abrangendo desde a sintaxe fundamental e instruções de controle de fluxo até estruturas de dados avançadas, orientação a objetos, funções integradas e módulos da biblioteca padrão.

---

## 1. Visão Geral e Sintaxe Fundamental

Python é uma linguagem de programação de alto nível, interpretada, de tipagem dinâmica e forte, de propósito geral e multi-paradigma (suportando programação imperativa, orientada a objetos e funcional). Criada por Guido van Rossum em 1991, destaca-se por sua filosofia de design focada na legibilidade do código, expressa no *Zen do Python* (PEP 20).

### Indentação Significativa e Blocos de Código
Ao contrário de linguagens derivadas do C/C++ ou Java, que utilizam chaves `{}` para delimitar blocos, o Python utiliza a indentação de espaço em branco como regra sintática obrigatória. O padrão recomendado pela comunidade (PEP 8) é o uso de 4 espaços por nível de indentação.

```python
# Exemplo de bloco de código indentado
def verificar_nivel(idade):
    if idade >= 18:
        status = "Adulto"
        print("Acesso concedido.")
    else:
        status = "Menor de idade"
        print("Acesso restrito.")
    return status
```

### Comentários e Docstrings
- **Comentários de linha única**: Iniciados pelo caractere `#`.
- **Docstrings**: Strings multilinha delimitadas por três aspas duplas `"""` ou simples `'''`, utilizadas para documentar módulos, classes e funções.

```python
def calcular_media(valores):
    """Calcula a média aritmética de uma lista de números.
    
    Parâmetros:
        valores (list): Lista de números inteiros ou flutuantes.
        
    Retorna:
        float: Média aritmética calculada.
    """
    return sum(valores) / len(valores) if valores else 0.0
```

---

## 2. Tipos de Dados Primitivos e Operadores

O Python trata todos os valores como objetos. Os tipos primitivos nativos e seus respectivos operadores determinam a alocação e manipulação de memória.

### Tipos Primitivos Integrados
- `int`: Números inteiros de precisão arbitrária (ex: `42`, `-1000`).
- `float`: Números em ponto flutuante de precisão dupla (ex: `3.14159`, `2.5e-3`).
- `complex`: Números complexos contendo parte real e imaginária (ex: `3 + 4j`).
- `bool`: Valores booleanos (`True` ou `False`), sub-tipo de inteiro.
- `str`: Sequência imutável de caracteres Unicode (ex: `"Python"`, `'Código'`).
- `bytes` / `bytearray`: Sequências de bytes imutáveis e mutáveis para dados binários.
- `NoneType`: Representado pelo literal `None`, indicando a ausência de valor.

### Tabela de Operadores Matemáticos, Lógicos e Comparativos

O quadro a seguir resume os operadores nativos suportados pela linguagem.

| Categoria | Operador | Descrição | Exemplo | Resultado |
| :--- | :--- | :--- | :--- | :--- |
| Aritmético | `+` | Adição / Concatenação | `10 + 5` | `15` |
| Aritmético | `-` | Subtração | `10 - 5` | `5` |
| Aritmético | `*` | Multiplicação / Repetição | `3 * 4` | `12` |
| Aritmético | `/` | Divisão real (retorna float) | `7 / 2` | `3.5` |
| Aritmético | `//` | Divisão inteira (piso) | `7 // 2` | `3` |
| Aritmético | `%` | Módulo (resto da divisão) | `7 % 2` | `1` |
| Aritmético | `**` | Exponenciação | `2 ** 3` | `8` |
| Relacional | `==` | Igualdade de valor | `5 == 5` | `True` |
| Relacional | `!=` | Diferença de valor | `5 != 3` | `True` |
| Relacional | `>`, `<`, `>=`, `<=` | Comparações relacionais | `10 >= 5` | `True` |
| Identidade | `is`, `is not` | Comparação de identidade de objeto (endereço de memória) | `a is None` | `True` / `False` |
| Pertencimento | `in`, `not in` | Verificação de elemento em sequência/coleção | `"py" in "python"` | `True` |
| Lógico | `and`, `or`, `not` | Conjunção, disjunção e negação lógica | `True and False` | `False` |

---

## 3. Estruturas de Controle de Fluxo

As estruturas de controle de fluxo direcionam a execução de um programa Python com base em avaliações condicionais ou iterações.

### Instruções Condicionais (`if`, `elif`, `else`)

```python
nota = 85

if nota >= 90:
    conceito = "A"
elif nota >= 80:
    conceito = "B"
elif nota >= 70:
    conceito = "C"
else:
    conceito = "F"
```

### Correspondência de Padrões (`match...case`)
Introduzido no Python 3.10 (PEP 634/636), a instrução `match...case` permite a correspondência estrutural de padrões de forma expressiva.

```python
comando = "MOVER_DIREITA"

match comando.split("_"):
    case ["MOVER", direcao]:
        print(f"Movendo para: {direcao}")
    case ["PARAR"]:
        print("Parando execução.")
    case _:
        print("Comando não reconhecido.")
```

### Estruturas de Repetição (`for` e `while`)

O laço `for` itera sobre qualquer objeto iterável (listas, tuplas, dicionários, geradores), enquanto o `while` executa até que a condição seja falsa.

```python
# Iteração com for e range()
for i in range(1, 6):
    print(f"Contagem: {i}")

# Iteração com while
contador = 0
while contador < 3:
    print(f"Passo: {contador}")
    contador += 1
```

### Instruções de Desvio (`break`, `continue`, `pass` e `else` em laços)
- `break`: Interrompe imediatamente o laço de repetição.
- `continue`: Pula a iteração atual e avança para a próxima.
- `pass`: Instrução nula (*placeholder*) utilizada quando a sintaxe exige um comando.
- `else` no laço: Bloco executado apenas se o laço terminar sem interrupção por `break`.

```python
# Exemplo de busca com instrução else no laço for
busca = 7
numeros = [1, 3, 5, 9, 11]

for n in numeros:
    if n == busca:
        print("Número encontrado!")
        break
else:
    print("Número não encontrado na coleção.")
```

---

## 4. Coleções Integradas e Comprehensions

O Python fornece quatro estruturas de dados nativas fundamentais para o armazenamento de coleções.

### 1. Listas (`list`)
Coleções ordenadas, mutáveis e que permitem elementos duplicados.

```python
frutas = ["maçã", "banana", "laranja"]
frutas.append("uva")          # Adiciona ao final
frutas.insert(1, "abacaxi")    # Insere na posição 1
removido = frutas.pop()       # Remove e retorna o último elemento
frutas.sort()                 # Ordena in-place
```

### 2. Tuplas (`tuple`)
Coleções ordenadas e imutáveis. Ideais para dados estruturados e desempacotamento.

```python
ponto = (10, 20, 30)
x, y, z = ponto  # Desempacotamento de tupla
```

### 3. Dicionários (`dict`)
Coleções mutáveis de pares chave-valor indexados por chaves exclusivas.

```python
usuario = {"nome": "Maria", "idade": 30, "cargo": "Engenheira"}
nome = usuario.get("nome", "Desconhecido")  # Acesso seguro
usuario["email"] = "maria@example.com"      # Atribuição/atualização

for chave, valor in usuario.items():
    print(f"{chave}: {valor}")
```

### 4. Conjuntos (`set`)
Coleções não ordenadas de elementos únicos. Suportam operações matemáticas de teoria dos conjuntos.

```python
conjunto_a = {1, 2, 3, 4}
conjunto_b = {3, 4, 5, 6}

uniao = conjunto_a | conjunto_b          # {1, 2, 3, 4, 5, 6}
interseccao = conjunto_a & conjunto_b    # {3, 4}
diferenca = conjunto_a - conjunto_b      # {1, 2}
```

### Comprehensions (Expressões de Compreensão)
As *comprehensions* oferecem uma sintaxe concisa para criar coleções a partir de iteráveis.

```python
# List comprehension
quadrados = [x**2 for x in range(10) if x % 2 == 0]

# Dict comprehension
quadrados_dict = {x: x**2 for x in range(5)}

# Set comprehension
letras_unicas = {char.upper() for char in "abracadabra"}
```

---

## 5. Funções, Parâmetros e Escopo

As funções são blocos reutilizáveis de código definidos pela palavra-chave `def`.

### Assinatura e Argumentos (`*args` e `**kwargs`)

```python
def processar_dados(nome, *args, modo="padrao", **kwargs):
    """
    *args: Captura argumentos posicionais extras em uma tupla.
    **kwargs: Captura argumentos nomeados extras em um dicionário.
    """
    print(f"Nome: {nome}, Modo: {modo}")
    print(f"Posicionais extras: {args}")
    print(f"Nomeados extras: {kwargs}")

processar_dados("Dataset1", 10, 20, modo="avancado", autor="Ana", versao=2.0)
```

### Funções Anônimas (`lambda`) e Geradores (`yield`)
- **Expressões `lambda`**: Funções pequenas e anônimas contendo apenas uma expressão.
- **Geradores (`yield`)**: Funções que mantêm estado e produzem uma sequência de valores sob demanda, economizando memória.

```python
# Lambda
somar = lambda a, b: a + b

# Gerador
def gerador_fibonacci(limite):
    a, b = 0, 1
    for _ in range(limite):
        yield a
        a, b = b, a + b

for num in gerador_fibonacci(5):
    print(num)
```

### Regra de Escopo LEGB e Instruções `global` / `nonlocal`
O Python busca variáveis seguindo a ordem **LEGB**: Local, Enclosing (funções aninhadas), Global e Built-in.

```python
x = "Global"

def funcao_externa():
    x = "Enclosing"
    def funcao_interna():
        nonlocal x
        x = "Modificado no Enclosing"
    funcao_interna()
    print(x)  # Exibe "Modificado no Enclosing"
```

---

## 6. Catálogo de Funções Integradas (Built-in Functions)

O Python inclui mais de 60 funções integradas acessíveis sem a necessidade de importar módulos. A tabela abaixo cataloga as principais funções de uso contínuo.

| Função | Sintaxe / Assinatura | Descrição Operacional |
| :--- | :--- | :--- |
| `print()` | `print(*objects, sep=' ', end='\n')` | Imprime objetos na saída padrão (stdout). |
| `len()` | `len(s)` | Retorna o número de itens de uma sequência ou coleção. |
| `range()` | `range(start, stop[, step])` | Gera uma sequência imutável de números inteiros. |
| `type()` | `type(object)` | Retorna o tipo do objeto passado como argumento. |
| `isinstance()`| `isinstance(object, classinfo)` | Verifica se um objeto é instância de uma classe ou tupla de classes. |
| `enumerate()` | `enumerate(iterable, start=0)` | Retorna um iterador de tuplas contendo índice e valor. |
| `zip()` | `zip(*iterables)` | Agrupa elementos correspondentes de múltiplos iteráveis em tuplas. |
| `map()` | `map(function, iterable)` | Aplica uma função a todos os itens de um iterável. |
| `filter()` | `filter(function, iterable)` | Filtra elementos de um iterável onde a função retorna `True`. |
| `sorted()` | `sorted(iterable, key=None, reverse=False)` | Retorna uma nova lista ordenada a partir do iterável. |
| `sum()` | `sum(iterable, start=0)` | Soma os elementos de um iterável numérico. |
| `min()` / `max()`| `min(arg1, arg2, ...)` | Retorna o menor ou maior elemento. |
| `open()` | `open(file, mode='r', encoding=None)` | Abre um arquivo e retorna o objeto de arquivo correspondente. |
| `any()` / `all()`| `any(iterable)` / `all(iterable)` | Avalia se algum ou todos os elementos do iterável são verdadeiros. |
| `dir()` | `dir([object])` | Retorna a lista de atributos e métodos válidos do objeto. |

---

## 7. Programação Orientada a Objetos (POO)

O Python oferece suporte robusto à Orientação a Objetos, permitindo o encapsulamento de estado e comportamento em classes.

### Classes, Atributos e Métodos

```python
class ContaBancaria:
    # Atributo de classe (compartilhado por todas as instâncias)
    banco = "Banco Central"

    def __init__(self, titular: str, saldo_inicial: float = 0.0):
        # Atributos de instância
        self.titular = titular
        self._saldo = saldo_inicial  # Atributo protegido por convenção

    def depositar(self, valor: float) -> None:
        if valor > 0:
            self._saldo += valor

    @property
    def saldo(self) -> float:
        """Getter para acesso controlado ao saldo."""
        return self._saldo

    @classmethod
    def criar_com_bonus(cls, titular: str):
        """Método de classe funcionando como construtor alternativo."""
        return cls(titular, saldo_inicial=100.0)

    @staticmethod
    def e_valor_valido(valor: float) -> bool:
        """Método estático utilitário sem acesso ao self ou cls."""
        return valor > 0
```

### Herança e Polimorfismo

```python
class Animal:
    def __init__(self, nome: str):
        self.nome = nome

    def emitir_som(self) -> str:
        raise NotImplementedError("Subclasses devem implementar este método.")

class Cachorro(Animal):
    def emitir_som(self) -> str:
        return f"{self.nome} diz: Au Au!"

# Uso polimórfico
pets = [Cachorro("Rex"), Cachorro("Bob")]
for pet in pets:
    print(pet.emitir_som())
```

### Métodos Especiais (Dunder Methods)
Métodos iniciados e terminados com duplo sublinhado (`__`) definem comportamentos especiais para operadores e funções integradas.

```python
class Livro:
    def __init__(self, titulo: str, paginas: int):
        self.titulo = titulo
        self.paginas = paginas

    def __str__(self) -> str:
        return f"'{self.titulo}' ({self.paginas} págs.)"

    def __repr__(self) -> str:
        return f"Livro(titulo='{self.titulo}', paginas={self.paginas})"

    def __len__(self) -> int:
        return self.paginas

    def __eq__(self, outro) -> bool:
        return isinstance(outro, Livro) and self.paginas == outro.paginas
```

---

## 8. Tratamento de Exceções e Erros

O tratamento de exceções permite a gestão graciosa de falhas durante o tempo de execução.

### Bloco `try...except...else...finally`

```python
try:
    arquivo = open("dados.txt", "r")
    conteudo = arquivo.read()
    numero = int(conteudo.strip())
    resultado = 100 / numero
except FileNotFoundError:
    print("Erro: O arquivo não foi encontrado.")
except ValueError:
    print("Erro: O conteúdo do arquivo não é um inteiro válido.")
except ZeroDivisionError:
    print("Erro: Divisão por zero não permitida.")
else:
    # Executado somente se NENHUMA exceção ocorrer no bloco try
    print(f"Cálculo realizado com sucesso: {resultado}")
finally:
    # Executado SEMPRE, ocorrendo erro ou não (limpeza de recursos)
    print("Finalizando operação.")
```

### Exceções Customizadas

```python
class SaldoInsuficienteError(Exception):
    """Exceção lançada quando uma operação de saque excede o saldo."""
    def __init__(self, saldo_atual: float, valor_solicitado: float):
        super().__init__(f"Saldo de R${saldo_atual:.2f} é insuficiente para o saque de R${valor_solicitado:.2f}.")
        self.saldo_atual = saldo_atual
        self.valor_solicitado = valor_solicitado

# Disparando a exceção
def sacar(saldo, valor):
    if valor > saldo:
        raise SaldoInsuficienteError(saldo, valor)
    return saldo - valor
```

---

## 9. Manipulação de Arquivos e Gerenciadores de Contexto

A abertura e manipulação de arquivos deve ser feita preferencialmente com o protocolo de gerenciamento de contexto (`with`), garantindo o fechamento automático de descritores.

### Modos de Abertura de Arquivos
- `'r'`: Leitura (padrão).
- `'w'`: Escrita (sobrescreve o arquivo existente).
- `'a'`: Escrita no final (*append*).
- `'b'`: Modo binário (ex: `'rb'`, `'wb'`).
- `'+'`: Atualização (leitura e escrita).

```python
# Escrita de arquivo de texto
with open("exemplo.txt", "w", encoding="utf-8") as file:
    file.write("Linha 1: Introdução ao Python\n")
    file.write("Linha 2: Manipulação de Arquivos\n")

# Leitura iterativa
with open("exemplo.txt", "r", encoding="utf-8") as file:
    for linha in file:
        print(linha.strip())
```

---

## 10. Módulos Essenciais da Biblioteca Padrão

O Python possui uma filosofia conhecida como *"Batteries Included"* (baterias incluídas), oferecendo um conjunto robusto de módulos nativos.

| Módulo | Finalidade e Principais Recursos |
| :--- | :--- |
| `os` / `sys` | Interação com o sistema operacional, variáveis de ambiente, caminhos e argumentos de linha de comando (`sys.argv`). |
| `pathlib` | Manipulação orientada a objetos de caminhos do sistema de arquivos (`Path`). |
| `math` / `random` | Funções matemáticas avançadas (`trigonometria`, `logaritmos`) e geração de números pseudoaleatórios. |
| `datetime` | Manipulação de datas, horários e fusos horários (`datetime`, `date`, `timedelta`). |
| `json` / `csv` | Serialização e desserialização de formatos de troca de dados padrão JSON e CSV. |
| `re` | Expressões regulares para busca, validação e manipulação avançada de texto. |
| `collections` | Estruturas de dados especializadas (`Counter`, `defaultdict`, `namedtuple`, `deque`). |
| `itertools` / `functools` | Ferramentas para iteração eficiente (`chain`, `permutations`) e programação funcional (`higher-order functions`, `lru_cache`). |
| `typing` | Suporte a anotações de tipo estático (*type hints* como `List`, `Dict`, `Optional`, `Union`). |
