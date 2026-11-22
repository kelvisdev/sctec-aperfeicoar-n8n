# 02 Webhook de boas-vindas

Antes se chamava 002 Exemplo. Foi o primeiro webhook da turma, na aula 1.

## O que faz

O Webhook Boas Vindas espera uma chamada GET no caminho cadastro. Tudo o que vier na URL, nos cabeçalhos ou no corpo chega no fluxo como dado e segue para o Normalizar.

O Normalizar é um Edit Fields que está vazio de propósito. É nele que você monta os seus campos.

## Como testar

1. Importe o arquivo e clique em Execute workflow. O n8n fica esperando a chamada.
2. Abra o Webhook Boas Vindas e copie a Test URL.
3. Cole no navegador e acrescente ?nome=Ana no fim do endereço.
4. Volte para o n8n e veja os dados que chegaram.

O que vem depois do ? na URL aparece dentro de query.

Também dá para mandar a chamada pelo [Postman](https://www.postman.com/downloads/), pelo [Insomnia](https://insomnia.rest/download) ou pelo [Thunder Client](https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client), uma extensão do VS Code. Use a Test URL depois de clicar em Execute workflow, ou a Production URL depois de publicar o fluxo.

## O que treinar

Crie no Normalizar um campo nome com o valor que veio na URL.

```
{{ $json.query.nome }}
```

Depois mande também ?nome=Ana&cidade=Joinville e crie um segundo campo para a cidade.

## Erros comuns

A Test URL escuta uma chamada só. Se o navegador mostrar 404, clique em Execute workflow de novo e recarregue a página.

A Production URL só funciona com o fluxo publicado. E a execução de produção não aparece no canvas, só na aba Executions.
