# KDM Internet - Site Estático

Este repositório contém a landing page estática da KDM Internet. O site pode ser executado localmente ou implantado como um contêiner leve.

## Executar localmente

Como o site é estático, basta abrir o `index.html` em um navegador ou servir a pasta com qualquer servidor HTTP simples.

```bash
python -m http.server 8080
```

Acesse em `http://localhost:8080`.

## Deploy via Docker

Um `Dockerfile` foi adicionado para empacotar o site com Nginx.

### Build da imagem
```bash
docker build -t kdm-site .
```

### Subir localmente
```bash
docker run --rm -p 8080:80 kdm-site
```

Acesse `http://localhost:8080` para validar.

### Publicar
Envie a imagem para seu registry (ex.: Docker Hub ou GitHub Container Registry) e configure seu provedor (Kubernetes, VM, ou serviço de containers) para executar a imagem `kdm-site`, expondo a porta 80. Exemplo para Docker Hub:

```bash
docker tag kdm-site usuario/kdm-site:latest
docker push usuario/kdm-site:latest
```

## Deploy em provedores estáticos

Se preferir GitHub Pages, Netlify ou Vercel, basta publicar o `index.html` na raiz do site. Para GitHub Pages:

1. Crie a branch `gh-pages` contendo o `index.html`.
2. Ative Pages nas configurações do repositório apontando para `gh-pages`.
3. Aguarde a propagação e acesse o domínio gerado.
