# 🌤️ Chatbot de Clima no Telegram com n8n

Este projeto consiste em um **chatbot no Telegram** desenvolvido utilizando o **n8n** que informa a **temperatura atual de qualquer cidade do Brasil**.

O bot recebe uma mensagem no formato **Cidade,UF**, consulta a API da OpenWeather e retorna ao usuário a temperatura atual de forma simples e amigável.

Exemplo de interação:

**Usuário envia:**

```
São Paulo,SP
```

**Bot responde:**

```
🌤️ A temperatura em São Paulo é de 25°C.
```

Se a cidade não for encontrada ou o formato da mensagem estiver incorreto, o bot retorna uma mensagem de erro orientando o usuário.

---

<img width="1260" height="953" alt="image" src="https://github.com/user-attachments/assets/634bab46-98d9-4a70-929d-86143c1d4b86" />


# 🧠 Como funciona

O workflow no n8n segue o seguinte fluxo:

1. O bot recebe uma mensagem do Telegram.
2. O texto enviado é processado e normalizado (minúsculas e remoção de acentos).
3. O workflow monta a query no formato aceito pela API.
4. O n8n consulta a API da OpenWeather.
5. A temperatura atual da cidade é extraída da resposta.
6. O bot envia a temperatura ao usuário no Telegram.

---

# ⚙️ Pré-requisitos

Antes de importar o workflow, você precisa ter:

* Uma instância do **n8n** instalada ou em execução
* Um **bot do Telegram**
* Uma **API Key da OpenWeather**

---

# 🔑 Variáveis utilizadas

O projeto espera as seguintes credenciais:

| Variável              | Descrição                       |
| --------------------- | ------------------------------- |
| `TELEGRAM_BOT_TOKEN`  | Token do bot criado no Telegram |
| `OPENWEATHER_API_KEY` | Chave da API da OpenWeather     |

---

# 🤖 Criando o Bot no Telegram

1. Abra o Telegram.
2. Procure por **@BotFather**.
3. Execute o comando:

```
/newbot
```

4. Escolha um nome e um username para o bot.
5. O BotFather irá retornar um **token**, que será usado no n8n.

Exemplo de token:

```
123456789:ABCDEF123456abcdef
```

Guarde esse token para usar nas credenciais do n8n.

---

# 🌦️ Obtendo a API Key da OpenWeather

1. Acesse o site da OpenWeather. (https://home.openweathermap.org/users/sign_up)
2. Crie uma conta gratuita.
3. No painel da conta, gere uma **API Key**.

Essa chave será utilizada para consultar a temperatura das cidades.

---

# 📥 Importando o Workflow no n8n

1. Abra o **n8n Editor**.
2. Clique em:

```
Import workflow
```

3. Selecione o arquivo:

```
workflow-chatbot-telegram.json
```

4. O workflow será carregado no editor.

---

# 🔐 Configurando as Credenciais no n8n

## Credencial do Telegram

1. No n8n, clique em **Credentials**.
2. Clique em **New Credential**.
3. Escolha:

```
Telegram API
```

4. Preencha:

```
Access Token → TELEGRAM_BOT_TOKEN
```

5. Salve a credencial.

Depois disso, selecione essa credencial nos nodes:

* **Telegram Trigger**
* **Telegram Send Message**

---

## Credencial da OpenWeather

1. Vá em **Credentials**.
2. Clique em **New Credential**.
3. Escolha:

```
HTTP Query Auth
```

4. Configure:

```
Query Name → appid
Query Value → OPENWEATHER_API_KEY
```

5. Salve a credencial.

Depois associe essa credencial ao node **HTTP Request (OpenWeatherAPI)**.

---

# ▶️ Executando o Chatbot

1. Ative o workflow no n8n.
2. Abra o Telegram.
3. Encontre o seu bot.
4. Envie uma mensagem no formato:

```
Cidade,UF
```

Exemplo:

```
Belo Horizonte,MG
```

---

# 💬 Exemplo de uso

### Entrada do usuário

```
Rio de Janeiro,RJ
```

### Resposta do bot

```
🌤️ A temperatura em Rio de Janeiro é de 29°C.
```

---

# ❌ Exemplo de erro

Caso o usuário envie uma cidade inexistente ou formato inválido:

### Entrada

```
CidadeTeste,ZZ
```

### Resposta

```
❌ Cidade não encontrada. Use o formato Cidade,UF (ex.: São Paulo,SP).
```

---

# 📁 Estrutura do repositório

```
.
├── workflow-chatbot-telegram.json
└── README.md
```

---

# 🚀 Tecnologias utilizadas

* n8n (automação de workflows)
* Telegram Bot API
* OpenWeather API
* JavaScript (processamento da mensagem)

---

# 📌 Observações

* Este repositório **não contém credenciais ou tokens reais**.
* As credenciais devem ser configuradas manualmente no n8n utilizando as variáveis:

  * `TELEGRAM_BOT_TOKEN`
  * `OPENWEATHER_API_KEY`

---

# 👨‍💻 Autor

Projeto desenvolvido como parte de um desafio de automação com **n8n** para criação de chatbots integrados com APIs externas.
