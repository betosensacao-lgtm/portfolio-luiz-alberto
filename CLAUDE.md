# Portfólio — Luiz Alberto

Site pessoal de portfólio (single-page, dark mode) apresentando aplicações web desenvolvidas por Luiz Alberto (betosensacao@gmail.com).

## Arquivos

Tudo vive em `portfolio-luiz-alberto/`:

- **`index.html`** — versão em português (padrão, `lang="pt-BR"`).
- **`index-en.html`** — versão em inglês (`lang="en"`), tradução completa do mesmo layout/seções.
- **`CLAUDE.md`** — este arquivo.

As duas versões são autocontidas (HTML + CSS + JS embutidos, sem dependências externas) e **devem ficar em sincronia estrutural**: qualquer alteração de layout, estilo, seção ou projeto precisa ser replicada nos dois arquivos (traduzindo os textos). Cada nav e o rodapé incluem um seletor de idioma (`.lang-switch`) que aponta para o arquivo irmão (`index.html` ↔ `index-en.html`).

## Estrutura do site

Página única com navegação por âncoras (`#medbook`, `#aria`, `#bookclinic`). Cada projeto tem sua própria seção em formato de mini landing page:

- **Hero**: título, pitch pessoal, estatísticas e CTA de contato.
- **Seção por projeto**: kicker + título + descrição, lista de tags/stack, lista de funcionalidades, botões com link para a URL ao vivo, e um "mockup" da interface desenhado em CSS (sem capturas de tela reais).
- **Footer**: contato e atalhos para as três URLs ao vivo.

Navegação ativa, menu mobile (hambúrguer) e animações de "reveal on scroll" são controlados pelo `<script>` no fim do arquivo (sem libs externas, usa `IntersectionObserver`).

## Projetos cadastrados

| Projeto | URL ao vivo | Observação |
|---|---|---|
| **MedBook** | https://medbook-amber.vercel.app/booking (+ `/triage`) | Fusão dos projetos **ScheduleClinic** + **Aria-Med**. Plataforma de agendamento médico multi-clínica com triagem de sintomas por IA. |
| **ARIA** | https://aria-chatbot-blond.vercel.app/ | Chatbot de atendimento ao cliente com IA (Claude/Anthropic), pronto para 3 verticais (imobiliário, e-commerce, saúde). |
| **BookClinic (AgendaClin)** | https://agendaclin.vercel.app/model-dental-clinic (+ `/login`) | Plataforma de agendamento online white-label para clínicas; instância de demonstração: "Model Dental Clinic". |

> Nota: ScheduleClinic e Aria-Med não têm mais seções próprias — foram unificados no MedBook. Não recriar seções separadas para eles.

## Como adicionar ou atualizar um projeto

1. Duplique um bloco `<section class="project" id="...">` existente (estrutura `.section-head` + `.project-grid` com `.project-info` e `.mockup`).
2. Atualize: kicker, título, descrição, tagline, tags (`.tag`), lista de funcionalidades (`.feature-list`) e os links (`.project-links`) com a URL real do projeto (sempre `target="_blank" rel="noopener"`).
3. Recrie o "mockup" (`.mockup .screen`) em CSS/HTML simples — siga o estilo dos existentes (barra de navegador falsa com `.bar`, conteúdo estilizado representando a UI real). Evite imagens externas; mantenha tudo inline para o arquivo continuar autocontido.
4. Adicione o link de navegação correspondente em `<div class="nav-links">` e no rodapé (`.footer-links`).
5. Adicione a classe `reveal` em blocos que devem animar ao entrar na tela.
6. **Replique a mudança no arquivo irmão** (`index.html` ↔ `index-en.html`), traduzindo todos os textos (kicker, título, descrição, tagline, tags, features, mockup, nav, footer). Não deixe as duas versões divergirem em estrutura — só o idioma deve mudar.

## Convenções de estilo

- Paleta dark definida via variáveis CSS no `:root` (`--bg`, `--card`, `--accent`, `--accent2`, `--accent3`, `--grad`).
- Gradiente de destaque (`--grad`) usado em títulos (`.grad`), botões primários (`.btn-primary`) e elementos de IA/usuário no chat.
- Tipografia do sistema (`Segoe UI`/system fonts) — sem fontes externas, para manter o arquivo leve e independente.
- Espaçamento generoso (`padding:120px 6vw` nas seções) e bordas suaves (`border-radius` entre 10–18px).
- Responsivo: breakpoint único em `880px` que empilha o grid de duas colunas e ativa o menu mobile.

## Manutenção

- O arquivo é autocontido — não requer build, bundlers ou servidor. Basta abrir `index.html` no navegador.
- Ao alterar conteúdo de projetos, confira se as URLs ainda estão no ar (os projetos estão hospedados na Vercel e podem mudar de domínio).
- Para novas capturas de tela reais (em vez de mockups CSS), usar a extensão Claude in Chrome para navegar e capturar, depois substituir o bloco `.mockup .screen` por uma `<img>`.
