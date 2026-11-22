# Conserte o webhook

Exercício 3 da aula 1. Usa o Webhook, o Edit Fields e o Respond to Webhook.

## O que faz

Este fluxo deveria confirmar a inscrição de um aluno numa turma. Ele recebe nome e turma por POST e responde assim.

```
Inscrição confirmada, Ana! Sua turma é a T1.
```

Só que ele tem 3 defeitos. Seu trabalho é achar e consertar os três.

## O que treinar

1. Importe o partida.json e clique em Execute workflow.
2. Copie a Test URL do Receber Inscricao e mande o POST abaixo.
3. Leia o que volta. Conserte, rode de novo e repita até a resposta sair certa.

```bash
curl -X POST "COLE_A_TEST_URL_AQUI" -H "Content-Type: application/json" -d '{"nome":"Ana","turma":"T1"}'
```

Pelo Insomnia funciona do mesmo jeito. Escolha POST, cole a Test URL e mande o corpo em JSON.

## Como testar

A cada conserto, clique em Execute workflow e mande o POST de novo. Abra cada nó e compare a entrada com a saída. O defeito costuma estar no primeiro nó em que a saída não é o que você esperava.

Também dá para mandar a chamada pelo [Postman](https://www.postman.com/downloads/), pelo [Insomnia](https://insomnia.rest/download) ou pelo [Thunder Client](https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client), uma extensão do VS Code. Use a Test URL depois de clicar em Execute workflow, ou a Production URL depois de publicar o fluxo.

## Erros comuns

Não pule a mensagem de erro. Ela já diz qual é o primeiro defeito.

Lembre onde cada coisa chega. O que vem na URL fica em query. O que vem no corpo de um POST fica em body.

## Gabarito

Está em gabarito.json, nesta mesma pasta, e a nota Leia primeiro dele lista os três consertos. Tente antes de abrir.
