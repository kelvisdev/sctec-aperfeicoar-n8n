# Mensagem pela URL

Exercício 2 da aula 1. Usa o Webhook em GET e o Respond to Webhook.

## O que faz

Uma escola quer mandar um link para cada aluno novo. Quando o aluno abre o link, aparece uma mensagem com o nome dele e o nome do curso. Os dois vêm na própria URL.

```
?nome=Ana&curso=Excel
```

A resposta tem que ser.

```
Que bom ter você no curso de Excel, Ana!
```

O fluxo de partida tem o webhook Receber Visita, que escuta GET no caminho exercicio-mensagem, e o Responder Mensagem com um texto provisório.

## O que treinar

1. Importe o partida.json e clique em Execute workflow.
2. Copie a Test URL do Receber Visita, cole no navegador e acrescente ?nome=Ana&curso=Excel no fim.
3. Volte para o n8n e veja onde o nome e o curso chegaram.
4. No Responder Mensagem, troque o Response Body para Expression e monte a mensagem com os dois campos.

## Como testar

Clique em Execute workflow de novo e recarregue a página no navegador. A mensagem tem que aparecer na tela.

Teste com outro nome e outro curso, como ?nome=Bia&curso=Python.

Também dá para mandar a chamada pelo [Postman](https://www.postman.com/downloads/), pelo [Insomnia](https://insomnia.rest/download) ou pelo [Thunder Client](https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client), uma extensão do VS Code. Use a Test URL depois de clicar em Execute workflow, ou a Production URL depois de publicar o fluxo.

## Erros comuns

Se o navegador mostrar 404, a Test URL parou de escutar. Clique em Execute workflow antes de recarregar.

Se a mensagem sai com as chaves e tudo, o Response Body ainda está em Fixed.

## Gabarito

Está em gabarito.json, nesta mesma pasta. Ele escuta no caminho exercicio-mensagem-gabarito, para não brigar com o seu.
