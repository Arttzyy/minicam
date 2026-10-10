# 📁 MiniCam — Meus Uploads

Um site simples (um único `index.html`) que funciona como um **explorador de arquivos pessoal**,
hospedado de graça no **GitHub Pages**.

**A ideia:** você envia qualquer arquivo (imagens, textos, PDFs, vídeos, APKs… tudo) para a pasta
[`Uploads/`](Uploads/) deste repositório, abre o site no celular e vê/baixa tudo de lá — sem cabo,
sem app, sem nuvem de terceiros.

## ✨ O que o site faz

- 🗂️ Mostra todas as **pastas e arquivos** dentro de `Uploads/`, com navegação por breadcrumbs
- 🖼️ **Prévia em miniatura de todas as imagens** (jpg, png, gif, webp, svg…)
- ⬇️ **Botão de download ao lado de cada arquivo**
- 🔍 Busca por nome em todo o `Uploads/`
- 👆 Toque em um arquivo para abrir a prévia ampliada (imagem grande, texto, vídeo e áudio)
- 📱 Interface responsiva, feita para usar no celular

## 🚀 Como publicar (uma vez só)

1. No GitHub, abra este repositório → **Settings** → **Pages** (menu lateral).
2. Em **Build and deployment → Source**, escolha **Deploy from a branch**.
3. Em **Branch**, selecione `main` e a pasta `/ (root)` → **Save**.
4. Aguarde ~1 minuto. Seu site estará em:

   ```
   https://SEU-USUARIO.github.io/minicam/
   ```

> Se você mudou o nome do repositório ou o dono, não precisa alterar nada:
> o site detecta o usuário e o repositório automaticamente pela URL do Pages.

## 📤 Como enviar arquivos (do PC ou do celular)

1. Abra o repositório no GitHub → entre na pasta **`Uploads`**.
2. Clique em **Add file → Upload files** e arraste o que quiser (dá para criar subpastas).
3. Faça o **Commit**. Pronto: atualize o site e os arquivos aparecem.

Também funciona via `git`:

```bash
cp ~/minha-foto.jpg Uploads/Fotos/
git add Uploads && git commit -m "novas fotos" && git push
```

Limites do GitHub: até **100 MB por arquivo** e ~25 MB por upload feito pelo navegador.

## 📲 Como usar no celular

1. Abra o endereço do seu site no navegador do celular (adicione à tela inicial, se quiser).
2. Navegue pelas pastas, veja as prévias e toque no botão **⬇️** para baixar.

## ⚙️ Personalização

Tudo está no `CONFIG` no topo do `<script>` do [`index.html`](index.html):

```js
const CONFIG = {
  owner: "Arttzyy",   // seu usuário do GitHub (usado só como fallback)
  repo: "minicam",    // nome do repositório (usado só como fallback)
  branch: "main",     // branch onde está a pasta Uploads
  rootPath: "Uploads",// pasta exibida pelo site
  title: "Meus Uploads",
  githubToken: "",    // opcional (veja abaixo)
};
```

Também dá para apontar o site para outro repositório/pasta pela URL:
`https://SEU-USUARIO.github.io/minicam/?owner=fulano&repo=outro&path=MinhaPasta`

### Notas técnicas

- A listagem dos arquivos usa a **API pública do GitHub** (1 requisição por visita,
  limite de 60/hora por IP para uso anônimo — mais que suficiente para uso pessoal).
- Para repositório **privado** o Pages gratuito não serve o site; se quiser só aumentar o
  limite da API, preencha `githubToken` com um token de leitura.
- O arquivo `.nojekyll` garante que qualquer arquivo (inclusive com `_` no nome) seja servido.
- Arquivos ocultos (começando com `.`) não aparecem no site.

## 📂 Estrutura do repositório

```
├── index.html        ← o site inteiro (HTML + CSS + JS em um arquivo)
├── .nojekyll         ← garante que o Pages sirva todos os arquivos
└── Uploads/          ← COLOQUE SEUS ARQUIVOS AQUI
    ├── leiame.txt
    └── Exemplos/
        ├── imagem-exemplo.svg
        └── texto-exemplo.txt
```
