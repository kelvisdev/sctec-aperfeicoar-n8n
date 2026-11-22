# 01 Montar nome completo

Antes se chamava 001 Exemplo. Foi o primeiro fluxo da aula 1.

## O que faz

Pega um aluno com nome e sobrenome e cria um campo novo, o nomecompleto, no formato Borges, Kelvis.

São dois nós. O Gatilho Manual começa o fluxo quando você clica em Execute workflow e já traz os dados do aluno fixados (pin). O Normalizar Dados é um Edit Fields que monta o campo com esta expressão.

```
{{ $json.aluno.sobrenome }}, {{ $json.aluno.nome }}
```

A vírgula e o espaço ficam fora das chaves, então saem do jeito que foram escritos.

## Como testar

Importe o arquivo, clique em Execute workflow e abra o Normalizar Dados. Na saída aparece o nome completo montado com os dados do gatilho.

## O que treinar

1. Troque o nome e o sobrenome nos dados fixados do gatilho e rode de novo. A expressão continua a mesma e o resultado muda.
2. Mude a expressão para sair Kelvis Borges, sem vírgula.
3. Acrescente um toUpperCase() para o sobrenome sair em maiúsculas.

## Erros comuns

Campo vazio na saída quase sempre é nome escrito diferente. Para o n8n, aluno.nome e Aluno.Nome são dois campos diferentes.

Antes de tirar o pin do gatilho, copie os dados fixados. Sem eles, o Normalizar Dados não tem aluno nenhum para ler.
