# AI Real Estate Lead Agent

Agente de IA para **primeiro atendimento e qualificação de leads imobiliários**, construído com n8n e integrado ao WhatsApp.

O objetivo do projeto é automatizar a etapa inicial do atendimento sem substituir o corretor: a IA recebe o lead, entende o contexto, responde às primeiras dúvidas e organiza informações para que um profissional humano dê continuidade ao atendimento.

## Arquitetura

```text
Meta Ads / Lead
       |
       v
    WhatsApp
       |
       v
     Webhook
       |
       v
      n8n
   /    |    \
texto  áudio  imagem
   \    |    /
       v
 Supabase / Debounce
       |
       v
    AI Agent
       |
       +---- PostgreSQL Chat Memory
       |
       v
    WhatsApp
       |
       v
 Corretor humano
```

## Funcionalidades

- Recepção de mensagens por webhook
- Tratamento de texto, áudio e imagem
- Transcrição de áudio
- Análise de imagens com IA
- Controle de usuário e mensagens com Supabase
- Debounce para agrupar mensagens enviadas em sequência
- Agente de IA para o primeiro atendimento
- Memória de conversa com PostgreSQL
- Resposta automática pelo WhatsApp
- Estrutura preparada para handoff ao corretor

## Stack

- n8n
- Supabase
- PostgreSQL
- OpenAI / LLM
- Groq
- WhatsApp API / UAZAPI
- Webhooks e APIs REST

## Segurança

Este repositório contém uma versão sanitizada do workflow. Credenciais reais, tokens, IDs privados e chaves de API não devem ser commitados.

Configure os serviços diretamente no gerenciador de credenciais do n8n e use variáveis de ambiente quando necessário.

## Como usar

1. Importe `workflow/ai-real-estate-lead-agent.json` no n8n.
2. Configure as credenciais de Supabase, PostgreSQL, OpenAI/Groq e sua API de WhatsApp.
3. Defina `UAZAPI_BASE_URL` e `UAZAPI_TOKEN` no ambiente do n8n.
4. Troque `CHANGE_ME_WEBHOOK_PATH` por um caminho seguro.
5. Revise o System Message do AI Agent para sua operação.
6. Teste texto, áudio e imagem antes de ativar o workflow.

## Observação

O projeto foi desenvolvido como automação de primeiro atendimento. Informações comerciais sensíveis ou que exigem confirmação devem ser encaminhadas para um corretor humano.

## Autor

Douglas Faria dos Santos
