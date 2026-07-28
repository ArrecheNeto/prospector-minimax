---
name: prospector-setup
description: Configuração inicial do Prospector de Sites no MiniMax Code — coleta assinatura, nichos, cidade e conexão HostGator, e instala o painel local. Use quando o usuário disser "configurar prospector", "setup", "começar", "meus dados", ou na primeira vez que rodar qualquer skill do prospector sem um prospector-config.json.
---

# Prospector — configuração inicial (MiniMax Code)

Rode UMA vez. Salva tudo em `prospector-config.json` na pasta de trabalho do projeto.

## 0. ANTES DE TUDO — precisa ser o MiniMax Code DESKTOP

Este plugin trabalha com arquivos e programas **no computador do usuário**: cria o banco de leads, gera os sites, roda o painel local e publica na hospedagem. Isso só funciona na versão **desktop** (self-hosted), que tem acesso ao disco e ao terminal.

Na versão **web** (nuvem), a busca até roda, mas nada é salvo na máquina do usuário — sem painel, sem publicação, sem banco.

Confirme com o usuário que ele está no desktop. Se não estiver, avise antes de continuar: baixar em `https://agent.minimax.io/download`. Não prossiga com o setup do painel na versão web.

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

Os arquivos do painel **vêm do repositório**, não do pacote da skill — assim funciona mesmo que a importação da skill não tenha trazido as pastas de apoio.

Na pasta do projeto, baixe os quatro arquivos (use o terminal; `curl` no Windows/Mac):

```
BASE=https://raw.githubusercontent.com/ArrecheNeto/prospector-minimax/main/dashboard

curl -L -o dashboard-server.py     $BASE/dashboard-server.py
curl -L -o dashboard-template.html $BASE/dashboard-template.html
curl -L -o iniciar-dashboard.bat   $BASE/iniciar-dashboard.bat
curl -L -o iniciar-dashboard.command $BASE/iniciar-dashboard.command
```

Confira que os arquivos existem e não vieram vazios (o `dashboard-template.html` tem dezenas de KB — se vier com poucos bytes, o download falhou e é preciso repetir).

Depois siga a skill `dashboard-leads` para criar o banco `prospector.db` e gerar o `dashboard.html`. Explique ao usuário: duplo clique em `iniciar-dashboard.bat` (Windows) ou `iniciar-dashboard.command` (Mac) abre o painel em http://localhost:8765 — precisa de Python instalado e no PATH. Sem Python, o `dashboard.html` abre por duplo clique em modo leitura.

O mesmo vale para os scripts de publicação (skill `deploy-hostgator`): se não estiverem na pasta, baixe de `https://raw.githubusercontent.com/ArrecheNeto/prospector-minimax/main/skills/deploy-hostgator/references/`.

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
