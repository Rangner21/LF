# LF Transporte — Site Institucional

Site institucional de uma página (one-page) para a LF Transporte, empresa de
transporte rodoviário de cargas sediada em Jaboatão dos Guararapes (PE).

Construído em **HTML5, CSS3 e JavaScript puro**, sem frameworks, sem
back-end e sem banco de dados — pronto para publicação em GitHub Pages,
Vercel, Netlify ou qualquer hospedagem estática.

---

## 1. Estrutura do projeto

```
/
├── index.html
├── css/
│   └── style.css
├── js/
│   └── script.js
├── assets/
│   ├── images/     → reservado para fotografias reais (ver seção 4)
│   ├── icons/       → favicon.svg
│   └── videos/      → reservado para vídeo do hero, se desejado
├── robots.txt
├── sitemap.xml
└── README.md
```

Todas as seções do briefing estão implementadas como âncoras de uma mesma
página: Início, Quem Somos, Serviços, Área de Atuação, Segmentos,
Diferenciais, Parceiros, Galeria, FAQ, Blog, Trabalhe Conosco e Contato.

## 2. Como visualizar localmente

Não é necessário nenhum servidor especial. Basta abrir `index.html` no
navegador, ou, para simular melhor um ambiente de produção:

```bash
# Python
python3 -m http.server 8000

# Node
npx serve .
```

Depois acesse `http://localhost:8000`.

## 3. Como publicar

**GitHub Pages**
1. Suba o conteúdo desta pasta para um repositório.
2. Em *Settings → Pages*, selecione a branch principal e a pasta raiz (`/`).
3. O site ficará disponível em `https://<usuario>.github.io/<repositorio>/`.

**Vercel**
1. Importe o repositório em vercel.com (ou rode `vercel` na pasta do
   projeto).
2. Como é um site estático, nenhuma configuração de build é necessária —
   apenas confirme o *Output Directory* como a raiz do projeto.

## 4. Onde entrar com fotos e vídeo profissionais

O briefing pede fotografia profissional, que não pôde ser produzida nesta
entrega. Para manter o site com aparência premium mesmo sem fotos, o Hero,
a Galeria e o Blog usam **ilustrações vetoriais (SVG) desenhadas
especificamente para a marca** — não são um placeholder genérico quebrado,
mas uma solução visual funcional que já pode ir ao ar.

Quando as fotos estiverem disponíveis, troque os elementos ilustrados por
imagens reais:

| Local no site              | Onde adicionar o arquivo         | Tamanho sugerido |
|-----------------------------|-----------------------------------|-------------------|
| Hero (`.hero-art`)          | `assets/images/hero-caminhao.jpg` | 1600×1200px |
| Cards da Galeria             | `assets/images/galeria-01.jpg` a `05.jpg` | 1200×900px |
| Open Graph (compartilhamento em redes sociais) | `assets/images/og-image.jpg` | 1200×630px |
| Vídeo do Hero (opcional)     | `assets/videos/hero.mp4`          | até ~8s, com legenda/`muted` |

Basta trocar o bloco `<svg>...</svg>` correspondente por uma tag
`<img src="assets/images/arquivo.jpg" alt="...">` (ou `<video>`), mantendo
a classe do elemento para não perder o estilo já aplicado.

## 5. Personalização rápida

- **Número de WhatsApp**: definido em uma única constante no topo de
  `initQuoteForm()`, em `js/script.js` (`WHATSAPP_NUMBER`), e replicado nos
  links `href="https://wa.me/..."` do cabeçalho, do botão flutuante e da
  seção "Trabalhe Conosco". Atualize todas as ocorrências ao trocar o
  número.
- **Cores**: todas centralizadas em `:root` no topo de `css/style.css`
  (`--c-sinalizacao` = laranja, `--c-estrada` = azul institucional).
- **Textos**: todo o conteúdo está direto no `index.html`, sem CMS.

## 6. Formulário de orçamento

O formulário não usa back-end nem banco de dados. Ao ser enviado:

1. `event.preventDefault()` impede o recarregamento da página.
2. Todos os campos obrigatórios (Nome, Empresa, WhatsApp, Origem, Destino,
   Tipo de Carga) são validados; "Observações" é opcional.
3. Se algum campo obrigatório estiver vazio ou inválido, o envio é
   bloqueado e o campo é destacado — nenhuma mensagem vazia é enviada.
4. Com os dados válidos, a mensagem é montada automaticamente com
   `encodeURIComponent()` e o WhatsApp é aberto em **nova aba** via
   `window.open()`, sem alterar a URL nem rolar a página automaticamente.

## 7. QA realizado antes da entrega

- [x] Todos os links internos (`href="#..."`) apontam para IDs existentes.
- [x] Nenhum ID duplicado no HTML.
- [x] Tags HTML balanceadas (`section`, `div`, `form`, `ul`, `nav`, etc.).
- [x] JavaScript validado com `node --check` (sem erros de sintaxe).
- [x] Formulário: `preventDefault()`, validação de obrigatórios e abertura
      do WhatsApp em nova aba, sem reload e sem scroll indesejado.
- [x] Menu mobile funcional (abre/fecha, fecha ao clicar em um link).
- [x] `prefers-reduced-motion` respeitado nas animações.
- [x] Estados de foco visíveis (`:focus-visible`) para navegação por
      teclado.

Recomenda-se rodar o Lighthouse (Chrome DevTools) após a publicação, já com
as imagens reais adicionadas, para confirmar as notas de Performance,
Acessibilidade, Boas Práticas e SEO — o placeholder ilustrado em SVG e o
CSS/JS enxutos foram escritos com esse objetivo em mente.

## 8. Observações sobre o conteúdo

- Nenhum número, certificação ou parceiro foi inventado. Os diferenciais e
  dados institucionais usados (fundação em 2015, sede em Jaboatão dos
  Guararapes/PE, atuação nacional com foco no Nordeste) refletem apenas as
  informações fornecidas no briefing.
- A seção "Blog" está preparada como vitrine (com indicação "Em breve"),
  já que o projeto não inclui back-end/CMS para publicação de posts.
