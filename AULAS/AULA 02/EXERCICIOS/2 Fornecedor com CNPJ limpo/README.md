# Fornecedor com CNPJ limpo

Exercício 2 da aula 2, adaptado do treino Cadastro de fornecedores. Usa o Edit Fields, o IF e a Data Table.

## O que faz

O setor de compras de uma empresa recebe pedidos de cadastro de fornecedores. Cada um escreve o nome e o CNPJ de um jeito. Antes de guardar, o nome precisa ficar padronizado e o CNPJ precisa ficar só com números. CNPJ sem 14 dígitos não entra na tabela.

O fluxo de partida tem dois fornecedores fixados no Gatilho Manual.

| empresa | cnpj | categoria |
|---|---|---|
| PAPELARIA boa vista | 11.222.333/0001-81 | Papelaria |
| limpa TUDO | 98.765.432/0001 | Limpeza |

Os dados são inventados. Depois do gatilho vêm o Limpar Dados (vazio), o IF CNPJ tem 14 digitos? (sem condição), o Guardar Fornecedor e o CNPJ invalido.

## Antes de começar

Crie no seu n8n uma Data Table chamada fornecedores com as colunas empresa, cnpj e categoria, todas como String. Depois abra o Guardar Fornecedor e escolha a sua tabela. O arquivo vem com o marcador CONFIGURAR_TABELA_FORNECEDORES no lugar dela.

## O que treinar

1. No Limpar Dados, deixe a empresa com a primeira letra de cada palavra em maiúscula.
2. Ainda no Limpar Dados, deixe o CNPJ só com números. A categoria passa como veio.
3. No IF, mande para a saída true só o CNPJ que tem 14 dígitos.

As expressões que arrumaram o nome e o WhatsApp na Orbita Labs v2 servem aqui. Para contar os caracteres de um texto, use .length.

## Como testar

Clique em Execute workflow. A Papelaria Boa Vista tem que ir para a tabela. A Limpa Tudo tem só 12 dígitos e tem que cair em CNPJ invalido.

Abra a tabela fornecedores e confira a linha nova, com o CNPJ 11222333000181.

## Erros comuns

Se o IF reclama do tipo, a comparação escolhida é de String. O .length devolve um número, então use a comparação de Number, is equal to.

Se o nome sai Papelaria boa vista, faltou o toLowerCase() antes do toTitleCase().

Se nada entra na tabela, confira se você escolheu a sua tabela no Guardar Fornecedor.

## Gabarito

Está em gabarito.json, nesta mesma pasta. No gabarito, a tabela também precisa ser escolhida.
