# Orbita Labs v1

Primeira versão do projeto da Orbita Labs, montada na aula 1.

## O que faz

A página da campanha manda o pedido do cliente para o n8n e o fluxo responde na hora, agradecendo pelo nome.

O Disparo de Gatilho recebe o pedido por POST no caminho senai-orbita-v1. O Allowed Origins com * deixa o formulário do site falar com o n8n.

O Declarar Variaveis separa o campo nome que veio no corpo.

O Resposta do Gatilho devolve o texto com esta expressão.

```
{{ 'Recebemos seu pedido, ' + String($json.nome ?? '').trim() + '!' }}
```

O ?? troca o nome que não veio por um texto vazio, e o fluxo não quebra. O String garante que o valor vire texto. O trim tira os espaços do começo e do fim.

## Como testar

Importe, clique em Execute workflow e copie a Test URL do Disparo de Gatilho. Mande um POST com o nome no corpo.

```bash
curl -X POST "COLE_A_TEST_URL_AQUI" -H "Content-Type: application/json" -d '{"nome":"  Ana  "}'
```

A resposta tem que chegar como Recebemos seu pedido, Ana! sem os espaços extras.

Também dá para mandar a chamada pelo [Postman](https://www.postman.com/downloads/), pelo [Insomnia](https://insomnia.rest/download) ou pelo [Thunder Client](https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client), uma extensão do VS Code. Use a Test URL depois de clicar em Execute workflow, ou a Production URL depois de publicar o fluxo.

## O que treinar

1. Mande o pedido sem o campo nome e veja o que volta.
2. Mude o texto da resposta para incluir o nome da empresa, Orbita Labs.

## Erros comuns

Se a página fica sem resposta, confira o Allowed Origins do gatilho. Sem o * o navegador bloqueia a chamada.

A Orbita Labs v1 teste usa o mesmo caminho. Só uma das duas pode ficar publicada.
