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
