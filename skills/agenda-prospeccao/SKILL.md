---
name: agenda-prospeccao
description: Coloca a prospecção para rodar sozinha em horário fixo usando o Scheduled do MiniMax Code, e entrega o resumo dos leads novos por mensagem. Use quando o usuário disser "prospecta todo dia", "agenda a prospecção", "roda sozinho", "me manda os leads de manhã", "deixa rodando".
---

# Prospecção agendada (rodando sozinha)

Prospecção é trabalho repetitivo de rotina — o tipo de coisa que não deveria depender de você lembrar. Aqui ela vira tarefa agendada: roda no horário marcado e te entrega os leads prontos.

## Montar o agendamento

1. Pergunte o essencial: **nicho(s)**, **cidade/região**, **quantos leads por rodada** (padrão 10) e o **horário** (sugestão: 8h, para os leads estarem prontos quando a pessoa senta).
2. Crie a tarefa no **Scheduled** do MiniMax Code com uma instrução direta, por exemplo:
   > Rode a skill `prospeccao-maps` para [nicho] em [cidade], até [N] leads qualificados. Pule quem já está no `leads.md`. Ao terminar, atualize o banco e o dashboard e me mande um resumo com nome, nota, site atual e o motivo de cada lead novo.
3. Frequência: diária em dia útil costuma ser suficiente. Evite rodar de hora em hora — não aparece lead novo nesse ritmo e só gasta cota.

## Entrega do resultado

Se o usuário usa a integração de mensagem (Telegram), peça o resumo por lá: ele acorda com a lista no celular e decide quais leads quer redesenhar. Sem isso, o resumo fica na própria tarefa e no `dashboard.html`.

O resumo é curto: **quantos leads novos**, os 3 melhores com o motivo, e quantos foram descartados e por quê. Nada de despejar tabela gigante.

## Regras

- **Nunca** agende as etapas seguintes (redesenhar, publicar, enviar proposta) sem aprovação humana. O que roda sozinho é a busca; o que gasta mídia e o que fala com o cliente passa por você.
- A rodada agendada respeita os mesmos filtros de qualificação e nunca duplica lead já avaliado.
- Se a rodada não achar nada, avise assim mesmo — silêncio faz o usuário achar que quebrou.
- Deixe claro ao usuário: cada rodada agendada consome cota do plano. Uma por dia é um custo previsível; várias por dia, não.
