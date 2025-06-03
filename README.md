# 🕵️‍♂️🤖 Sistema de Criação de Posts para LinkedIn com Agentes de IA

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jvmorva/Google-Gemini-Agentes/blob/main/Gemini_Agentes.ipynb)

Este projeto demonstra a criação de um sistema automatizado para gerar rascunhos de posts para o LinkedIn utilizando múltiplos agentes de IA. Cada agente possui uma função específica dentro do fluxo de trabalho, desde a busca por informações relevantes até a revisão final do conteúdo.

## 🔍 Visão Geral

O coração deste sistema reside em um pipeline de agentes de IA que trabalham em conjunto. Cada agente é treinado para executar uma tarefa específica, e a informação flui de um agente para o outro, permitindo a criação autônoma de conteúdo. O processo pode ser visualizado da seguinte forma:

**Tópico de Entrada ➡️ Agente Buscador ➡️ Agente Planejador ➡️ Agente Redator ➡️ Agente Revisor ➡️ Rascunho de Post Finalizado**

1.  **Agente Buscador:** Pesquisa as últimas notícias e lançamentos relevantes sobre um tópico fornecido.
2.  **Agente Planejador:** Com base nos lançamentos encontrados pelo primeiro agente, planeja os pontos mais relevantes a serem abordados em um post e seleciona o tema mais interessante.
3.  **Agente Redator:** Cria um rascunho de post para o LinkedIn com base no plano fornecido.
4.  **Agente Revisor:** Revisa o rascunho gerado, verificando clareza, concisão, correção e tom.

## 📝 Requisitos

1. Instalar as seguintes bibliotecas:

*   `google-genai` (versão 1.15.0): Para interagir com os modelos da Google AI.
*   `google-adk` (versão 1.0.0): Framework para construção de agentes.
> As versões das bibliotecas acima estão congeladas para garantir compatibilidade, já que estão em constante evolução e podem passar por mudanças frequentes.
*   `IPython`: Para funcionalidades específicas de ambientes de notebook (como exibição de conteúdo formatado). Apenas necessário se executando fora de um ambiente de notebook como Google Colab ou Jupyter para funcionalidades de exibição).

Este projeto também utiliza módulos que fazem parte da biblioteca padrão do Python, como `os`, `uuid`, `datetime`, e `warnings`, que não precisam ser instalados separadamente.

2. Chave de API do Google Gemini.
>*Dica*: Uma maneira fácil de conseguir é através do Google AI Studio - basta acessar - https://aistudio.google.com/app/apikey - fazer login com sua conta Google e clicar em "Create API Key").

## ▶️ Como Usar

1.  Configure sua API Key do Google Gemini.
- No Google Colab:
Armazene sua chave de API do Google Gemini nos secrets do Colab.
Vá em “Secrets” (ícone de chave) na barra lateral esquerda, clique em + Novo secret e crie um secret com o nome GOOGLE_API_KEY e o valor da sua chave.
>Se você optou por importar a API KEY do Google AI Studio, basta clicar em “Chaves da API Gemini” e importá-la.

- Em ambiente local: Defina a variável de ambiente `GOOGLE_API_KEY`.
2.  **Execute todas as células:** Percorra o notebook executando todas as células de código sequencialmente, da primeira à última. Isso instalará as bibliotecas necessárias, configurará o cliente da API e definirá as funções dos agentes.
  
3.  **Forneça o Tópico:** Quando a execução chegar à última célula e você vir a mensagem solicitando o tópico (`❓ Por favor, digite o TÓPICO sobre o qual você quer criar o post de tendências:`), digite o assunto desejado e pressione Enter.

4.  **Acompanhe a Geração do Post:** O sistema de agentes será ativado. Você verá a saída de cada agente no console.

## 🎨 Personalização

*   **Adicionar mais agentes para tarefas como seleção de imagens ou sugestão de horários de postagem.**
*   **Permitir a interação do usuário em etapas intermediárias do pipeline.**
*   **Adicionar ou remover ferramentas:** Inclua outras ferramentas (além do `google_search`) que os agentes podem usar para realizar suas tarefas.
*   **Alterar o público-alvo e a plataforma:** Adapte as instruções do redator e revisor para gerar posts para outras plataformas de redes sociais e públicos.
*   **Implementar agentes adicionais:** Crie novos agentes para adicionar etapas extras ao fluxo de trabalho.
*   Mudar o tom de escrita do Agente Redator (mais formal, informal, divertido, etc.).
*   Alterar os critérios de revisão do Agente Revisor.
*   **Modificar os modelos de linguagem:** Altere o `MODEL_ID` para experimentar diferentes modelos do Gemini.
> *Dica*: Tenha em vista que os modelos da Google AI têm limites de uso, também conhecidos como **Taxa de Requisições por Minuto (RPM)** e **Tokens por Minuto (TPM)**. Se você utilizar um modelo com uma taxa de requisições por minuto muito baixa e tentar fazer muitas chamadas em um curto espaço de tempo, você atingirá rapidamente o limite. Quando isso acontece, a API da Google AI irá rejeitar suas requisições subsequentes por um tempo, retornando um erro.
