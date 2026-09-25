# Architecture

## Fluxo principal

1. **Webhook** recebe o evento enviado pelo provedor do WhatsApp.
2. O workflow identifica o tipo da mensagem.
3. **Texto** segue diretamente para o pipeline.
4. **Áudio** é baixado e transcrito antes de entrar no pipeline.
5. **Imagem** é baixada e interpretada por um modelo multimodal.
6. O **Supabase** é usado para identificar/criar o usuário e armazenar mensagens temporárias.
7. Um mecanismo de **debounce** aguarda mensagens próximas e consolida o conteúdo.
8. O **AI Agent** recebe o texto consolidado e aplica o System Message de primeiro atendimento.
9. **PostgreSQL Chat Memory** mantém o contexto da conversa por sessão.
10. A resposta é enviada novamente ao cliente pelo provedor do WhatsApp.
11. O processo foi pensado para permitir continuidade por um corretor humano.

## Princípio de atendimento

A IA atua na entrada do funil: acolhimento, identificação do interesse e qualificação inicial. O fechamento, negociação e confirmação de condições comerciais permanecem com o profissional humano.

## Segurança

- Não armazene API keys em Notes, Set nodes ou código.
- Não versione arquivos `.env`.
- Use o Credentials Manager do n8n.
- Rotacione imediatamente qualquer segredo que tenha sido publicado.
- Revise exports do n8n antes de cada publicação.
