# Alerta de chuva na visita

Exercício 3 da aula 2, adaptado do treino Clima nas visitas técnicas. Usa o Edit Fields em modo JSON e o IF.

## O que faz

Uma empresa de manutenção agenda visitas de técnicos na casa dos clientes. Visita com chuva forte acaba remarcada em cima da hora. A regra é simples. Se a chance de chuva for de 70% ou mais, a visita é remarcada.

No treino completo a previsão vem de uma API de clima. Aqui ela já está digitada no Previsao de Amanha, um Edit Fields em modo JSON.

```json
{
  "cliente": "Oficina do Seu Jorge",
  "cidade": "Joinville",
  "data_visita": "2026-11-25",
  "chuva": 80,
  "vento": 20,
  "temperatura": 29
}
```

Depois dele vêm o IF Chuva forte? (sem condição) e dois nós No Operation, o Reagendar visita e o Visita mantida.

## O que treinar

1. Importe o partida.json e clique em Execute workflow para ver os dados.
2. No Chuva forte?, arraste a chuva para o primeiro campo da condição.
3. Escolha a comparação de Number is greater than or equal e digite 70.

## Como testar

Clique em Execute workflow. Com chuva 80, o item tem que passar pelo Reagendar visita.

Troque a chuva para 40 no Previsao de Amanha e rode de novo. Agora tem que passar pelo Visita mantida.

## Erros comuns

Se o IF reclama do tipo, a comparação escolhida é de String. A chuva está sem aspas no JSON, então chega como número.

Com is greater than, sem o or equal, uma chuva de exatamente 70 não remarca a visita.

## Desafio extra

Vento a partir de 50 km/h também remarca a visita, porque o técnico não pode subir no telhado. Acrescente uma segunda condição no mesmo IF e troque o AND por OR. Teste com chuva 40 e vento 60.

## Gabarito

Está em gabarito.json, nesta mesma pasta. O desafio extra não está no gabarito.
