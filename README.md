# Flow Agent — Landing Page

Landing page bilíngue (PT-BR / EN) para o **Flow Agent**, um Agente de IA humanizado construído com n8n para automação de atendimento via WhatsApp voltado a negócios de beleza e estética premium.

---

## Estrutura do projeto

```
/
└── index.html        # Arquivo único — todo o HTML, CSS e JS inline
```

Sem dependências externas de build. Nenhum framework, nenhum bundler. Basta abrir o arquivo no browser.

---

## Seções

| ID                 | Seção                                                  |
|--------------------|--------------------------------------------------------|
| `#hero`            | Apresentação principal com chat mockup e estatísticas  |
| `#problem`         | Diagnóstico — comparação Sem vs Com o Flow Agent       |
| `#features`        | Cinco automações (pilares do agente)                   |
| `#how`             | Como funciona — 4 passos de ativação                   |
| `#insights`        | Dados de mercado — por que automação com IA            |
| `#pricing`         | Modelo de planos com toggle mensal/anual               |
| `#faq`             | Dúvidas frequentes                                     |
| `#form-section`    | Formulário de solicitação de demo                      |

---

## Funcionalidades

### Internacionalização (i18n)

A página é totalmente bilíngue. O toggle **PT / EN** aparece no header, no menu mobile e no footer — os três sincronizam simultaneamente.

- A função `setLang(lang, btn)` itera todos os elementos `[data-i18n]` e substitui o conteúdo pelo dicionário correspondente
- Placeholders de inputs também são trocados (incluindo formato de telefone: `+55` → `+1`)
- Opções de `<select>` são trocadas via IDs (`opt-tipo-*`, `opt-pais-*`, `opt-plano-*`)
- Texto de consentimento, links e badges são cobertos

**Para adicionar uma string nova:**
1. Adicione `data-i18n="minha-chave"` ao elemento HTML
2. Adicione `'minha-chave': 'Texto em PT'` ao objeto `PT` do dicionário `i18n`
3. Adicione `'minha-chave': 'English text'` ao objeto `EN`

### Modelo de Planos

Toggle **Mensal / Anual** com 20% de desconto no plano anual. A função `applyPrices()` é chamada tanto na troca de idioma quanto na troca de ciclo.

**Preços fixos (sem conversão por API):**

| Plano        | BR Mensal | BR Anual   | EUA Mensal | EUA Anual   |
|--------------|-----------|------------|------------|-------------|
| Essencial    | R$ 147    | R$ 118/mês | US$ 97     | US$ 78/mês  |
| Profissional | R$ 297    | R$ 238/mês | US$ 197    | US$ 158/mês |
| Exclusivo    | R$ 497    | R$ 398/mês | US$ 397    | US$ 318/mês |

Para alterar preços, edite o objeto `PLAN_PRICES` no bloco de script.

### Favicon

SVG inline como `data:image/svg+xml` — ícone de robô IA com paleta teal/gold, funciona sem arquivo externo e em `file://`.

### Formulário

Campos: Nome, E-mail, WhatsApp/Telefone, Tipo de estabelecimento, Plano, País.

- O botão **"Solicitar Demo"** do nav pré-seleciona a opção "Ainda não sei" no campo de plano e rola até o formulário
- Os CTAs de cada card de plano pré-selecionam o plano correspondente

---

## Responsividade

| Breakpoint   | Comportamento                                                      |
|--------------|--------------------------------------------------------------------|
| `≤ 1100px`   | Pricing em coluna, ajustes de padding                              |
| `≤ 900px`    | Features em cards verticais, nav mobile ativo                      |
| `≤ 768px`    | Hero-stats em grid 2×2, how-grid em coluna, footer em coluna       |
| `≤ 480px`    | Hero CTAs em coluna, badge do billing toggle em posição estática   |

---

## Paleta de cores (CSS custom properties)

| Variável                 | Uso                                        |
|--------------------------|--------------------------------------------|
| `--teal` / `--teal-d`    | Cor de destaque principal (verde-azulado)  |
| `--gold` / `--gold-lt`   | Cor secundária (dourado)                   |
| `--s1` / `--s2`          | Backgrounds de seção                       |
| `--card`                 | Background de cards                        |
| `--bdr`                  | Bordas sutis                               |
| `--t1` / `--t2` / `--t3` | Hierarquia de texto                        |

---

## Como usar localmente

```bash
# Nenhuma instalação necessária
# Abra diretamente no browser:
open index.html

# Ou sirva com qualquer servidor estático, ex:
npx serve .
python3 -m http.server 5500
```

---

## Personalização rápida

| O que mudar           | Onde no arquivo                                              |
|-----------------------|--------------------------------------------------------------|
| Nome/marca            | Buscar `Flow Agent` — ocorre em textos, título e meta tags   |
| Cores                 | Bloco `:root { }` no início do `<style>`                     |
| Preços                | Objeto `PLAN_PRICES` e `PLAN_OPT_LABELS` no bloco `<script>` |
| Textos PT             | Objeto `PT:` dentro de `var i18n`                            |
| Textos EN             | Objeto `EN:` dentro de `var i18n`                            |
| WhatsApp de contato   | Buscar `wa.me/5531994536050`                                 |
| E-mail de contato     | Buscar `contato@flow-agent.app`                              |

---

## Stack mencionada na página

- **n8n** — orquestração de fluxos de automação
- **OpenAI** — modelo de linguagem do agente
- **WhatsApp Business** — canal de atendimento
- **Cal.com / Google Agenda** — integração de agendamento

---

## Licença

Uso interno — TecWise / Flow Agent. Todos os direitos reservados.