# Edu-site

Site de apresentação do [Edu-app](https://github.com/araujoatila/Edu-app) — plataforma educacional interativa para aprender algoritmos de escalonamento de processos, com narração em Nheengatu pelo assistente Kurumimwasú.

![Captura de tela do site](assets/img/image.png)

## Stack

- HTML puro + [Tailwind CSS](https://tailwindcss.com) via CDN (configuração inline no `<head>`)
- Fonte Poppins via Google Fonts
- JavaScript vanilla
- Sem build step, sem dependências npm

## Estrutura

```
.
├── index.html                  # Página única do site
├── assets/
│   └── img/                    # Logo, mascote, imagem de fundo e captura de tela do README
└── .github/workflows/deploy.yml      # Deploy no GitHub Pages
```

## Seções da página

| Âncora | Conteúdo |
|---|---|
| `#inicio` | Hero com apresentação do Edu e botão **Baixar para Windows** |
| `#funcionalidades` | Cards com as funcionalidades do app (algoritmos interativos, narração em Nheengatu, aprendizado guiado, app desktop, conteúdo gratuito, bilíngue) |
| `#sobre` | Apresentação do mascote Kurumimwasú |

O botão do header ("Baixar agora") e os links do rodapé (autor e GitHub) são renderizados pela função `renderRelease()`, no `<script>` ao final do `index.html`.

## Download do instalador

O instalador do Windows **não fica neste repositório**: ele é publicado como anexo nos [Releases](https://github.com/AraujoAtila/Edu-site/releases) do GitHub, e os botões do site apontam para lá. Assim o site continua leve (menos de 1 MB) e não é preciso usar Git LFS.

### Publicar uma nova versão do app

1. Crie um novo release em [Releases → Draft a new release](https://github.com/AraujoAtila/Edu-site/releases/new):
   - **Tag:** `vX.Y.Z` (ex.: `v2.3.0`)
   - **Título:** `Edu X.Y.Z`
   - Anexe o instalador `Edu_X.Y.Z_x64-setup.exe` e clique em **Publish release**.
2. Atualize a constante `INSTALLER` no `<script>` ao final do `index.html`, trocando a versão nos dois lugares (tag e nome do arquivo):

   ```js
   const INSTALLER = 'https://github.com/AraujoAtila/Edu-site/releases/download/v2.2.1/Edu_2.2.1_x64-setup.exe';
   ```

   Os dois botões de download (hero e header) usam essa constante, e a versão exibida abaixo do botão é extraída do nome do arquivo (padrão `Edu_<versão>_...`).
3. Commite e faça push:

```bash
git add index.html
git commit -m "release: Edu x.y.z"
git push
```

> Publique o release **antes** do push, senão o botão de download fica apontando para um arquivo que ainda não existe.

## Desenvolvimento local

```bash
npx serve .
# ou
python3 -m http.server 8080
```

## Deploy

Hospedado via GitHub Pages. O workflow `.github/workflows/deploy.yml` publica a raiz do repositório a cada push na branch `main` (também pode ser disparado manualmente em *Actions → Deploy to GitHub Pages → Run workflow*).

## Repositório do app

O código-fonte do Edu-app está em [araujoatila/Edu-app](https://github.com/araujoatila/Edu-app).
