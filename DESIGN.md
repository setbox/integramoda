# Design Reference — Entire.io

Análise visual do site https://entire.io para uso como referência de design.

---

## Identidade Visual

**Filosofia:** Editorial minimalista. Swiss/International typographic style. Quase zero ornamento — todo o trabalho estético é feito por tipografia e espaçamento.

**Paleta:** Estritamente preto e branco. Sem cor de destaque.

| Token | Valor | Uso |
|---|---|---|
| `--color-bg` | `#FFFFFF` | Fundo de todas as páginas |
| `--color-text` | `#111111` | Texto primário |
| `--color-text-muted` | `#666666` | Texto secundário, subtítulos, datas |
| `--color-border` | `#E5E5E5` | Divisores, bordas sutis |
| `--color-btn-bg` | `#000000` | Botão primário (Sign in) |
| `--color-btn-text` | `#FFFFFF` | Texto do botão primário |
| `--color-status-ok` | `#22C55E` | Dot "Operational" no footer |

Única exceção à monocromia: logos de investidores (cores originais de cada marca).

---

## Tipografia

**Font stack:** Sans-serif geométrica clean — aparência muito próxima de **Inter** ou **Geist**. Sem serifa em nenhum elemento, exceto datas que usam variante tabular/monospace.

### Escala

| Nível | Tamanho | Peso | Uso |
|---|---|---|---|
| Display | ~52–60px | 700–800 | H1 de páginas principais ("Newsroom", "Blog") |
| H2 | ~32–36px | 700 | Títulos de seção ("Latest", "Archive", "Naming") |
| H3 | ~20–22px | 600–700 | Título de post/artigo em lista |
| Body | ~15–16px | 400 | Parágrafos, descrições |
| Small / Meta | ~13px | 400 | Datas, labels de seção, copyright |
| Nav | ~14px | 400–500 | Links de navegação |
| Caption | ~12px | 400 | Legendas, sublinks no footer |

### Datas

Datas de posts usam **fonte monospace ou numerais tabulares**: `10 Feb 2026`. Cor `--color-text-muted`. Uppercase para abreviação do mês, separação visual clara do título.

---

## Layout e Grid

**Max width:** ~760px para conteúdo de texto (blog, newsroom, brand). Páginas com grid de time/investors: ~1100px.

**Alinhamento:** Conteúdo centrado com `margin: auto`. Sem layout de duas colunas no conteúdo principal — foco em leiturabilidade single-column.

**Padding horizontal:** ~24px mobile, ~48px tablet, ~auto desktop (centralizado no max-width).

---

## Espaçamento Vertical

Sistema generoso — o "ar" é parte do design.

| Contexto | Valor |
|---|---|
| Entre seções principais | 80–120px |
| Entre H1 e primeiro parágrafo | 24–32px |
| Entre parágrafos | 20–24px |
| Entre itens de lista (blog/news) | 48–64px |
| Entre H2 e conteúdo da seção | 16–20px |
| Padding top da página (abaixo da nav) | 64–80px |
| Padding bottom da página (acima do footer) | 80–120px |

---

## Componentes

### Navbar

```
[Logo + "Entire"]          [Company]  [Vision]  [Blog]  [Sign in ▼]
```

- Posição: sticky top, fundo branco
- Altura: ~52–56px
- Logo: ícone abstrato (~20px) + texto "Entire" em peso semibold
- Links: texto plain, sem underline, hover implícito
- Botão "Sign in": fundo preto, texto branco, `border-radius: 6–8px`, padding `8px 16px`, sem shadow

### Botão Primário

```css
background: #000;
color: #fff;
border-radius: 6px;
padding: 8px 18px;
font-size: 14px;
font-weight: 500;
border: none;
```

### Botão Outline / Download

```css
background: #000;   /* Download Brand Assets usa fundo preto também */
color: #fff;
border-radius: 6px;
padding: 10px 20px;
font-size: 14px;
width: 100%;        /* Ocupa a coluna inteira no contexto brand */
```

### Divisor de Seção

Linha `<hr>` ou `border-top: 1px solid #E5E5E5`. Sem margem decorativa extra além do espaçamento padrão.

### Lista de Posts (Blog / Newsroom)

```
[Data mono muted]
[Título bold 20px]
[Excerpt muted 15px, max 2 linhas]
─────────────────────────────────
```

- Sem imagem/thumbnail
- Sem card/box/shadow — apenas texto com separador horizontal
- Tag colorida abaixo do título (ex: `Changelog`, `Dispatch`) — pill pequena, fundo levemente cinza ou colorido conforme categoria

### Tags / Pills

Aparece em posts do blog. Pequenas, ~11–12px, `border-radius: 999px`, padding `2px 8px`. Cores variam por categoria mas sempre discretas (ex: cinza claro, ou cor de baixo contraste).

### Footer

4 colunas: **Product | Company | Legal | Connect**

```
[Logo]                  Product    Company    Legal      Connect
Made with 🌿 on 🌎      CLI        Blog       Privacy    GitHub
© 2026 Entire Inc.      Docs       Vision     Cookie     Discord
● Operational                      Company    ToS        X
                                   Newsroom              Bluesky
                                   Brand                 LinkedIn
                                                         YouTube
```

- Fonte: ~13px, `--color-text-muted`
- Cabeçalhos de coluna: ~13px, peso 500–600, preto
- Status dot: verde `#22C55E`, ~8px, inline com "Operational"
- Separador topo: `border-top: 1px solid #E5E5E5`
- Padding vertical: ~48–64px

### Grid de Team / Investidores

- Time: grade de fotos em preto e branco, ~5–6 colunas, fotos quadradas com `border-radius: 0` ou mínimo
- Investidores: logos coloridos dos parceiros em linha horizontal, tamanhos normalizados por altura (~32–40px)

---

## Brand / Logo

**Regras oficiais (da página Brand):**

- Nome sempre "Entire" com E maiúsculo
- Manter clear space de no mínimo 25% da altura do símbolo
- Uso monocromático preferido
- Dois formatos: **Lockup** (símbolo + texto) e **Symbol** (só ícone)
- Ícone reservado para contextos muito pequenos (≤32px)
- Fundo escuro: versão branca. Fundo claro: versão preta
- Proibido: sombras, gradientes, distorção, rotação, fundo de baixo contraste

---

## Tom Visual Geral

- **Zero decoração:** sem gradientes, sem shadows, sem ilustrações, sem fotos de stock
- **Hierarquia por tamanho:** nenhum recurso de cor para hierarquia — só tamanho e peso
- **Densidade baixa:** uma ideia por bloco de conteúdo, muito espaço entre blocos
- **Confiança editorial:** o conteúdo fala sozinho — o design não grita
- **Acessibilidade implícita:** alto contraste preto/branco, sem dependência de cor para significado (exceto status dot)
