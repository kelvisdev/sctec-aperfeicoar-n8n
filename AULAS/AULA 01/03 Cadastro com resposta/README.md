# 03 Cadastro com resposta

Antes se chamava 003 Exemplo. Aqui, na aula 1, o webhook passou a responder para quem chamou.

## O que faz

Recebe um cadastro com nome e email por POST e devolve uma mensagem de confirmação em texto.

O Disparo de Gatilho aceita POST no caminho cadastro. O Respond dele está em Using Respond to Webhook Node, então quem responde é o último nó. O Allowed Origins com * deixa uma página da internet chamar o fluxo.

O Declarar Variaveis guarda o nome que veio no corpo em pessoa.nome.

O Resposta do Gatilho monta o texto. O nome sai em maiúsculas com toUpperCase. O email não passou pelo Declarar Variaveis, então a expressão busca direto no primeiro nó, pelo nome dele.

```
{{ $('Disparo de Gatilho').item.json.body.email }}
```

## Como testar

Importe, clique em Execute workflow e copie a Test URL do Disparo de Gatilho. Mande um POST pelo Insomnia, pelo Postman ou pelo terminal.

```bash
curl -X POST "COLE_A_TEST_URL_AQUI" -H "Content-Type: application/json" -d '{"nome":"Ana","email":"ana@exemplo.com"}'
```

A resposta volta com o nome em maiúsculas e o email que você mandou.

Também dá para mandar a chamada pelo [Postman](https://www.postman.com/downloads/), pelo [Insomnia](https://insomnia.rest/download) ou pelo [Thunder Client](https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client), uma extensão do VS Code. Use a Test URL depois de clicar em Execute workflow, ou a Production URL depois de publicar o fluxo.

## O que treinar

1. O texto da resposta tem um erro de digitação. Ache e corrija no Resposta do Gatilho.
2. Guarde o email também no Declarar Variaveis e troque a expressão da resposta para usar esse campo novo.

## Erros comuns

Mandar GET em vez de POST dá 404, porque o gatilho só escuta POST.

Se o nome sair vazio, confira se o campo no corpo se chama nome mesmo, tudo em minúsculas.

O nome dentro de $('...') tem que ser igual ao nome do nó, com espaço e maiúscula no mesmo lugar.
