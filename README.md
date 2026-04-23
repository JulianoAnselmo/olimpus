# Academia Olimpus — Site

Site institucional da Academia Olimpus (Taquaritinga-SP). HTML/CSS/JS puro, pronto para deploy no GitHub Pages.

## Estrutura

```
olimpus/
├── index.html          ← site principal (único HTML)
├── 404.html            ← página de erro customizada
├── imagens/            ← todas as imagens (logo, galeria, hero)
├── robots.txt          ← SEO
├── sitemap.xml         ← SEO
├── .nojekyll           ← desativa Jekyll no GitHub Pages
└── package.json        ← metadados + script `npm run dev`
```

## Integração com o Cardapio Admin

O site consome o documento `businessInfo` do Firestore (projeto `cardapio-admin-prod`), slug `academia-olimpus`:

```
restaurants/academia-olimpus/data/businessInfo
```

Campos atualizados dinamicamente (IDs do DOM):

| ID                     | Atualiza                                      |
|------------------------|-----------------------------------------------|
| `contact-address`      | Endereço completo (innerHTML com `<br>`)      |
| `contact-phone`        | Link `tel:` + texto do telefone               |
| `contact-hours`        | Horário de funcionamento                      |
| `contact-maps-link`    | Link "Traçar Rota no GPS"                     |
| `contactMap`           | Iframe do Google Maps embed                   |
| `wa-float-btn`         | Botão flutuante de WhatsApp                   |
| `.plan-wa-link` (class)| Botões "Consultar" / "Assinar Plano"          |
| `window.__OLIMPUS_BIZ` | Usado pelo modal de aula experimental         |

A integração roda em `file://` → desliga (mantém valores estáticos do HTML como fallback).

## Desenvolvimento local

```bash
npm run dev
# abre em http://localhost:8080
```

> Em `localhost`, a integração com o Firestore **funciona** (protocolo `http:`). Em `file:`, não.

## Deploy (GitHub Pages)

1. Push para `main`
2. Em Settings → Pages → Source: `main` / `(root)`
3. Aguarde ~1 min

Para domínio personalizado, crie o arquivo `CNAME` com o domínio e configure os registros A/CNAME no DNS.
