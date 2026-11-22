# Etiqueta do participante

Exercício 1 da aula 1. Usa o Gatilho Manual, os dados fixados e o Edit Fields.

## O que faz

Um evento precisa imprimir a etiqueta de cada participante. O cadastro chega com o nome todo em minúsculas, e a etiqueta tem que sair assim.

```
ANA SOUZA | Padaria Pão Quente
```

O fluxo de partida já tem o participante fixado no Gatilho Manual e um Edit Fields vazio, o Montar Etiqueta.

## O que treinar

1. Importe o partida.json.
2. Abra o Montar Etiqueta e crie um campo chamado etiqueta, do tipo String.
3. Arraste participante.nome do painel da esquerda para o valor. O n8n escreve a expressão para você.
4. Faça o mesmo com o sobrenome e a empresa, e coloque o | entre eles.
5. Acrescente o toUpperCase() no nome e no sobrenome.

## Como testar

Clique em Execute workflow e abra o Montar Etiqueta. A saída tem que mostrar a etiqueta igual à do exemplo.

Depois troque os dados fixados do gatilho por outro participante e rode de novo. A expressão continua a mesma.

## Erros comuns

O toUpperCase() sem os parênteses não funciona. Ele tem que vir colado no campo, assim.

```
{{ $json.participante.nome.toUpperCase() }}
```

Se a etiqueta sai com as chaves e tudo, o campo está em Fixed. Troque para Expression.

## Gabarito

Está em gabarito.json, nesta mesma pasta.
