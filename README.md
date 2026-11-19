# Elas mudaram a ciência e a computação

Quiz para totem da **Semana Nacional de Ciência e Tecnologia 2026**, do programa **Computadores para Inclusão** (Ministério das Comunicações). Tema: mulheres na ciência e na computação, mais o que o programa faz.

O público são crianças e adultos que passam pelo estande. A pessoa lê a linha do tempo, responde 6 perguntas e ganha carimbos e brindes conforme os acertos.

> Jogo em um único arquivo HTML, com fontes e imagens embutidas. Interface em português (pt-BR). Não depende de bibliotecas nem de CDN.

## Como é uma partida (3 a 5 minutos)

1. **Início**
2. **Regras**
3. **Linha do tempo**, com 9 paradas: Ada Lovelace, Marie Curie, Hedy Lamarr, Katherine Johnson, Sônia Guimarães e Jaqueline Goes de Jesus, mais 3 sobre o Computadores para Inclusão. É preciso passar por todas para liberar o botão **Jogar**.
4. **Quem vai jogar?** (crianças ou adultos)
5. **6 perguntas**
6. **Resultado**, com prêmio e vídeo da PCzinha

| Acertos | Resultado |
|---|---|
| 0 | "Quase lá", sem prêmio |
| 1 a 3 | Carimbinhos e, quem sabe, uma foto com a PCzinha |
| 4 a 6 | Carimbos e brindes (PC feliz). Para levar os brindes, a pessoa precisa votar: o QR code da votação aparece na tela |

O corte dos brindes fica na constante `ACERTOS_PARA_BRINDE`.

## Como rodar

- **No totem (sem internet):** deixe todos os arquivos na mesma pasta e abra `jogo-mulheres-na-ciencia.html` em tela cheia (F11) no Chrome ou Edge.
- **Online:** veja "Publicar no Cloudflare" abaixo. Hospedado, o jogo precisa de internet.

Funciona em **1920x1080** (totem deitado) e **1080x1920** (totem em pé). O layout muda sozinho.

## Estrutura

```
jogo-mulheres-na-ciencia.html   o jogo
perguntas.js                    todas as perguntas
fotos/                          fotos da linha do tempo
videos/                         pc-happy.mp4 e pc-sad.mp4
img/                            logos
```

### Fotos e vídeos

As fotos e os vídeos não vêm no código. Coloque-os com **exatamente** estes nomes:

| Arquivo | Pasta |
|---|---|
| `ada-lovelace.webp` | `fotos/` |
| `marie-curie.jpg` | `fotos/` |
| `hedy-lamarr.jpg` | `fotos/` |
| `katherine-johnson.webp` | `fotos/` |
| `sonia-guimaraes.jpg` | `fotos/` |
| `jaqueline-goes-de-jesus.png` | `fotos/` |
| `pc-happy.mp4` | `videos/` |
| `pc-sad.mp4` | `videos/` |

Sem as fotos, aparecem as iniciais de cada mulher. Sem os vídeos, a tela final fica sem vídeo. Os vídeos devem ser MP4 com **H.264** (HEVC não toca no Chrome) ou `.webm`.

## Perguntas

Ficam em `perguntas.js`, com 74 perguntas para crianças e 54 para adultos:

```js
window.PERGUNTAS = {
  criancas: [
    { p: "Pergunta?", r: ["A", "B", "C", "D"], c: 1, tema: "mulheres", e: "Explicação opcional." },
  ],
  adultos: [ /* ... */ ],
};
```

- `c` é a posição da alternativa certa (0 a 3). As alternativas são embaralhadas a cada pergunta.
- `tema` é `"mulheres"` ou `"cpi"`.
- Se mudar uma pergunta, confira se o texto da linha do tempo ainda traz a resposta.

### Rodadas

Cada rodada tem 6 perguntas. O jogo monta as rodadas sozinho, misturando os temas, e avança para a próxima a cada partida concluída. O número da rodada fica salvo no navegador do totem.

- **Novas rodadas:** acrescente perguntas no fim de cada lista. O jogo cria as rodadas novas sozinho.
- **Controle manual:** escreva `rodada: 1`, `rodada: 2`... nas perguntas. Quem tiver o campo é agrupado por esse número.
- **Painel da equipe:** segure o dedo no logo (canto superior esquerdo) por 2 segundos. Dá para escolher a rodada, voltar para a 1 e ver os contadores de partidas, carimbinhos e brindes.
- Abrir o jogo com `?rodada=3` no fim do endereço também escolhe a rodada.

## Configuração

No começo do script do HTML:

| Constante | O que faz |
|---|---|
| `PERGUNTAS_POR_PARTIDA` | Perguntas por rodada (6) |
| `ACERTOS_PARA_BRINDE` | A partir de quantos acertos ganha brindes (4) |
| `PREMIOS` | Textos de prêmio da tela final |
| `VOTACAO` | `exigir`, `onde` (nome da sala) e o QR code embutido |
| `PARADAS_PARA_LIBERAR` | Paradas a ver para liberar o Jogar (0 = todas) |
| `INATIVIDADE_SEGUNDOS` / `INATIVIDADE_CONTAGEM` | Tempo parado até avisar e contagem até voltar ao início |
| `MODO_LEVE` | `true` desliga desfoque e reduz efeitos, para computadores fracos (também vale `?leve` no endereço) |
| `LINHA_DO_TEMPO` | Conteúdo das paradas |

## Créditos

Programa Computadores para Inclusão, Ministério das Comunicações, Governo Federal. Conteúdo das perguntas: equipe do programa.
<span class="credito">Desenvolvido por: Victor A. Lêla © 2026</span>
