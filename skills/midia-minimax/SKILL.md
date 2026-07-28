---
name: midia-minimax
description: Gera as mídias do projeto com a geração nativa do MiniMax — imagens do site e o vídeo antes/depois da proposta. Use quando o usuário disser "gera as imagens do site", "cria o vídeo da proposta", "vídeo antes e depois", "imagem pro hero", ou quando as skills redesign-premium e proposta-gmail precisarem de mídia própria.
---

# Mídia nativa (imagem e vídeo)

O diferencial desta versão: o próprio MiniMax gera as mídias, na mesma casa. Nada de banco de imagem, nada de assinar outro serviço só pra ter imagem e vídeo.

Use a geração de **imagem** e de **vídeo** nativas do MiniMax Code. Salve os arquivos na pasta do lead — o site publicado não pode depender de link temporário.

## 1. Imagens do site (dentro do redesign)

Quando a skill `redesign-premium` for montar a página, gere as imagens que faltarem em vez de usar banco de imagem.

Regras para o prompt:

- Descreva **o negócio real do lead** (nicho, ambiente, clima), não algo genérico. Ex.: "consultório de nutricionista claro e minimalista, luz natural, plantas, mesa de madeira clara, fotografia profissional".
- Estilo consistente no site inteiro: defina uma linha (paleta, luz, lente) e repita nos outros prompts.
- **Sem texto dentro da imagem** — todo texto do site é HTML por cima. Peça explicitamente "sem texto, sem logotipo, sem marca d'água".
- **Nunca gere rosto humano representando o dono do negócio.** Use ambiente, mãos, detalhes. Rosto inventado passando por "o profissional" é desonesto com o cliente.
- Proporção: hero em paisagem (16:9), blocos internos em 4:3 ou quadrado.

Salve em `sites/[slug]/assets/` e referencie por caminho relativo no HTML.

## 2. Vídeo antes/depois (na proposta)

O gancho comercial: em vez de mandar só um link, a proposta leva um vídeo curto mostrando a transformação.

1. Tenha os dois estados: o site antigo do lead e a página nova publicada.
2. Gere um clipe de **6 segundos** (o suficiente; mais que isso encarece sem ganho) com movimento suave de apresentação — aproximação lenta numa tela mostrando a nova página, luz limpa, clima profissional.
3. A geração de vídeo é assíncrona: **espere concluir** e confirme o arquivo antes de seguir.
4. Salve como `sites/[slug]/proposta.mp4`.
5. **No e-mail o vídeo NÃO vai anexado.** Ele é publicado junto e embutido na página-capa — anexo em e-mail frio aumenta score de spam e medo de abrir. O e-mail continua com um link só: o da capa.

## Custo e bom senso (avise o usuário)

Cada imagem e cada vídeo consomem cota do seu plano. Antes de gerar em lote, informe quantas peças serão criadas. Padrão enxuto sugerido por lead: **3 imagens + 1 vídeo de 6s**. Quem quiser cortar custo, gera só as imagens.

## Regras

- Gere mídia só para leads já qualificados — não gaste em lead que vai ser descartado.
- Se a geração falhar ou demorar demais, siga sem a mídia e avise: o site funciona sem ela; melhor entregar do que travar.
- Registre no `leads.md`/dashboard quais leads já têm mídia, para não gerar duas vezes.
