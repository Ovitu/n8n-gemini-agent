# 🤖 Agente de IA com n8n, Gemini e Ferramentas Google

Este projeto é um assistente de IA pessoal construído na plataforma de automação n8n. Ele usa um gatilho do Telegram para receber mensagens, processa essas mensagens usando um **Agente de IA** (AI Agent) avançado, e utiliza o **Google Gemini** como seu cérebro (modelo de chat).

O agente é capaz de manter conversas, lembrar do histórico e usar ferramentas do Google (Gmail e Calendar) para executar tarefas no mundo real.

*(Nota: Embora o nome na imagem seja "Agente de WhatsApp", o gatilho usado neste fluxo é o `Telegram Trigger`. A lógica pode ser facilmente adaptada para o WhatsApp.)*

## 🖼️ Visualização do Fluxo

https://serafimevitor.app.n8n.cloud/workflow/eRU1mbneDJaPmFl7/debug/88)(image_dc8dd5.png
<img width="765" height="391" alt="image" src="https://github.com/user-attachments/assets/eef94e9d-8f93-4844-9a86-e0fb57085034" />


---

## ⚙️ Arquitetura e Componentes

Este fluxo demonstra o poder do novo nó `AI Agent` do n8n, que funciona como um orquestrador central (um "cérebro").

1.  **Gatilho (Trigger): `Telegram Trigger`**
    * Recebe mensagens de usuários em um bot do Telegram.

2.  **Cérebro (Brain): `AI Agent`**
    * É o nó central que recebe a mensagem do usuário.
    * Ele decide, com base na inteligência do Gemini, se deve apenas responder ou se precisa usar uma de suas "ferramentas".

3.  **Inteligência (Model): `Google Gemini Chat`**
    * Conectado ao `AI Agent` como o modelo de chat (Chat Model).
    * É o motor de IA que fornece a capacidade de raciocínio, entendimento e geração de respostas.

4.  **Memória (Memory): `Simple Memory`**
    * Conectado ao `AI Agent`, permite que o bot se lembre de mensagens anteriores na conversa, dando-lhe contexto.

5.  **Ferramentas (Tools):**
    * São as ações que o agente pode decidir executar para responder a uma pergunta.
    * **`Get many events in Google Calendar`**: Permite que o agente verifique a agenda. (Ex: "Eu tenho alguma reunião hoje?").
    * **`Send a message in Gmail`**: Permite que o agente envie e-mails. (Ex: "Envie um e-mail para o cliente X dizendo que vou me atrasar").

6.  **Saída (Output): `Send a text message`**
    * Envia a resposta final (gerada pelo agente) de volta para o usuário no Telegram.

---

## 🛠️ Como Usar (Setup)

Para usar este fluxo de trabalho no seu próprio n8n:

1.  **Baixe o `workflow.json`** deste repositório.
2.  No seu n8n, vá em "Import" > "From File" e selecione o arquivo.
3.  **Configure as Credenciais.** Este fluxo não funcionará sem as credenciais corretas.

---

## 🔑 Credenciais Necessárias

Você precisará criar e adicionar as seguintes credenciais no seu n8n para que os nós funcionem:

* **Telegram:** `Telegram Bot Token` (do BotFather)
* **Google Gemini Chat:** `Google Gemini API Key` (do Google AI Studio)
* **Gmail & Google Calendar:** `Google OAuth2` (Você precisará configurar as permissões no Google Cloud Console para as APIs do Gmail e do Calendar)
