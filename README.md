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

