# weather-app

# Aplicação de Previsão do Tempo

## Funcionalidades

- Campo de entrada para digitar o nome da cidade
- Botão de busca que dispara a consulta
- Exibição da previsão do tempo para 3 dias
- Interface organizada e responsiva
- Tratamento de erros (cidade inexistente, problemas de conexão)
- Informações exibidas:
  - Temperatura máxima e mínima
  - Condições do tempo (ensolarado, nublado, chuva etc.)
  - Data de cada previsão
  - Ícone representativo do clima
  - Descrição detalhada das condições

## Tecnologias Utilizadas

### Backend
- **Node.js** com **Express.js**
- **Axios** para requisições HTTP
- **CORS** para permitir requisições cross-origin
- **dotenv** para gerenciamento de variáveis de ambiente

### Frontend
- **Angular** (versão mais recente)
- **TypeScript**
- **CSS** responsivo
- **HttpClient** para comunicação com o backend

### API Externa
- **Visual Crossing Weather API** para dados meteorológicos

## Estrutura do Projeto

```
weather-app/
├── backend/
│   ├── server.js          # Servidor Express.js
│   ├── package.json       # Dependências do backend
│   └── .env              # Configurações de ambiente
└── frontend/
    ├── src/
    │   └── app/
    │       ├── weather/   # Componente de previsão do tempo
    │       ├── app.ts     # Componente principal
    │       └── app.html   # Template principal
    ├── angular.json       # Configurações do Angular
    ├── proxy.conf.json    # Configuração de proxy
    └── package.json       # Dependências do frontend
```

## Como Executar a Aplicação

### Pré-requisitos
- Node.js (versão 18 ou superior)
- npm
- Chave da API do Visual Crossing Weather

### 1. Executar o Backend

```bash
cd backend
npm install
npm start
```

O servidor backend estará rodando em `http://localhost:3000`

### 2. Executar o Frontend

Em um novo terminal:

```bash
cd frontend
npm install
ng serve --host 0.0.0.0 --port 4200
```

O frontend estará disponível em `http://localhost:4200`

## Endpoints da API

### Backend (Express.js)

- `GET /api/health` - Verifica se o servidor está funcionando
- `GET /api/weather/:city` - Obtém a previsão do tempo para uma cidade

#### Exemplo de Resposta da API

```json
{
  "city": "London, England, United Kingdom",
  "forecast": [
    {
      "date": "2025-09-10",
      "tempMax": 20,
      "tempMin": 11,
      "conditions": "Partially cloudy",
      "icon": "partly-cloudy-day",
      "description": "Becoming cloudy in the afternoon."
    },
    {
      "date": "2025-09-11",
      "tempMax": 18,
      "tempMin": 14,
      "conditions": "Rain, Partially cloudy",
      "icon": "rain",
      "description": "Partly cloudy throughout the day with rain."
    },
    {
      "date": "2025-09-12",
      "tempMax": 18,
      "tempMin": 12,
      "conditions": "Rain, Partially cloudy",
      "icon": "rain",
      "description": "Partly cloudy throughout the day with afternoon rain."
    }
  ]
}
```

### Conversão de Temperatura
- A API retorna temperaturas em Fahrenheit
- O backend converte automaticamente para Celsius
- Fórmula: `(°F - 32) × 5/9 = °C`

### Ícones do Tempo
- Mapeamento de ícones da API para emojis
- Representação visual intuitiva das condições climáticas

### Arquitetura REST
- Separação clara entre frontend e backend
- API RESTful seguindo boas práticas
- Comunicação via HTTP/JSON

