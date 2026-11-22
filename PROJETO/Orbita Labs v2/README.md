# Orbita Labs v2

Segunda versão do projeto da Orbita Labs, montada na aula 2. Agora a página manda o formulário completo e cada pedido fica guardado numa tabela dentro do próprio n8n.

## O que faz

O Disparo de Gatilho recebe o pedido por POST no caminho orbita-v2. O Respond dele está em Using Respond to Webhook Node, então a resposta sai pelo último nó.

O Variveis (assim mesmo, sem o a, do jeito que a turma criou) tira cada campo de dentro do body. São nome, email, whatsapp, empresa, porte, area, prazo e consentimento, todos como String. O faturamento está como Number só para treinar o tipo do campo, porque a página não manda esse campo.

O Normalizar Dados arruma dois campos e repassa o resto como chegou.

```
{{ $json.nome.toLowerCase().toTitleCase() }}
{{ $json.whatsapp.replace(/\D/g, '') }}
```

A primeira deixa tudo em minúsculas e depois põe maiúscula na primeira letra de cada palavra, então MARIA borges vira Maria Borges. A segunda apaga tudo o que não é número, então (67) 99272-0990 vira 67992720990.

O Adicionar Lead é um nó Data Table que insere uma linha na tabela leads, com cada campo na sua coluna.

O Resposta do Gatilho devolve Recebemos seu pedido com o nome da pessoa.

## Antes de testar

Crie no seu n8n uma Data Table chamada leads com as colunas nome, email, whatsapp, empresa, porte, area, prazo e consentimento. Depois abra o Adicionar Lead e escolha a sua tabela. O arquivo vem com o marcador CONFIGURAR_TABELA_LEADS no lugar da tabela.

## Como testar

Clique em Execute workflow e copie a Test URL do Disparo de Gatilho. Abra a página da campanha com ?webhook= e a sua Test URL no fim do endereço, preencha o formulário e envie.

```
https://orbita-automacao-gratuita.lovable.app/?webhook=COLE_A_TEST_URL_AQUI
```

A página mostra Recebemos seu pedido com o nome arrumado, e a tabela leads ganha uma linha nova. Para testar sem a página, mande um POST pelo terminal.

```bash
curl -X POST "COLE_A_TEST_URL_AQUI" -d "nome=MARIA borges" -d "whatsapp=(67) 99272-0990" -d "email=maria@exemplo.com"
```

Também dá para mandar a chamada pelo [Postman](https://www.postman.com/downloads/), pelo [Insomnia](https://insomnia.rest/download) ou pelo [Thunder Client](https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client), uma extensão do VS Code. Use a Test URL depois de clicar em Execute workflow, ou a Production URL depois de publicar o fluxo.

## O que treinar

1. Mande o nome todo em maiúsculas e o WhatsApp com parênteses e traço. Abra o Normalizar Dados e compare a entrada com a saída.
2. Acrescente o trim() no nome para tirar os espaços que sobram.
3. Deixe o email em minúsculas com toLowerCase().

## Erros comuns

O pedido não chega na tabela quando o Adicionar Lead ainda não tem a sua tabela escolhida.

Um campo novo não aparece quando o gatilho está com dados fixados antigos. Tire o pin e mande o pedido de novo.

Se a página mostrar O fluxo respondeu 404, a Test URL parou de escutar. Clique em Execute workflow antes de enviar.

## Depois desta versão

Na aula 3 este fluxo ganha o trim, o email em minúsculas e um IF que responde de um jeito para quem deixou email e de outro para quem não deixou.
