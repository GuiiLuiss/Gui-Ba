# Guilherme & Bárbara — Site do Casamento

Site one page, estático, para GitHub Pages. Estética editorial (preto, branco, cinzas e dourado fosco), com vídeo fullscreen, contagem regressiva, galeria e todas as seções do casamento.

## Estrutura

```
/
├── index.html
├── README.md
├── assets/
│   ├── css/style.css
│   ├── js/script.js
│   ├── img/         → fotos e logo (placeholders — substituir)
│   ├── video/        → vídeo do pré-wedding (adicionar pre-wedding.mp4)
│   ├── icons/         → favicon (placeholder — substituir)
│   └── fonts/         → não usado (fontes vêm do Google Fonts via CDN)
└── scripts/gerar-placeholders.ps1   → script usado só para gerar os placeholders locais
```

## O que falta substituir antes de publicar

Todos os arquivos abaixo estão hoje como **placeholders gerados automaticamente** (retângulos com o nome do arquivo) só para o site não quebrar durante o desenvolvimento. Troque cada um mantendo **o mesmo nome de arquivo**:

| Arquivo | Onde é usado | Recomendação |
|---|---|---|
| `assets/img/logo-gb.png` | Monograma na Home | Exportar o monograma GB oficial (o mesmo enviado por vocês) em PNG com fundo transparente, mín. 300×300px |
| `assets/icons/favicon.png` | Aba do navegador | Versão quadrada simplificada do monograma GB, 64×64px (ou 512×512px que o navegador redimensiona) |
| `assets/img/capa-compartilhamento.jpg` | Preview ao compartilhar o link no WhatsApp + poster do vídeo | 1200×630px, foto horizontal bonita do casal |
| `assets/img/foto-01.jpg` até `foto-07.jpg` | Seção "Nossa História" e Galeria | 6 a 8 fotos do pré-wedding, mescladando verticais/horizontais e coloridas/P&B, conforme já indicado no `index.html` |
| `assets/video/pre-wedding.mp4` | Vídeo fullscreen da Home | Vídeo curto (15–30s), **comprimido** (H.264, idealmente < 15MB), sem áudio necessário pois toca mudo |

> Dica de compressão de vídeo: exporte em 1080p, bitrate ~4-6 Mbps, ou use o HandBrake / `ffmpeg -i original.mp4 -vcodec h264 -crf 28 -an assets/video/pre-wedding.mp4`.

## Pontos já configurados

- **Contagem regressiva** até 29/11/2026 às 16h — some automaticamente após a data (ver `data-wedding-date` em `index.html`, seção `#contagem`).
- **Mapa** já embutido com o endereço do Espaço Aviv Eventos + botão "Ver no Google Maps".
- **Lista de presentes** já aponta para `https://casamento-guieba.listaideal.com.br/pt/`.
- **RSVP**: botão do WhatsApp está com `href="#"` e `aria-disabled="true"` — assim que a assessoria definir o número, edite o link em `index.html` (busque por `id="rsvpWhatsapp"`) para algo como:
  ```html
  <a class="btn btn--outline" href="https://wa.me/55XXXXXXXXXXX" target="_blank" rel="noopener">
  ```
- **Open Graph**: título, descrição e imagem de capa já configurados no `<head>` do `index.html`.

## Como publicar no GitHub Pages

1. Crie um repositório no GitHub (ex.: `guilherme-barbara-casamento`).
2. Suba todos os arquivos desta pasta para a branch `main`.
3. Em **Settings → Pages**, selecione a branch `main` e a pasta raiz (`/`).
4. O site ficará disponível em `https://SEU-USUARIO.github.io/NOME-DO-REPOSITORIO/`.
5. Se quiser um domínio próprio, configure em **Settings → Pages → Custom domain**.

## Testando localmente

Basta abrir o `index.html` num navegador, ou rodar um servidor local simples (recomendado para o vídeo/fetch funcionarem sem restrições de `file://`):

```powershell
# na pasta do projeto
python -m http.server 8000
# depois acesse http://localhost:8000
```
