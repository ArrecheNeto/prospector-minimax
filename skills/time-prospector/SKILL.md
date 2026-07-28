---
name: time-prospector
description: Define o time de agentes do Prospector no MiniMax Code — quem faz o quê na esteira (Scout, Designer, Publisher, Copywriter) e o que o Verifier confere antes de cada entrega sair. Use quando o usuário disser "monta o time", "agent team do prospector", "quem faz o quê", "revisa antes de publicar", ou ao rodar a esteira completa de prospecção.
---

# Time do Prospector (Agent Team)

A esteira tem etapas com fronteiras claras — é o cenário ideal para dividir entre agentes em vez de um só fazendo tudo. Cada papel abaixo tem seu próprio contexto e sua própria skill.

> **Como a esteira roda:** em **sequência**, não todos ao mesmo tempo — o Designer não tem o que refazer antes do Scout achar o lead. O paralelismo real acontece **dentro** de uma etapa: várias buscas ao mesmo tempo (por nicho ou cidade) ou vários sites sendo refeitos ao mesmo tempo.

## Como criar o time no MiniMax Code

No menu esquerdo, em **Agent Team**, clique no **+**. A janela *Create Agent* pede: ícone, **Name** (até 20 caracteres), **Description** (até 100 caracteres) e **Default working folder**.

> Assim que o primeiro agente é criado, aparecem também os padrões do MiniMax — **General**, **Coder** e **Verifier**. O **Verifier não precisa ser criado**: use o que já vem, e é este documento que define o que ele deve conferir.

> **Importante:** aponte a *Default working folder* de TODOS os agentes para a mesma pasta do projeto (onde ficam `prospector-config.json`, `prospector.db` e `sites/`). Se cada agente trabalhar numa pasta diferente, o Designer não acha o lead que o Scout salvou.

Crie estes quatro (o Verifier já existe). As descrições já cabem no limite de 100 caracteres:

| Name | Description (cole assim) |
|---|---|
| `Scout` | Acha e qualifica leads no Google Maps: nota alta, site fraco, com e-mail. |
| `Designer` | Refaz a página do lead em versão premium e gera as imagens que faltam. |
| `Publisher` | Publica página, capa e mídias na HostGator e confere o HTTPS. |
| `Copywriter` | Escreve a proposta anti-spam e cria o rascunho no Gmail. |

As instruções detalhadas de cada papel NÃO vão nesse campo — elas vivem nas skills do plugin. A descrição é só o crachá que diz ao orquestrador quem faz o quê.

## Os papéis

| Agente | O que faz | Skill que segue |
|---|---|---|
| **Scout** | Busca no Google Maps, aplica os filtros (nota, avaliações, site fraco), caça e-mail e WhatsApp | `prospeccao-maps` |
| **Designer** | Refaz a página em versão premium e gera as imagens que faltarem | `redesign-premium` + `midia-minimax` |
| **Publisher** | Publica na HostGator (página, capa, assets e vídeo) e confirma o HTTPS | `deploy-hostgator` |
| **Copywriter** | Escreve a proposta e cria o rascunho no Gmail | `proposta-gmail` |
| **Verifier** | Revisa a entrega de cada um ANTES de sair. Não participou da execução — começa do zero | (este documento) |

O **Scout** pode rodar em paralelo por nicho ou por região: cada sub-agente cuida de uma busca e os resultados são somados no fim, sem duplicar lead já avaliado.

## O Verifier (a trava de qualidade)

Regra que não se quebra: **quem faz não revisa**. O Verifier recebe só o resultado — a página pronta, o e-mail pronto — sem o histórico de como aquilo foi produzido. Ele não sabe as justificativas do autor, então julga o que está na frente dele, e é isso que faz a revisão valer.

O que ele confere em cada etapa:

**Depois do Scout (antes de gastar trabalho no lead)**
- Nota ≥ 4.7 e avaliações ≥ 40 conferem com o que está no perfil?
- O site é próprio mesmo (não é Instagram, linktree ou diretório de terceiros)?
- O e-mail existe e é público? Sem e-mail, o lead não fecha o ciclo — devolver como descartado.
- O motivo do "site ruim" é objetivo e verificável, ou é opinião genérica? Ele vai ser citado na proposta.

**Depois do Designer (antes de publicar)**
- A página abre sem erro e sem seção quebrada em 360, 768, 1024 e 1440px?
- Logo e fotos ORIGINAIS do cliente estão lá? (o cliente precisa se reconhecer)
- Todas as imagens carregam por caminho relativo — nenhuma dependendo de URL temporária?
- O CTA de WhatsApp aparece sem precisar rolar?
- Se falhar em qualquer um: devolve ao Designer com o ponto exato. Não publica.

**Depois do Publisher (antes de mandar pro cliente)**
- As duas URLs abrem em `https://` com cadeado válido?
- Os assets subiram junto (nenhuma imagem quebrada no site publicado)?
- O domínio é apresentável, ou é um subdomínio técnico cheio de números? Se for, PARA: link assim parece golpe.

**Depois do Copywriter (antes do envio)**
- Roda o checklist anti-spam inteiro da skill `proposta-gmail`: 1 link só, sem encurtador, sem palavra-gatilho, sem CAIXA ALTA, assunto ≤ 60 caracteres, primeira linha personalizada de verdade.
- O elogio de abertura é específico e verificável (cita avaliação/credencial real) ou é genérico?
- Tem preço no e-mail? Não pode ter.
- Se falhar: devolve para reescrever. Nada sai no automático.

## Como reportar

O Verifier responde em duas linhas: **aprovado** ou **devolvido**, e no caso de devolução, o item exato que falhou e para qual agente volta. Nada de laudo longo — o valor está em travar o que está errado, não em escrever relatório.

## Tolerância a falha

Se um agente travar (site fora do ar, Maps pedindo captcha, geração de imagem falhando), o orquestrador reatribui ou segue sem aquele item, registrando o motivo — não derruba a esteira inteira. Uma imagem que não gerou não impede a página de ser publicada; um lead que falhou não impede os outros nove.
