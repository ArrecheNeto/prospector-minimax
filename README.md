# Prospector de Sites — para MiniMax Code

Um time de agentes que encontra pequenos negócios com site fraco, refaz a página em versão premium, publica e prepara a proposta — rodando no **MiniMax Code** com o modelo **MiniMax-M3**.

**O que muda nesta versão:** as imagens do site e o vídeo antes/depois da proposta são gerados pelo próprio MiniMax (não precisa de outro serviço), a esteira roda como **Agent Team** com um **Verifier** revisando cada entrega, e a prospecção pode ficar **agendada**, rodando sozinha.

## As skills

| Skill | O que faz |
|---|---|
| `prospector-setup` | Configuração inicial (seus dados, HostGator, painel) |
| `time-prospector` | Define o Agent Team e o que o **Verifier** confere antes de cada entrega sair |
| `prospeccao-maps` | Busca no Google Maps e qualifica os leads (nota alta + site fraco + e-mail) |
| `redesign-premium` | Refaz a página em versão premium, com editor e comparador |
| `midia-minimax` | Gera as imagens do site e o vídeo antes/depois (nativo) |
| `deploy-hostgator` | Publica página, capa, assets e vídeo; confere o HTTPS |
| `proposta-gmail` | Escreve a proposta anti-spam e cria o rascunho no Gmail |
| `agenda-prospeccao` | Deixa a prospecção rodando sozinha (Scheduled) |
| `dashboard-leads` | Painel local com kanban e financeiro |
| `contrato-servico` | Gera o contrato quando o cliente fecha |

## O time (Agent Team)

```
Scout      → acha e qualifica os leads
Designer   → refaz a página e gera as imagens
Publisher  → publica e confere o HTTPS
Copywriter → escreve a proposta
Verifier   → revisa a entrega de cada um, sem ter participado da execução
```

O Verifier é o que segura a qualidade: ele não vê como o trabalho foi feito, só o resultado — então julga o que está na tela. Se a página quebra no celular, se o e-mail tem algo que cai no spam, se o site publicado ficou com imagem quebrada: volta pra correção antes de chegar no cliente.

## ⚠️ Precisa ser o MiniMax Code **desktop**

Este plugin mexe em arquivos no seu computador: cria o banco de leads, gera os sites, roda o painel local e publica na hospedagem. Isso exige a versão **desktop** (self-hosted), que tem acesso ao disco e ao terminal — baixe em [agent.minimax.io/download](https://agent.minimax.io/download).

Na versão **web** (nuvem) a busca até roda, mas nada é salvo na sua máquina: sem painel, sem publicação, sem banco de leads.

## Instalação

1. **Skills** — no MiniMax Code, vá em **Skills → Create**. Três caminhos:
   - **Import from Github** (recomendado): cole o link deste repositório. O campo aceita o repo inteiro ou um caminho específico: `https://github.com/owner/repo[/tree/branch/path]` — para uma skill isolada, aponte para a pasta dela, ex.: `.../tree/main/skills/prospeccao-maps`.
   - **Upload a skill**: envie um arquivo `.zip`, `.skill` ou `.md`.
   - **Build with Mavis**: criar conversando (não é o caso aqui).

   Depois de importar, confira em **Skills → Yours** se elas aparecem.
2. **CRM (MCP)** — adicione `mcp/prospector-mcp.py` como servidor MCP:
   ```
   python  CAMINHO/mcp/prospector-mcp.py  --pasta  CAMINHO/DO/PROJETO
   ```
   É ele que guarda os leads (SQLite, local).
3. **Navegador** — necessário para a prospecção abrir o Maps e os sites dos leads.
4. **Painel** — a skill `prospector-setup` baixa os arquivos do painel deste repositório para a pasta do projeto e cria o banco. Depois é só dar duplo clique em `iniciar-dashboard.bat` (Windows) ou `iniciar-dashboard.command` (Mac): o painel abre em `http://localhost:8765`. Precisa de **Python instalado e no PATH** (no instalador oficial, marque "Add python.exe to PATH"). Sem Python, o `dashboard.html` ainda abre por duplo clique, em modo leitura.

Depois é só dizer no chat: **"configurar o prospector"**.

## Como usar (linguagem natural)

1. **"prospecta nutricionistas em São Paulo"** → o Scout busca, qualifica e o Verifier confere antes de entrar na lista.
2. **"redesenha os 5 melhores"** → o Designer refaz as páginas e gera as imagens que faltam.
3. **"publica na HostGator"** → o Publisher sobe tudo e confirma o HTTPS.
4. **"manda a proposta"** → o Copywriter escreve, o Verifier roda o checklist anti-spam, e o rascunho fica no Gmail pra você revisar.
5. **"prospecta nutricionistas todo dia às 8h"** → vira tarefa agendada e você recebe o resumo.

## Custo (a real)

Cada imagem e cada vídeo consomem cota do seu plano. Padrão sugerido: **3 imagens + 1 vídeo de 6s por lead**, e só para leads já qualificados. Prospecção agendada: uma rodada por dia é um custo previsível.

## Privacidade

A senha da HostGator, o banco de leads e os sites gerados ficam **no seu computador** — o `prospector-config.json` e o `prospector.db` não saem da sua pasta.

---

Feito por **Helio Arreche**.
