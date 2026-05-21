# Edu-site

Site de apresentação do [Edu-app](https://github.com/FernandoNandoz/Edu-app) — plataforma educacional interativa para aprender algoritmos de escalonamento de processos, com narração em Nheengatu pelo assistente Kurumiwasú.

**Site:** https://araujoatila.github.io/edu-site/

## Stack

- HTML puro + Tailwind CSS via CDN
- JavaScript vanilla
- Sem build step, sem dependências npm

## Modos do site

O site possui dois modos controlados pela flag `COMING_SOON` no topo do `<script>` em `index.html`:

| Modo | Valor | O que exibe |
|---|---|---|
| Em breve | `true` | Badge "Em breve", sem links do repositório |
| Lançamento | `false` | Botão de download dinâmico + link do GitHub |

### Alternar entre os modos

Execute o script `toggle.sh` na raiz do projeto:

```bash
./toggle.sh
```

Ele detecta o modo atual, vira para o oposto, cria o commit e tenta o push. Se o push falhar por permissão SSH, rode manualmente em seguida:

```bash
git push
```

Após o push, o GitHub Actions faz o deploy automaticamente em alguns segundos.

### Alterar manualmente (opcional)

Abra `index.html` e edite a linha:

```js
const COMING_SOON = true; // true = em breve | false = download ativo
```

Depois commite e faça push:

```bash
git add index.html
git commit -m "release: ativa modo de download público"
git push
```

## Download dinâmico

Quando `COMING_SOON = false`, o botão de download consome a GitHub Releases API para sempre apontar para o instalador mais recente do Edu-app, com detecção automática do sistema operacional do usuário (`.exe`/`.msi` para Windows, `.deb` para Linux, `.dmg` para macOS).

## Desenvolvimento local

```bash
npx serve .
# ou
python3 -m http.server 8080
```

## Deploy

Hospedado via GitHub Pages com deploy automático ao fazer push na branch `main`.

## Repositório do app

O código-fonte do Edu-app está em [FernandoNandoz/Edu-app](https://github.com/FernandoNandoz/Edu-app). 

![alt text](image.png)
