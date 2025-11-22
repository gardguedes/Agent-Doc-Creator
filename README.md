# Desafio do Azure Frontier Girls – AI Foundry

## 📌 README Completo

***

## 📑 Sumário

* [Introdução](#introdução)
* [🧠 Breve Explicação](#breve-explicação)
    * [O que é um Agente de IA](#o-que-é-um-agente-de-ia)
    * [Modelos LLM – Large Language Models](#modelos-llm--large-language-models)
    * [Azure AI Foundry – AI Agent Services](#azure-ai-foundry--ai-agent-services)
* [🚀 Descrição do Projeto](#descrição-do-projeto)
* [🎯 Objetivo do Agente](#objetivo-do-agente)
* [🛠️ Criação do Agente](#criação-do-agente)
* [➡️ Fluxo do Agente](#fluxo-do-agente)
* [⚙️ Execução do Agente](#execução-do-agente)
* [✅ Conclusão](#conclusão)
* [🔗 Links de Referências](#links-de-referências)

***

## Introdução

Este repositório apresenta o desenvolvimento completo de um **Agente de IA criado no Azure AI Foundry**, como parte do **Desafio Azure Frontier Girls**.

O objetivo é demonstrar como construir um agente capaz de gerar documentos essenciais para uma agência de marketing, automatizando processos e garantindo organização e consistência nas informações de clientes e serviços.

***

## 🧠 Breve Explicação

### O que é um Agente de IA

Um **Agente de Inteligência Artificial** é um sistema de **automação inteligente** projetado para **liberar tempo e recursos**, permitindo que você foque no que realmente importa. Eles:

* Recebem **entradas** (prompts, alertas, mensagens).
* Geram **saídas** (resultados, documentos ou mensagens), podendo chamar **ferramentas** para buscar dados ou executar ações.

### Modelos LLM – Large Language Models

Os **LLMs** (Large Language Models) são modelos de linguagem avançados treinados com grandes quantidades de texto. Eles são a base dos Agentes de IA, sendo capazes de:

* Compreender e gerar linguagem natural de forma coerente e contextual.
* Criar conteúdos complexos, seguindo instruções detalhadas.

### Azure AI Foundry – AI Agent Services

O **Azure AI Foundry** é uma plataforma confiável da Microsoft que capacita os desenvolvedores a impulsionar a inovação e a moldar o futuro com a IA de maneira segura, protegida e responsável. Ele oferece a infraestrutura para **criar, treinar e gerenciar agentes** utilizando modelos de ponta, base de conhecimento e logs de execução.

***

## 🚀 Descrição do Projeto

O projeto consiste na criação de um agente de IA chamado **AgentDocCreator**. Sua função é criar documentos profissionais relacionados ao atendimento de clientes e à execução de serviços de marketing, incluindo **checklists** e avisos de informações importantes necessárias para a prestação do serviço.

#### Problema que o Agente Resolve

Uma agência de marketing médico lida com dois problemas principais:
1.  **Briefings Incompletos:** Os documentos iniciais não contêm toda a informação necessária para o início do serviço.
2.  **Informações Dispersas:** As informações do cliente e dos serviços ficam espalhadas em vários documentos, dificultando a organização e o acesso rápido.

O agente centraliza a criação e validação desses documentos, garantindo que nenhum dado importante seja esquecido.

***

## 🎯 Objetivo do Agente

* Criar documentos de briefing **completos e profissionais** (Site, Tráfego Pago, Redes Sociais).
* **Verificar automaticamente** se informações cruciais estão faltando.
* Gerar **checklists detalhados** por tipo de serviço.
* Utilizar os arquivos de referência adicionados ao **conhecimento** como base para a estrutura dos documentos.

***

## 🛠️ Criação do Agente

O **AgentDocCreator** foi desenvolvido no Azure AI Foundry seguindo as etapas de infraestrutura e configuração abaixo:

### 1) Criar um Grupo de Recursos

**Passo a passo para criar o Grupo de Recursos no Portal do Azure:**
1.  Entre no [Portal do Azure](https://portal.azure.com) com a assinatura habilitada para o Foundry.
2.  No menu lateral, selecione **Grupo de recursos** e clique em **+ Criar**.
3.  Defina o nome do recurso: `rg-froundry-lab-2`
4.  Preencha as demais informações e finalize a criação.

### 2) Criar um Recurso do AI Foundry

**Passo a passo para criar um recurso do AI Foundry:**
1.  Acesse o [Azure AI Foundry portal](https://ai.azure.com) e selecione **Criar projeto**.
2.  Informe o nome do projeto: `proj-doc-creator-2`
3.  Informe a Fábrica de IA: `aif-gard-challenge-2`
4.  Preencha as demais informações e crie o recurso.

### 3) Fazer o Deploy de um Modelo LLM

O modelo LLM (GPT-4o-mini) é o motor de raciocínio do agente.
1.  Acesse o seu projeto no portal do Azure AI Foundry.
2.  Na barra lateral esquerda do projeto, acesse **Meus ativos > Modelos + pontos de extremidade**.
3.  Selecione **Implantar modelo > Implantar modelo base**.
4.  Pesquise e selecione um modelo, como **gpt-4o-mini** na lista de modelos.
5.  Selecione **Confirmar** para abrir a janela de implantação.
6.  Especifique o nome da implantação (Ex: `gpt-4o-mini-2`) e outras configurações, se necessário.
7.  Selecione **Implantar**.
8.  Acesse a página de detalhes da implantação e selecione **Abrir no playground**.


<br>**Tela do Grupo de Recursos e o Recurso do AI Foundry**<br>

![Criação do agente](/Criacao-do-agente/criacao-dos-recursos.jpg)

### 4) Criar um Agente no Foundry

#### Passo 1 – Criação e Configuração

1.  No projeto do Foundry, abra **Criar e personalizar** e clique em **Agentes**.
2.  Na tela "Criar e depurar seus agentes", clique em **+ Novo agente**.<br><br>

![Criação do agente](/Criacao-do-agente/criar-01-agent-primeiro-comando.jpg) <br><br>

3.  No menu à direita em "Configuração" defina os campos:
    * **Nome do agente:** `AgentDocCreator`
    * **Implantação:** `gpt-4o-mini-2`
    * **Descrição do Agente:** "Agente que criar documentos relacionados ao atendimento de clientes e à execução de serviços de marketing."
    * **Temperatura:** `0.3` - *Controla a aleatoriedade. Abaixar a temperatura significa que o modelo produzirá respostas mais repetitivas e determinísticas. Aumentar a temperatura resultará em respostas mais inesperadas ou criativas.*
    * **Top P:** `0.8` - *Controla a aleatoriedade, mas usa um método diferente. Abaixar o Top P restringirá a seleção de tokens do modelo para tokens mais prováveis. Aumentar o Top P permitirá que o modelo escolha tokens com alta e baixa probabilidade.*


#### Passo 2 – Ajuste das Instruções (System Prompt)

As instruções foram ajustadas para focar apenas nos documentos de briefing, acrescentando responsabilidades detalhadas e regras específicas para o contexto de uma agência de marketing:<br><br>

![Ajuste das Instruções](/Criacao-do-agente/criar-02-ajustando-o-prompt.jpg) <br><br>

**Instrução Final (System Prompt):**
"Você é um Analista de Marketing atuando em uma agência de marketing digital. Sua função é criar documentos profissionais relacionados ao atendimento de clientes e à execução de serviços de marketing. Você não responde perguntas sobre qualquer outro assunto. Você criar documentos profissionais relacionados aos serviços de marketing.

**Suas responsabilidades incluem:**
- Criar documentos de briefing, incluindo: Briefing para criação de site, Briefing para gestão de tráfego pago e Briefing para gestão de redes sociais.
- Checar se todas as informações necessárias foram fornecidas.
- Caso falte algo, você deve solicitar as informações adicionais de forma clara e organizada.
- Gerar um checklist completo para cada tipo de serviço, garantindo que todos os itens essenciais estejam contemplados.

**Regras gerais de atuação:**
- Sempre produza documentos organizados, profissionais e objetivos.
- Antes de finalizar qualquer documento, avalie a completude das informações.
- Para o serviço de tráfego pago solicite a criação do BM, conta de anúncio e pixel para o instagram (Meta Ads) e a criação de Tags para o Google Ads.
- Para o serviço de gestão de redes sociais solicite as senhas de acesso e a criação do BM para o instagram (Meta Ads).
- Os checklists devem ser claros, marcados por tópicos e abrangentes.
- Se algo estiver faltando, pergunte ao usuário explicitamente.
- Utilize linguagem formal, porém simples e direta.
- Sempre adapte o briefing ao serviço solicitado."


#### Passo 3 – Adicionar Conhecimento (RAG)

Para garantir que o agente seja preciso e utilize modelos internos da agência, foram incluídos documentos de briefing como base de conhecimento (RAG).
1.  Na tela de configuração do Agente, vá até **Conhecimento** e clique em **+Adicionar**.<br>

![Adicionar Conhecimento](/Criacao-do-agente/criar-03-conhecimento.jpg) <br><br>

2.  Clicar em **Arquivos**. Em **Adicionar Arquivos** selecione **Carregar local** e clique em **Selecionar arquivo local**.
3.  Foram incluídos modelos de briefing do cliente, site e tráfego pago. Clique em **Carregar** e **Salvar**.<br>

![Adicionar arquivos](/Criacao-do-agente/criar-04-arquivos.jpg) <br><br>

***

## ➡️ Fluxo do Agente

O agente utiliza a técnica RAG (Retrieval-Augmented Generation) para consultar os documentos de conhecimento e gerar a resposta: <br>

![Fluxo do Agente](/Fluxo/fluxo.jpg)<br><br>

### Fluxo de Funcionamento<br>

![Fluxo do funcionamento](/Fluxo/funcionamento.jpg) <br><br>

1.  **Usuário envia comando:** O usuário solicita um briefing específico com informações iniciais.
2.  **Agente recebe o comando** pelo chat.
3.  **Consulta ao Conhecimento:** O agente vai aos documentos anexados para obter a estrutura, os campos e os requisitos do briefing.
4.  **Geração:** O agente gera uma resposta para o usuário, estruturando o documento com as informações fornecidas e adicionando o checklist e a solicitação de dados faltantes, com base no conhecimento.
5.  **Saída:** O agente envia essa resposta no chat.

***

## ⚙️ Execução do Agente

### 1) Execução e Validação

1.  **Recebe o comando do usuário:** <br><br>
![Recebe o comando](Execução-e-Teste/02-execucao.jpg) <br><br>
2.  **Gera a resposta** (Documento + Checklist + Solicitações):<br><br>
![Recebe o comando](Execução-e-Teste/03-execucao-01.jpg) <br><br>
![Recebe o comando](Execução-e-Teste/03-execucao-02.jpg) <br><br>
![Recebe o comando](Execução-e-Teste/03-execucao-03.jpg) <br><br>
![Recebe o comando](Execução-e-Teste/03-execucao-04.jpg) <br><br>
![Recebe o comando](Execução-e-Teste/03-execucao-05.jpg) <br><br>
4.  **Detalhes do Thread Logs:** Os **Thread Logs** mostram o passo a passo de raciocínio do agente, incluindo a consulta e o uso dos arquivos de conhecimento para fundamentar a resposta.
    **Raciocínio (Thread Logs):** <br><br>
    ![Thread Logs](Execução-e-Teste/thread-log-01.jpg) <br><br>
    ![Thread Logs](Execução-e-Teste/thread-log-02.jpg) <br><br>
    ![Thread Logs](Execução-e-Teste/thread-log-03.jpg) <br><br>
    **Consulta dos arquivos:** <br><br>
    ![Thread Logs](Execução-e-Teste/thread-log-04.jpg) <br><br>
    ![Thread Logs](Execução-e-Teste/thread-log-05.jpg) <br><br>
    ![Thread Logs](Execução-e-Teste/thread-log-06.jpg) <br><br>
    **Resposta:** <br><br>
    ![Thread Logs](Execução-e-Teste/thread-log-07.jpg) <br><br>

### 2) Testando com um Novo Comando

O agente demonstra consistência e capacidade de adaptar o briefing a um novo cenário:
**Novo Teste:** <br><br>
![Novo comando](Execução-e-Teste/nova-pergunta-01.jpg) <br><br>

**Respostas:** <br><br>
![Respostas](Execução-e-Teste/nova-pergunta-02.jpg) <br><br>
![Respostas](Execução-e-Teste/nova-pergunta-03.jpg) <br><br>
**Thread Logs:** <br><br> 
![Respostas](Execução-e-Teste/nova-pergunta-04.jpg) <br><br>

### 3) Testando Comando Fora do Escopo do Agente

Testes fora do escopo são vitais para validar os limites e as regras do agente.
* **Solicitação:** Criar um **contrato de serviço**, o que não era permitido.<br><br>
![Respostas](Execução-e-Teste/fora-do-escopo-01.jpg) <br><br>

* **Resultado Inicial:** O agente inicialmente aceitou, desrespeitando o foco em apenas **briefings**. <br>
    **Solicitação Fora de Escopo:** <br><br>
  ![Fora do escopo](Execução-e-Teste/fora-do-escopo-02.jpg) <br><br>
  ![Fora do escopo](Execução-e-Teste/fora-do-escopo-03.jpg) <br><br>
  ![Fora do escopo](Execução-e-Teste/fora-do-escopo-04.jpg) <br><br>
  ![Fora do escopo](Execução-e-Teste/fora-do-escopo-05.jpg) <br><br>
  ![Fora do escopo](Execução-e-Teste/fora-do-escopo-06.jpg) <br><br>
  ![Fora do escopo](Execução-e-Teste/fora-do-escopo-07.jpg) <br><br>

* **Ajuste:** Foi necessário incluir regras explícitas nas instruções para que o agente recusasse a criação de documentos não relacionados a briefing, garantindo que ele cumpra estritamente sua função.
    **Ajuste de Regras:** <br><br> ![Ajuste de regras](Execução-e-Teste/fora-do-escopo-08-ajuste-do-prompt.jpg) <br><br>

***

## ✅ Conclusão

O **AgentDocCreator**, desenvolvido no Azure AI Foundry, é uma solução de IA que atende diretamente ao problema de organização e completude de informações em uma agência de marketing.

**Como o Agente de IA Agiliza o Processo de Criação de Briefings e Organização:**

* **Agilidade:** O agente cria instantaneamente documentos que levariam tempo, liberando a equipe para focar em tarefas estratégicas.
* **Padronização:** Garante que todos os briefings sigam o modelo de excelência da agência (baseado no conhecimento anexado).
* **Organização:** Automatiza a **organização das informações do cliente e dos serviços**, gerando um documento único e completo.
* **Redução de Erros:** O checklist e os avisos sobre informações técnicas cruciais asseguram que o serviço comece com todos os pré-requisitos atendidos, minimizando retrabalho.

Esse agente é essencial para agências que buscam **agilidade, precisão e organização** no processo de *onboarding* de clientes.

***

## 🔗 Links de Referências

* [Portal do Azure](https://portal.azure.com)
* [Azure AI Foundry Portal](https://ai.azure.com)
* [Documentação Azure AI Foundry (em português)](https://learn.microsoft.com/pt-br/azure/ai-studio/what-is-azure-ai-studio)
