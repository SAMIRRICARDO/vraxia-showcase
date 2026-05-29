# Checklist de Publicação — vraxia-showcase

Executar antes de tornar o repositório público.

---

## Segurança — Obrigatório

- [ ] Nenhum arquivo `.env` ou `.env.*` no repositório
- [ ] Nenhuma chave de API (Anthropic, OpenAI, Resend, etc.)
- [ ] Nenhum token do GitHub, Vercel ou serviço externo
- [ ] Nenhuma senha ou credencial de banco de dados
- [ ] Nenhum IP, hostname ou URL de infraestrutura interna
- [ ] Nenhum código de implementação backend
- [ ] Nenhum schema de banco de dados com dados reais
- [ ] `git log --all -- '*.env'` → confirmar que nunca houve commit de secrets
- [ ] `git grep -r "sk-"` → confirmar ausência de API keys
- [ ] `git grep -r "password"` → confirmar ausência de senhas

---

## Conteúdo — Verificar

- [ ] `README.md` — links funcionando (especialmente a URL do Vercel)
- [ ] `ARCHITECTURE.md` — apenas visão conceitual, sem detalhes de implementação
- [ ] `HUMAN_RAG.md` — conceito explicado, sem código proprietário
- [ ] `ROADMAP.md` — items de roadmap realistas e não comprometedores
- [ ] `SCREENSHOTS.md` — URL do Vercel correta
- [ ] `docs/` — todos os arquivos revisados e consistentes
- [ ] `LICENSE` — CC BY-NC-ND 4.0 adequada para showcase sem exposição de código
- [ ] `.gitignore` — cobre `.env`, `node_modules`, `secrets/`, `credentials/`

---

## Repositório GitHub — Configurar

- [ ] Nome: `vraxia-showcase`
- [ ] Visibilidade: **Public**
- [ ] Descrição: `AI Operating System for Enterprise — Portfolio Showcase`
- [ ] Topics: `ai`, `multi-agent`, `rag`, `llm`, `enterprise-ai`, `typescript`, `cognitive-legacy`, `portfolio`
- [ ] Website: `https://vraxia-platform.vercel.app`
- [ ] Desabilitar: Issues (opcional se não quiser gerenciar), Wiki, Projects
- [ ] Habilitar: Discussions (para feedback e perguntas técnicas)

---

## Repositório GitHub — Aparência

- [ ] Social preview image configurada (1280×640px)
  - Usar screenshot do dashboard ou logo VRAXIA sobre fundo escuro
- [ ] README renderizando corretamente com badges e tabelas
- [ ] Branch padrão: `main`

---

## Após Publicar

- [ ] URL do repositório: `https://github.com/samirricardo/vraxia-showcase`
- [ ] Adicionar URL no perfil do GitHub (Pinned Repositories)
- [ ] Atualizar LinkedIn com link do repositório
- [ ] Adicionar link no README do `ai-cognitive-runtime` (projeto principal)
- [ ] Testar link do Vercel na seção Screenshots

---

## Comandos Git para publicação

```bash
cd C:\AI-LAB\vraxia-showcase

# Inicializar
git init
git add .
git commit -m "feat: initial vraxia showcase — portfolio documentation"

# Criar repositório público no GitHub
gh repo create vraxia-showcase \
  --public \
  --description "AI Operating System for Enterprise — Portfolio Showcase" \
  --source=. \
  --remote=origin \
  --push

# Confirmar
gh repo view vraxia-showcase --web
```

---

## O que este repositório expõe ✅

- Conceito e posicionamento da VRAXIA
- Arquitetura conceitual (sem código)
- Explicação do Human RAG e PsychAgent
- Módulos e casos de uso
- Roadmap estratégico
- Link para o showcase ao vivo (Vercel)

## O que este repositório NÃO expõe ✅

- Código fonte da aplicação
- Implementação do backend ou agentes
- APIs, endpoints ou rotas
- Schemas de banco de dados
- Credenciais, tokens ou secrets
- Lógica de embeddings ou vetorização
- Configurações de infraestrutura
