Python Quiz
===========

Apareceu na minha timeline o seguinte [quiz](https://python-quiz.seznam.io).

Após responde-lo, decidi entender todos os comportamentos e compartilhar as explicações.

## 1 - O que o código abaixo irá reproduzir

```python
print(9 / 2, 9 // 2)
```

- [ ] 4.5 4

- [ ] 4.5 9

- [ ] 4 4

- [ ] 4 9

<details>
 <summary>Resposta e Explicação</summary>

A resposta é "4.5 4", pois a partir da versão 3 do Python, o operador de divisão agora retorna o resultado  como "float" e o operador "\\", o resultado truncado.

</details>

## 2 - O que o código abaixo irá reproduzir

```python
x = 1
print(++++x)
```

- [ ] 3

- [ ] 2

- [ ] 1

- [ ] raises SyntaxError

<details>
 <summary>Resposta e Explicação</summary>

A resposta é "1", pois em python não existe o operador unário "++". Essa expressão seria interpretada iniciando do "+" mais proximo de x, resultando em 1, que seria avaliado pelo proximo operador que também é um "+" e assim sucessivamente.

 Poderia fazer tambem uma mistura entre "+" e "-", e a avaliação seria como descrito acima. Exemplo: "++-1" seria avaliado como "-1" e "--+1" como "1".

</details>

## 3 - O que o código abaixo irá reproduzir

```python
x = None
try:
    print(int(x))
except ValueError, TypeError:
    print("Bad value")
```

- [ ] 0

- [ ] raises SyntaxError

- [ ] raises TypeError

- [ ] Bad value

<details>
 <summary>Resposta e Explicação</summary>

É uma pegadinha esta questão e a resposta correta é "raises Syntaxerror".

Na versão 3 do python quando queremos lidar com duas exceções que podem ocorrer, devemos utilizar uma tupla de expressões, então o código anterior deveria ser "except (ValueError, TypeError)".

Uma curiosidade é que caso o erro sintático seja corrigido, teremos o lançamento de TypeError, pois None não pode ser convertido em inteiro.

</details>

## 4 - O que o código abaixo irá reproduzir

```python
print(int(sum({
    1: 1,
    2: 2,
    1.0: 3,
})))
```

- [ ] 3

- [ ] 4

- [ ] 5

- [ ] 6

- [ ] raises ValueError

<details>
 <summary>Resposta e Explicação</summary>
Mais uma pegadinha. O método sum quando aplicado sobre um dicionário itera sobre suas chaves.

Porém nesta questão temo as chaves "1" e "1.0" que produzem o mesmo hash, logo o dicionário final produzido é "{1: 3, 2: 2}".

Logo a resposta correta é "3".
</details>

## 5 - O que o código abaixo irá reproduzir

```python
a = list(range(3))
b = a
c = a[:]
d = c[::-1]
a[-1], c[-1] = 4, 4

print(a[2], b[2], c[2], d[2])
```

- [ ] 4 2 4 0

- [ ] 4 4 4 0

- [ ] 4 2 2 2

- [ ] raises SyntaxError

- [ ] raises ValueError

<details>
<summary>Resposta e Explicação</summary>

Para entender este problema vamos fazer um "teste de mesa".

Após a execução da primeira linha temos a variável "a" com uma lista contendo os elementos "[0, 1, 2]".

Na atribuição "b = a", a variavel "b" não cria uma nova lista, apenas passa a indicar o endereço onde "a" já estava aramazenada.

Assim "a" e "b" estão indicando a mesma lista e a alteração de qualquer uma das duas variáveis é refletida na outra.

Na atribuição "c = a[:]", uma nova lista é criada com o mesmo conteúdo de a. Esta síntaxe é a de fatiamento, e normalmente passamos a posição inicial e final, por exemplo "[0:2]", que significa da posição 0 da lista até a 2. Quando omitido alguma das partes significa que vamos "a partir do começo" ou "até o final".

Neste ponto temos as variáveis "a", "b" e "c" com o mesmo conteúdo, porem somente "a" e "b" são as mesmas listas e isto pode ser verificado através da função "id" que retorna o endereço de memória daquela variável.

Executando o comando "id(a)", "id(b)" e "id(c) vemos que as duas primeiras apresentam o mesmo valor e a terceira um valor diferente.

A ultima atribuição é feita a variável "d", que recebe uma cópia de "a" porém invertida.

O fatiamento aceita um terceiro valor que indica o passo a dar, por exemplo "variavel[::2]", significa da primeira posição da lista até a ultima saltando de dois em dois(posição 0, 2, 4, 6...).

Então temos:

a = [0, 1, 2]
b = [0, 1, 2]
c = [0, 1, 2]
d = [2, 1, 0]

Na linha "a[-1], c[-1] = 4, 4" temos uma atrbuição multipla, ou seja "a[-1] = 4" e "c[-1] = 4". Posição -1 de uma lista significa o ultimo elemento, no nosso caso, a posição 2.

Quando modificamos "a", "b" também é alterada.

Então temos:

a = [0, 1, 4]
b = [0, 1, 4]
c = [0, 1, 4]
d = [2, 1, 0]

Então a resposta correta é "4 4 4 0".
</details>

## 6 - O que o código abaixo irá reproduzir

```python
class Foo(type):
    def ping(self):
        print("pong")

class Bar(metaclass=Foo):
    def pong(self):
        print("ping")

Bar().ping()
```

- [ ] pong

- [ ] raises SyntaxError

- [ ] raises AttributeError

- [ ] ping

<details>
 <summary>Resposta e Explicação</summary>
 A resposta correta é "raises AttributeError", isto porque Foo é metaclasse de Bar, não superclasse.

 Portanto não ocorre herança de seus métodos e atributos.

 Como é um tópico avançado sobre metaprogramação, recomendo assistir o [vídeo](https://youtu.be/JQBR8fUcd88) do canal Ignorância Zero que é bem didático sobre o assunto e em pt-br.
</details>

## 7 - O que o código abaixo irá reproduzir

```python
class Foo:
    x = 1

    def __int__(self):
        return self.x

class Bar:
    x = 2

    def __add__(self, y):
        return self.x + y

try:
    print(Bar() + 3)
    print(Foo() + 4)

except Exception:
    pass
```

- [ ] nothing

- [ ] 5

- [ ] 5 5

- [ ] 4 6

<details>
 <summary>Resposta e Explicação</summary>
A resposta correta é "5".

A instância de Bar implementa o método "__add__", somando x(2) ao valor do lado esquerdo do operador "+".

Já Foo não implementa esse método, o operador de adição não funciona para esta classe.

Uma curiosidade é que como Foo implementa "__int__", tenho a capacidade de fazer a conversão do objeto para inteiro, exemplo "int(Foo())" retornará "1".
</details>

## 8 - O que o código abaixo irá reproduzir

```python
x = "máma"
x[0], x[2] = ["t"] * 2
print(x)
```

- [ ] raises SyntaxError

- [ ] raises TypeError

- [ ] táta

- [ ] máma

<details>
 <summary>Resposta e Explicação</summary>

A resposta correta é "raises TypeError".

A variável x é do tipo str e é imutável, sendo assim uma exceção é lançada quando tentamos modificar o seu conteúdo.

Para realizar a alteração de uma string, devemos utilizar o método "replace" que irá criar uma nova string alterada.

</details>
