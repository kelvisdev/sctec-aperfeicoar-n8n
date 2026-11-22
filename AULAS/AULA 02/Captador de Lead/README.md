# Captador de Lead

Fluxo da aula 2 para ver os erros mais comuns quando a página chama o webhook.

## O que faz

O Gatilho da Pagina Orbita recebe um POST no caminho captador-lead. O Respond dele ficou no padrão, Immediately, que responde na hora com Workflow was started.

O Responder a chamada devolve o texto AGORA FOI, mas está solto no canvas. Sem ligação com o gatilho, ele nunca roda.

## Como testar

Clique em Execute workflow, copie a Test URL do gatilho e mande um POST.

```bash
curl -X POST "COLE_A_TEST_URL_AQUI" -d "nome=Joca"
```

Do jeito que está, a resposta é Workflow was started.

Também dá para mandar a chamada pelo [Postman](https://www.postman.com/downloads/), pelo [Insomnia](https://insomnia.rest/download) ou pelo [Thunder Client](https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client), uma extensão do VS Code. Use a Test URL depois de clicar em Execute workflow, ou a Production URL depois de publicar o fluxo.

## O que treinar

1. Ligue o Responder a chamada depois do gatilho e troque o Respond do gatilho para Using Respond to Webhook Node. Agora a resposta é AGORA FOI.
2. Faça o caminho contrário. Deixe o Respond em Using Respond to Webhook Node e desligue o Responder a chamada. A chamada volta com erro 500 e, na execução, o n8n avisa que não achou o nó de resposta.
3. Publique o fluxo e repita com a Production URL. A execução não aparece no canvas, só na aba Executions.

## Erros comuns

Erro 500 é o Respond esperando um nó de resposta que não está ligado.

Erro 404 é a Test URL que já parou de escutar. Clique em Execute workflow de novo antes de mandar outra chamada.
