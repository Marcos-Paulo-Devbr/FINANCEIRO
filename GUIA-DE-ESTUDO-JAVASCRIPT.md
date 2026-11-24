# Guia de estudo: JavaScript do FinHub

Regra de ouro: **digite cada código, não cole**. Em cada etapa você aprende 1 ideia, faz 1 tarefa e confere no navegador (F12, aba Console).

## IDs que já existem no HTML (o JS vai usar)
`valor`, `badge`, `variacao`, `grafico-barras`, `barra-progresso`, `abas`, `area-chart`

---

## Etapa 1: Ligar o JS e falar com o navegador
**Conceitos:** `console.log`, `document.getElementById`, `textContent`
**Tarefa:** no `script.js`, mostre no console o texto do elemento `valor`. Depois troque esse texto para `R$ 5,99`.
**Pista:** `const el = document.getElementById("valor");`
**Deu certo quando:** o valor na tela muda ao recarregar.

## Etapa 2: Variáveis, objetos e listas
**Conceitos:** `const`/`let`, objeto `{}`, array `[]`
**Tarefa:** crie um objeto `dolar` com `preco`, `variacao` e uma lista `historico` com 28 números (as alturas das barras).
**Pista:** `const dolar = { preco: 5.42, variacao: 2.03 };`
**Deu certo quando:** `console.log(dolar.preco)` imprime 5.42.

## Etapa 3: Funções
**Conceitos:** `function`, parâmetros, `return`, template string
**Tarefa:** escreva `formatarReal(numero)` que devolve `R$ 5,42` (use `toLocaleString("pt-BR", { style: "currency", currency: "BRL" })`). Escreva também `formatarPercentual(n)` com seta ↗ ou ↘.
**Deu certo quando:** `formatarReal(1234.5)` devolve `R$ 1.234,50`.

## Etapa 4: Mostrar os dados na tela
**Conceitos:** função `renderizarResumo()`, `classList`, `if/else`
**Tarefa:** coloque `dolar.preco` em `#valor` e a variação em `#variacao`. Se a variação for negativa, troque a cor para vermelho adicionando uma classe `.queda` (crie essa classe no CSS).
**Deu certo quando:** mudando `variacao` para `-1.2` o texto fica vermelho.

## Etapa 5: Gerar as barras com laço
**Conceitos:** `for`/`forEach`/`map`, `createElement`, `appendChild`, `style.setProperty`
**Tarefa:** apague as `<i>` do `#grafico-barras` no HTML e gere uma barra para cada número de `historico`, definindo `--h`. As 8 últimas devem ter a classe `claro`.
**Pista:** `barra.style.setProperty("--h", valor + "%")`
**Deu certo quando:** o gráfico aparece igual ao de antes, vindo só do JS.

## Etapa 6: Eventos (as abas de ano)
**Conceitos:** `addEventListener`, `event.target`, `classList.remove/add`
**Tarefa:** ao clicar em uma aba, ela vira `.on` e as outras perdem a classe. Mostre o ano clicado no console.
**Deu certo quando:** o destaque verde acompanha o clique.

## Etapa 7: Atualizar a tela ao trocar de aba
**Conceitos:** objeto de dados por ano, reutilizar funções
**Tarefa:** guarde um `historico` diferente para cada ano e chame `renderizarBarras()` de novo ao clicar. Limpe o container antes (`innerHTML = ""`).
**Deu certo quando:** o gráfico muda a cada aba.

## Etapa 8: Buscar dados reais (API)
**Conceitos:** `fetch`, `async/await`, `response.json()`, `try/catch`, JSON
**Tarefa:** busque `https://economia.awesomeapi.com.br/json/last/USD-BRL` e leia `data.USDBRL.bid` e `data.USDBRL.pctChange`. Abra a URL no navegador primeiro para ver o formato. Troque `dolar.preco` e `dolar.variacao` pelos valores reais e chame `renderizarResumo()`.
**Cuidado:** os valores vêm como texto, use `parseFloat`.
**Deu certo quando:** o preço da tela bate com o do Google. Se der erro, leia a mensagem no Console e trate no `catch`.

## Etapa 9: Atualização automática
**Conceitos:** `setInterval`, não repetir código
**Tarefa:** rode `atualizar()` ao abrir a página e depois a cada 60 segundos. Mostre "Atualizado às HH:MM" usando `new Date().toLocaleTimeString("pt-BR")`.
**Deu certo quando:** o horário muda sozinho.

## Etapa 10: Conversor de moedas
**Conceitos:** `<input>`/`<select>` (crie no HTML), evento `input`, `parseFloat`, `isNaN`
**Tarefa:** crie o HTML do conversor (valor, de, para, resultado) e a API `https://open.er-api.com/v6/latest/USD`. Calcule `valor / taxaDe * taxaPara`. Adicione botão de inverter.
**Deu certo quando:** 100 USD vira o valor certo em BRL, e inverter funciona.

## Etapa 11: Memória do navegador (watchlist)
**Conceitos:** `localStorage.setItem/getItem`, `JSON.stringify/parse`, `try/catch`
**Tarefa:** deixe o usuário favoritar moedas e guarde a lista. Ao recarregar, ela volta.
**Deu certo quando:** os favoritos sobrevivem ao F5.

## Etapa 12: Gráfico de área com SVG
**Conceitos:** converter números em coordenadas, `setAttribute`, strings de `path`
**Tarefa:** a partir de uma lista de preços, calcule pontos `x,y` e monte o atributo `d` de um `<path>` dentro de `#area-chart`.
**Dica:** `x = i / (n - 1) * 300` e `y = 120 - (valor - min) / (max - min) * 100`.

## Etapa 13: Desafios finais
1. Tema claro/escuro com botão e `localStorage`.
2. Seção de notícias com filtros por categoria.
3. Busca rápida com Ctrl+K (`keydown`).
4. Simulador de investimento (juros compostos).
5. Alertas de preço usando seu n8n (webhook).

---

## Como estudar com o Chat do VS Code
Cole este prompt quando travar, trocando o trecho entre colchetes:

> Sou iniciante em JavaScript e estou montando um site financeiro com HTML, CSS e JS puros. Estou na etapa [número e nome]. Meu código atual é: [cole o código]. Explique linha por linha o que acontece e por que dá este erro: [cole o erro do Console]. NÃO reescreva o projeto: aponte só a linha com problema, explique a causa e me dê uma dica para eu corrigir sozinho.

## Rotina sugerida
- 1 etapa por dia (30 a 60 minutos).
- Ao terminar, escreva em 2 frases o que a etapa ensinou.
- Sempre teste com F12 aberto no Console.
