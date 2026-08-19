# Plano de SEO On-Page — Clínica Qualité (clinicaqualite.com.br)

Diagnóstico completo do site atual + plano de ação para o melhor SEO on-page possível.
Auditoria feita em cima dos arquivos reais do projeto (`index.html`, `sobre.html`, `profissionais.html`, `profissional-*.html`).

**Legenda de prioridade:**
- 🔴 **P0 — Crítico.** Corrigir antes de qualquer outra ação de SEO. São erros que podem prejudicar confiança (E-E-A-T), gerar conteúdo duplicado ou quebrar compartilhamentos.
- 🟠 **P1 — Fundação técnica.** Base que todo o resto depende.
- 🟡 **P2 — Conteúdo e autoridade.** Onde o site ganha ranqueamento de verdade a médio prazo.
- 🟢 **P3 — Local SEO e fora do site.** Essencial para clínica local, mesmo sendo "fora da página".
- 🔵 **P4 — Monitoramento contínuo.**

---

## 🔴 P0 — Bugs críticos encontrados (corrigir primeiro)

### 1. Conteúdo de perfil idêntico (e incorreto) em TODAS as páginas de profissionais
Todas as 14 páginas `profissional-*.html` usam o **mesmo texto de template**, escrito para uma psicóloga que faz Terapia Cognitivo-Comportamental — inclusive nas páginas da **massoterapeuta**, **fonoaudióloga**, **médica** e **nutricionista**. Isso está presente em:
- Frase de abertura: *"Especialista em criar um espaço seguro para o autoconhecimento... utilizando a Terapia Cognitivo-Comportamental..."*
- Seção "Minha Abordagem" (fala em TCC para todos)
- Citação "O que eu penso sobre terapia"
- Tags de "Especialidades": Ansiedade, Depressão, Autoestima, Relacionamentos, Estresse, Luto — em **todas** as páginas
- Seção "Formação": **"Graduação em Psicologia — UNESP" e "Especialização em TCC"** aparece até no perfil da massoterapeuta Gabriela Balm e da médica Larissa

**Por que isso é grave:**
- **Conteúdo 100% duplicado entre 14 páginas** → Google trata como conteúdo fraco/duplicado e não indexa nem ranqueia bem nenhuma delas individualmente.
- Site de saúde é conteúdo **YMYL** (Your Money or Your Life) — o Google exige sinais fortes de **E-E-A-T** (Experiência, Expertise, Autoridade, Confiança). Credenciais erradas/genéricas destroem esse sinal.
- **Risco factual/legal:** atribuir formação em Psicologia e especialização em TCC a profissionais que não são psicólogos é uma informação falsa publicada no site.

**Ação:** reescrever individualmente cada uma das 14 páginas com: formação real, abordagem real, especialidades reais, uma citação autêntica. Preciso que você me envie (ou peça para cada profissional preencher) um mini-briefing por pessoa — modelo no final deste documento.

### 2. Dados estruturados (JSON-LD) com informação errada em todas as páginas
O campo `"description"` do schema `Person` é **idêntico e errado** nas 14 páginas — sempre *"Psicóloga especialista em Terapia Cognitivo-Comportamental..."*, mesmo em `profissional-gabriela-balm.html` (massoterapeuta) e `profissional-larissa-santana.html` (médica). O `jobTitle` está correto, mas a `description` contradiz.
Além disso, em `profissional-leonardo.html` (homem) a descrição diz **"Psicóloga"** (gênero errado) e o link do WhatsApp manda a mensagem *"Gostaria de agendar **com a** Leonardo Bonome"* — erro de concordância que se repete para todos os profissionais homens (Leonardo, Igor, Gustavo, Yudi).

**Ação:** gerar a `description` do JSON-LD dinamicamente a partir do texto real de cada perfil (ver item 1) e corrigir a concordância de gênero nos textos de WhatsApp ("com o"/"com a" conforme o profissional).

### 3. Telefone e endereço provavelmente fictícios (NAP inconsistente)
- Telefone usado em todo o site (schema, WhatsApp, footer): `+55-18-99999-9999` / `5518999999999`. **Igarapava-SP fica na região do DDD 16**, não 18 — indício forte de número placeholder que nunca foi trocado pelo real.
- Endereço no schema: `"Rua das Flores, 100"`, CEP `14960-000` — parecem dados de exemplo, não o endereço real da clínica.
- `"hasMap": "https://maps.google.com/?q=Igarapava+SP"` aponta para a cidade genérica, não para o pino real da clínica no Google Maps.

**Por que é grave:** para negócio local, **NAP (Nome, Endereço, Telefone) consistente** entre site, Google Business Profile e diretórios é um dos fatores mais fortes de Local SEO. Dado fictício = zero confiança para o Google e paciente perdido tentando ligar num número que não existe.

**Ação:** me passe telefone real (com DDD correto), endereço completo real, CEP real e o link do pino da clínica no Google Maps (ou do Google Business Profile) para eu atualizar em todo o site (schema + todos os `wa.me` + footer).

### 4. Imagem de compartilhamento (Open Graph) quebrada
`og:image` aponta para `https://clinicaqualite.com.br/og-image.jpg`, mas **esse arquivo não existe** na pasta do projeto. Resultado: ao compartilhar o link no WhatsApp, Instagram ou Facebook, o preview aparece **sem imagem**.

**Ação:** criar uma imagem 1200×630px (logo + nome + foto do espaço) e salvá-la como `og-image.jpg` na raiz do site, referenciada em todas as páginas (hoje só a home tem a tag `og:image`; as demais páginas não têm — replicar em todas com uma imagem por seção, ex: foto do profissional na página dele).

### 5. Nenhum favicon
Não há `<link rel="icon">` em nenhuma página. A aba do navegador fica sem ícone e o Google também usa o favicon nos resultados de busca mobile.

**Ação:** gerar favicon (16x16, 32x32, apple-touch-icon 180x180) a partir do logo e adicionar em todas as páginas.

---

## 🟠 P1 — Fundação técnica de SEO

### 6. `robots.txt` e `sitemap.xml` não existem
Nenhum dos dois arquivos existe na raiz do site. Sem `sitemap.xml`, o Google demora mais para descobrir e re-rastrear as 17 páginas do site (principalmente as 14 páginas de profissionais, que não têm nenhum link externo apontando para elas).

**Ação:**
- [ ] Criar `sitemap.xml` na raiz listando as 17 páginas (home, sobre, profissionais, 14 perfis) com `lastmod`.
- [ ] Criar `robots.txt` simples liberando tudo e apontando para o sitemap:
  ```
  User-agent: *
  Allow: /
  Sitemap: https://clinicaqualite.com.br/sitemap.xml
  ```
- [ ] Submeter o site e o sitemap no **Google Search Console** (ver seção de acessos necessários).

### 7. Tailwind CSS via CDN em produção
Todas as páginas carregam `<script src="https://cdn.tailwindcss.com?plugins=forms"></script>`. O próprio time do Tailwind **desaconselha isso em produção**: o navegador baixa o compilador inteiro e gera o CSS em tempo real no cliente, o que:
- Aumenta o tempo de bloqueio de renderização (**afeta LCP e INP**, que são fatores de ranqueamento do Core Web Vitals).
- Gera CSS não otimizado/purgado (arquivo maior do que precisa).
- É renderizado via JS, então por uma fração de segundo a página aparece sem estilo (FOUC).

**Ação:** migrar para uma build estática do Tailwind (CLI ou Vite) que gera um arquivo `.css` compilado e "purgado" no build, sem depender de JS no carregamento. Posso fazer essa migração — só preciso confirmar se você tem preferência de ferramenta de build/hospedagem.

### 8. Imagens pesadas, sem dimensões e sem lazy loading
- As imagens da pasta `imagens/` (fachada, sala de espera, consultórios) são **prints de tela em PNG**, entre 146 KB e **630 KB** cada — muito acima do recomendado (idealmente <150 KB por imagem hero).
- Fotos de profissionais são extremamente inconsistentes: algumas com **4 KB** (resolução muito baixa, vão aparecer borradas em tela cheia) e outras com **140–212 KB** sem compressão.
- Nenhuma tag `<img>` no site tem `width`/`height` definidos → risco de **CLS** (layout pulando enquanto a imagem carrega).
- Nenhuma imagem usa `loading="lazy"` (exceto as que já estão no topo, que devem continuar carregando eager).

**Ação:**
- [ ] Reexportar as fotos da clínica em resolução real (não prints de tela) e comprimir para **WebP/AVIF** com fallback, mirando <150 KB.
- [ ] Padronizar as fotos de profissionais: mesma resolução mínima (ex: 800×800px), mesmo enquadramento, comprimidas (~50–100 KB).
- [ ] Adicionar `width` e `height` em todas as tags `<img>`.
- [ ] Adicionar `loading="lazy"` em todas as imagens abaixo da dobra (equipe, "Nosso Espaço", galerias).
- [ ] Renomear arquivos de imagem para nomes descritivos com palavra-chave (ex: `imagens/Captura de tela 2026-05-24 183434.png` → `sala-de-espera-clinica-qualite-igarapava.webp`) — nome de arquivo também é sinal para Google Imagens.

### 9. Fontes do Google carregadas sem otimização
Duas folhas de estilo separadas do Google Fonts (`Be Vietnam Pro`/`Quicksand` e `Material Symbols`) são carregadas de forma bloqueante em todas as páginas.

**Ação:** combinar as famílias numa única requisição, usar `font-display: swap` (já usado, ok) e considerar hospedar as fontes localmente (self-host) para eliminar a dependência de terceiros e reduzir round-trips.

### 10. Google Analytics / Search Console não identificados
Não encontrei nenhum script de analytics (GA4, Meta Pixel, etc.) no código.

**Ação:**
- [ ] Instalar **Google Analytics 4**.
- [ ] Verificar propriedade no **Google Search Console** (domínio inteiro, via DNS).
- [ ] Configurar rastreamento de clique nos botões "Agendar via WhatsApp" como evento de conversão.

---

## 🟡 P2 — Conteúdo (onde o ranqueamento é ganho de verdade)

### 11. Reescrever os 14 perfis com conteúdo único e real
Depende do item 1. Cada página deve ter, com texto próprio:
- Abordagem/metodologia real do profissional
- Formação real (faculdade, ano, especializações) + **número de registro no conselho de classe** (CRP para psicólogos, CRM para médica, CRN para nutricionista, CREFONO para fonoaudióloga) — isso é forte sinal de E-E-A-T para saúde e também é **exigência ética/legal** dos conselhos profissionais no Brasil.
- Especialidades reais (ex: massoterapeuta não deveria ter "Depressão" como especialidade)
- Uma citação autêntica da pessoa

### 12. Criar páginas de especialidade (hoje só existem âncoras de filtro)
Hoje, "Psicologia", "Nutrição", "Massoterapia", "Medicina" e "Fonoaudiologia" na home são só filtros dentro de `profissionais.html` (`?area=psicologia`), sem conteúdo próprio indexável — é uma oportunidade perdida de ranquear para buscas como *"psicólogo em Igarapava"* ou *"nutricionista em Igarapava"*.

**Ação:** criar uma página própria por especialidade (ex: `psicologia.html`, `nutricao.html`, `fonoaudiologia.html`, `medicina.html`, `massoterapia.html`) com:
- H1 e conteúdo único sobre a especialidade e como é o atendimento na clínica
- Lista dos profissionais daquela área (com link para o perfil)
- FAQ específica da área (schema `FAQPage`)
- CTA de WhatsApp

### 13. Adicionar seção de FAQ (com schema `FAQPage`)
Nenhuma página tem perguntas frequentes. FAQ bem feita ranqueia em "People Also Ask" do Google e ajuda a capturar buscas de cauda longa.

**Sugestões de perguntas para a Home/Sobre:**
- A clínica atende por convênio ou é só particular?
- Atende presencial e online?
- Como funciona o agendamento?
- Quais especialidades a clínica oferece?
- Atende crianças/adolescentes?

### 14. Adicionar depoimentos reais de pacientes
Não há prova social no site (nenhum depoimento, avaliação ou selo). Depoimentos reais (com autorização do paciente) + schema `Review`/`AggregateRating` aumentam confiança e taxa de conversão, além de ser outro sinal de E-E-A-T.

### 15. Blog / conteúdo local (estratégia de médio prazo)
Para captar buscas informacionais ("como saber se preciso de terapia", "nutrição para ansiedade", "quando levar meu filho ao fonoaudiólogo") e reforçar autoridade da clínica na região. Não é urgente, mas é o maior alavancador de tráfego orgânico a médio/longo prazo depois que a fundação técnica estiver corrigida.

### 16. Revisão de title/description por página
Os títulos e descrições atuais já seguem um padrão razoável (únicos por página, com localização). Pontos de ajuste:
- Manter títulos com até ~60 caracteres para não truncar no Google (o da Home está em ~68).
- Meta descriptions com até ~155 caracteres, sempre com CTA implícito ("agende pelo WhatsApp").
- Adicionar `twitter:image` (falta hoje) espelhando o `og:image`.

---

## 🟢 P3 — Local SEO (o maior alavancador para uma clínica de bairro)

Para um negócio local como a Qualité, **Google Business Profile (Google Meu Negócio) e citações locais pesam tanto ou mais que o site em si** nos resultados de busca com intenção local ("clínica de psicologia perto de mim", "nutricionista Igarapava").

- [ ] **Criar/reivindicar o Google Business Profile** da clínica (se ainda não existir), com categoria correta, fotos reais, horário de funcionamento completo, e o mesmo NAP do site.
- [ ] Incorporar um **iframe do Google Maps** com o pino real da clínica na página "Sobre" (hoje só existe um link genérico para "Igarapava SP").
- [ ] Cadastrar a clínica em diretórios relevantes de saúde no Brasil: **Doctoralia**, **Google Business**, **Facebook**, diretórios locais de Igarapava/região.
- [ ] Pedir avaliações no Google de pacientes reais (aumenta CTR no mapa e no orgânico).
- [ ] Garantir que o NAP (nome, endereço, telefone) seja **idêntico** em: site, Google Business Profile, Instagram, WhatsApp Business e qualquer diretório.
- [ ] Avaliar se a clínica atende pacientes de cidades vizinhas (Ituverava, Guará, Buritizal, Miguelópolis, Aramina, Sales Oliveira) — se sim, vale mencionar isso no conteúdo (real, não forçado) para capturar buscas regionais.

---

## 🔵 P4 — Monitoramento contínuo

- [ ] Google Search Console: acompanhar cobertura de indexação, Core Web Vitals e queries que já trazem impressões.
- [ ] Revisar mensalmente quais páginas de profissionais/especialidades estão gerando cliques no WhatsApp (via GA4).
- [ ] Depois da fundação técnica pronta, rodar PageSpeed Insights / Lighthouse em mobile e desktop para confirmar ganho real de performance após tirar o Tailwind CDN e comprimir imagens.

---

## O que eu preciso de você para avançar

**Dados do negócio (crítico, bloqueia o item P0):**
1. Telefone/WhatsApp real da clínica (com DDD correto).
2. Endereço completo real + CEP.
3. Horário de funcionamento completo (inclusive sábado, se houver).
4. Link do Google Business Profile da clínica (se já existir) ou confirmação de que precisa ser criado.

**Por profissional (14 pessoas) — para reescrever os perfis com conteúdo real:**
- Formação (faculdade + ano) e número de registro no conselho (CRP/CRM/CRN/CREFONO/etc.)
- Abordagem/metodologia real de trabalho
- 3–6 especialidades reais
- Uma frase/citação autêntica sobre o trabalho dela(e)
- Instagram (já tenho a maioria, só confirmar)

**Outros:**
- Fotos originais em alta resolução (do espaço da clínica e dos profissionais) — hoje só existem prints de tela e fotos com resolução muito baixa.
- 2–3 depoimentos reais de pacientes (com autorização) para prova social.
- Acesso ao domínio/DNS ou à hospedagem, para eu configurar o Google Search Console e, se necessário, subir os arquivos corrigidos.
- Confirmação se pode usar Analytics/GA4 (padrão de mercado) sem restrição.

Assim que eu tiver essas informações, sigo com as correções em ordem de prioridade (🔴 P0 → 🟠 P1 → 🟡 P2 → 🟢 P3) e te aviso a cada etapa concluída.
