---
name: prospector-setup
description: Configuração inicial do Prospector de Sites no MiniMax Code — coleta assinatura, nichos, cidade e conexão HostGator, e instala o painel local. Use quando o usuário disser "configurar prospector", "setup", "começar", "meus dados", ou na primeira vez que rodar qualquer skill do prospector sem um prospector-config.json.
---

# Prospector — configuração inicial (MiniMax Code)

Rode UMA vez. Salva tudo em `prospector-config.json` na pasta de trabalho do projeto.

## 1. Verificar config

Procure `prospector-config.json` na pasta do projeto. Se existir, mostre um resumo (SEM a senha) e pergunte o que atualizar. Se não existir, colete os dados abaixo.

## 2. Dados do usuário (pergunte em blocos curtos)

- **Assinatura da proposta**: nome completo, como se apresenta (ex.: "Designer de páginas de alta conversão") e WhatsApp `55DDDNUMERO`.
- **Nichos padrão**: sugira nutricionistas, psicólogos, advogados, psiquiatras — deixe editar.
- **Cidade/região padrão**.
- **Leads por busca**: padrão 10.
- **Modo de envio da proposta**: padrão "rascunho no Gmail para revisão".

## 3. Conexão HostGator

Se já contratou a hospedagem: **não colete a senha pelo chat**. Oriente a preencher no `prospector-config.json` (ou na aba Configurações do painel), os campos `usuario`, `dominio`, `servidor` e `senha` do cPanel. A senha vive só no arquivo local.

## 4. Salvar

`prospector-config.json` na pasta do projeto:

```json
{
  "assinatura": { "nome": "", "apresentacao": "", "whatsapp": "" },
  "prospeccao": { "nichos": ["nutricionistas","psicologos","advogados","psiquiatras"], "cidade": "", "leadsPorBusca": 10 },
  "envio": { "modo": "rascunho" },
  "hostgator": { "usuario": "", "dominio": "", "servidor": "", "senha": "", "pastaBase": "clientes" }
}
```

## 5. Painel local

Siga a skill `dashboard-leads` para copiar `dashboard-server.py` + o iniciador e criar o banco `prospector.db` e o `dashboard.html`. Explique: duplo clique no `iniciar-dashboard.bat` (Windows) / `.command` (Mac) abre o painel em http://localhost:8765 (precisa de Python no PATH).

## 6. Pré-requisitos no MiniMax Code (avise o usuário)

Esta versão roda no **MiniMax Code** (modelo MiniMax-M3). O que precisa estar ligado:

1. **As skills do Prospector** — instaladas pelo Skills Hub (a partir do repositório) ou copiadas para a pasta de skills. Confira se aparecem na lista de Skills.
2. **MCP do Prospector CRM** (`mcp/prospector-mcp.py`) — administra os leads (listar, salvar, status, follow-ups, financeiro). Adicione como servidor MCP apontando para o arquivo, com `--pasta` na pasta do projeto.
3. **Navegador** — a skill `prospeccao-maps` precisa abrir o Google Maps e os sites dos leads. Use o navegador do MiniMax Code (Computer Use / browser) ou um MCP de navegador.
4. **Geração de imagem e vídeo** — nativa do MiniMax Code, usada pela skill `midia-minimax`. Não precisa de serviço externo.
5. (Opcional) **Agent Team** — ative para rodar a esteira como time (ver skill `time-prospector`); é o que habilita o Verifier revisar cada entrega.
6. (Opcional) **Scheduled** — para a prospecção rodar sozinha (ver skill `agenda-prospeccao`).

O MiniMax Code já tem ferramentas de **arquivo e terminal**, então o painel local e a publicação na HostGator funcionam sem nada extra.

## 7. Encerrar

Confirme o que foi salvo e explique o ciclo: **prospectar** (skill prospeccao-maps) → **redesenhar** (redesign-premium, com imagens geradas pela `midia-minimax`) → **publicar** (deploy-hostgator) → **proposta** (proposta-gmail, com o vídeo antes/depois na capa), com o `dashboard.html` como painel de tudo.
