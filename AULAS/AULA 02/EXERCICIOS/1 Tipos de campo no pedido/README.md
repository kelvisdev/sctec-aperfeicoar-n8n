# Tipos de campo no pedido

Exercício 1 da aula 2. Usa os dados fixados e o tipo de cada campo no Edit Fields.

## O que faz

Uma papelaria recebe pedidos em que tudo chega como texto, até os números.

```json
{ "produto": "Caderno", "quantidade": "4", "preco": "12.50", "entregue": "sim" }
```

Para fazer conta e para filtrar depois, cada campo precisa do tipo certo. O fluxo de partida tem esse pedido fixado no Gatilho Manual e um Edit Fields vazio, o Converter Tipos.

## O que treinar

1. Importe o partida.json.
2. No Converter Tipos, crie produto como String.
3. Crie quantidade e preco como Number.
4. Crie total como Number, com a quantidade vezes o preço. Em expressão, a multiplicação é o *.
5. Crie entregue como Boolean. Colocar o sim direto dá erro, então pense numa comparação que devolva true ou false.

## Como testar

Clique em Execute workflow e abra o Converter Tipos. O total tem que dar 50 e o entregue tem que sair true.

Depois troque o entregue para nao nos dados fixados. O campo tem que sair false.

## Erros comuns

Preço com vírgula, como 12,50, não vira Number. O n8n só entende o ponto.

Um campo Boolean só aceita true ou false. Qualquer outra palavra dá erro de tipo.

Se o total sai vazio, confira se os nomes na expressão estão iguais aos dos dados fixados.

## Gabarito

Está em gabarito.json, nesta mesma pasta.
