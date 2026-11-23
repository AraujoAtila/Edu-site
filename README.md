# Edu-site

Site de apresentação do [Edu-app](https://github.com/araujoatila/Edu-app) — plataforma educacional interativa para aprender algoritmos de escalonamento de processos, com narração em Nheengatu pelo assistente Kurumimwasú.

![Captura de tela do site](/assets//img/image.png)

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
│   ├── img/                    # Logo, mascote e imagem de fundo
│   └── release/
│       └── Edu_2.2.1_x64-setup.exe   # Instalador do Edu-app (Git LFS)
├── .github/workflows/deploy.yml      # Deploy no GitHub Pages
├── .gitattributes              # Arquivos *.exe rastreados via Git LFS
└── image.png                   # Captura de tela usada neste README
```

## Seções da página

| Âncora | Conteúdo |
|---|---|
| `#inicio` | Hero com apresentação do Edu e botão **Baixar para Windows** |
| `#funcionalidades` | Cards com as funcionalidades do app (algoritmos interativos, narração em Nheengatu, aprendizado guiado, app desktop, conteúdo gratuito, bilíngue) |
| `#sobre` | Apresentação do mascote Kurumimwasú |

O botão do header ("Baixar agora") e os links do rodapé (autor e GitHub) são renderizados pela função `renderRelease()`, no `<script>` ao final do `index.html`.

## Download do instalador

O instalador do Windows é servido diretamente pelo próprio site, a partir de `assets/release/`. Arquivos `.exe` são versionados com **Git LFS**, então é preciso tê-lo instalado:

```bash
git lfs install
```

### Publicar uma nova versão do app

1. Copie o novo instalador para `assets/release/` (e remova o antigo, se quiser).
2. Atualize a constante `INSTALLER` no `<script>` ao final do `index.html`:

   ```js
   const INSTALLER = 'assets/release/Edu_2.2.1_x64-setup.exe';
   ```

   Os dois botões de download (hero e header) usam essa constante, e a versão exibida abaixo do botão é extraída do nome do arquivo (padrão `Edu_<versão>_...`).
3. Commite e faça push:

```bash
git add assets/release index.html
git commit -m "release: Edu x.y.z"
git push
```

## Desenvolvimento local

```bash
npx serve .
# ou
python3 -m http.server 8080
```

## Deploy

Hospedado via GitHub Pages. O workflow `.github/workflows/deploy.yml` faz o checkout com `lfs: true` (para publicar o instalador real, e não o ponteiro do LFS) e publica a raiz do repositório a cada push na branch `main` (também pode ser disparado manualmente em *Actions → Deploy to GitHub Pages → Run workflow*).

## Repositório do app

O código-fonte do Edu-app está em [araujoatila/Edu-app](https://github.com/araujoatila/Edu-app).
