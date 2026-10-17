# 💸 App de Organização de Finanças Pessoais do João Mafra com Vibe Coding

```markdown
- Seu **prompt final** (PRD);

Você é um Desenvolvedor Front-end Senior especialista em React, Tailwind CSS e UI/UX.
Sua missão é construir um MVP completo e funcional de um App de Organização Financeira Conversacional em uma única resposta. O app deve ser construído "mobile-first" (centralizado na tela em desktops, simulando um celular).

# 1. Tech Stack e Bibliotecas
- React (Componentes Funcionais e Hooks).
- Tailwind CSS para estilização (Design limpo, minimalista, estilo Apple/Nubank, usando tons de verde esmeralda para ações principais).
- Lucide React para ícones.
- Recharts para os gráficos.

# 2. Gerenciamento de Estado (Crucial)
O app deve ser totalmente funcional na interface usando estados locais (useState/useContext) para simular o banco de dados. 
Crie um estado global ou eleve o estado no componente principal para manter:
- `transactions`: Array de objetos { id, type ('income' ou 'expense'), amount, category, description, date }. Inclua 3 transações falsas para começar.
- `goals`: Array de objetos { id, title, target_amount, current_amount }. Inclua 1 meta falsa.
- `balance`: Saldo atual calculado com base nas transações.

# 3. Navegação
Crie um Bottom Navigation Bar (Barra de navegação inferior) fixo com 3 abas: "Chat" (Principal), "Dashboard", e "Metas".

# 4. Telas e Lógica

## TELA 1: CHAT (Aba Principal)
- Interface de chat estilo WhatsApp/iMessage.
- Área de histórico de mensagens (balões do usuário à direita, balões da IA à esquerda).
- Input de texto na parte inferior com botão de enviar.
- LÓGICA DE SIMULAÇÃO DA IA (Importante): Quando o usuário digitar uma mensagem, crie uma função simples que busca números na string.
  - Se a mensagem contiver um número (ex: "gastei 50 no mercado"), a "IA" deve responder automaticamente: "Anotado! Adicionei uma despesa de R$ 50. Seu novo saldo é X".
  - A função deve adicionar automaticamente essa transação ao estado `transactions` e atualizar o `balance`.

## TELA 2: DASHBOARD (Visão Geral)
- Exibir o Saldo Atual em destaque no topo.
- Mostrar um Card com total de Receitas (verde) e total de Despesas (vermelho) do mês.
- Renderizar um gráfico de pizza (PieChart do Recharts) agrupando as despesas por categoria. As categorias devem ser geradas dinamicamente com base no estado `transactions`.

## TELA 3: METAS
- Uma lista de cards mostrando os objetivos financeiros.
- Cada card deve ter: Título da Meta, Valor Atual / Valor Alvo, e uma barra de progresso (Progress Bar) preenchida proporcionalmente.
- Um botão simples "+ Nova Meta" que abre um modal ou prompt para adicionar uma meta ao estado.

# Regras Finais de Execução
- Gere um código bonito, com padding adequado, bordas arredondadas (rounded-2xl) e sombras suaves.
- Não deixe nenhuma funcionalidade de UI pela metade. O chat precisa rolar para baixo, os gráficos precisam renderizar os dados do estado, e a navegação entre as 3 telas deve funcionar perfeitamente sem recarregar a página.
- O idioma da interface e da IA simulada deve ser o Português (PT-BR).
```


## Prints ou pequenos vídeos das interações com a IA;

<img width="1920" height="1032" alt="image" src="https://github.com/user-attachments/assets/71ff07ac-9284-44e0-895f-207039a7b3cd" />
<img width="1920" height="1032" alt="image" src="https://github.com/user-attachments/assets/69fc56c3-0b2c-467c-9826-09a48b39a229" />

RESULTADO: https://id-preview--9fda111b-18ae-404b-a6be-5e5dea7278ef.lovable.app/?__lovable_receipt=mat_5z049dwh4j8mev1en484ab6h4t


## Um resumo do que o seu **App de Finanças Pessoais** faz;

O Fina é um aplicativo de finanças pessoais focado em simplicidade, estruturado em formato mobile com três abas principais:

1. Chat (Assistente Fina)
Lançamentos conversacionais: Você digita em linguagem natural (ex.: "gastei 50 no mercado", "recebi 200 de freela").
Detecção inteligente: Identifica automaticamente se é receita ou despesa, extrai o valor e classifica na categoria correspondente (Mercado, Transporte, Alimentação, Moradia, Lazer, Saúde, Salário, etc.).
Feedback instantâneo: A assistente confirma o registro e calcula o novo saldo em tempo real.
2. Dashboard
Visão Geral: Cartões com saldo total, receitas e despesas do mês.
Gráfico de Categorias: Gráfico de pizza interativo mostrando a divisão percentual dos seus gastos.
Histórico com Exclusão: Lista todas as movimentações mais recentes, com categoria, data e um botão de lixeira para remover registros adicionados por engano. Ao apagar um item, o saldo e os gráficos recalculam na hora.
3. Metas Financeiras
Acompanhamento de Objetivos: Criação de metas com valor alvo e valor já guardado (ex.: Reserva de emergência, Viagem).
Barra de Progresso: Mostra visualmente a porcentagem atingida de cada objetivo.
Gestão Completa: Botões para editar valores/títulos ou excluir metas existentes.


## Uma breve **reflexão sobre o processo**:

  ### O que funcionou bem?  
Tradução rápida de requisitos (PRD para código): A transformação da proposta conceitual em uma interface funcional foi imediata. A IA estruturou a arquitetura em abas (Chat, Dashboard, Metas), adotou o padrão visual mobile e entregou componentes prontos para uso desde o primeiro rascunho.
Processamento de linguagem natural simples e eficaz: A lógica de regex para categorização e extração de valores no chat ("gastei 50 no mercado") atendeu perfeitamente ao caso de uso sem precisar de chamadas pesadas de API externa.
Iterações pontuais e modulares: Adicionar a edição/exclusão de metas e o histórico de transações com exclusão foi um processo cirúrgico: a base existente foi preservada enquanto novas funcionalidades e regras de recálculo reativo foram acopladas sem atrito.

  
  ### O que não funcionou como o esperado?  
Erros de ciclo de vida e runtime (o bug do destroy is not a function): No React, um useEffect espera que o retorno seja exclusivamente uma função de limpeza (cleanup) ou undefined. Ao usar endRef.current?.scrollIntoView(), em versões recentes de alguns navegadores a chamada retorna um valor, fazendo o React interpretá-lo como cleanup e quebrar a tela ao trocar de aba.
Atenção aos detalhes de compatibilidade: Bibliotecas de terceiros (como gráficos do Recharts e utilitários auxiliares) exigem atenção redobrada com tipos e dependências que não estão em uso para evitar quebras silenciosas no build inicial.
Persistência de dados volátil: Como o estado foi mantido apenas em memória (useState), recarregar o navegador ainda reseta as transações e metas aos valores padrão — um ponto de melhoria natural para as próximas etapas.


  
  ### O que aprendeu sobre conversar com IAs?
"Aprendi que quanto mais detalhes forneço, melhor ela trabalha, e uma conversa com IA é simples, fácil e prática.



