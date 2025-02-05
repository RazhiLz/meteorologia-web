# Bleya - Previsão do Tempo

## Descrição

**Bleya** é uma aplicação web para **previsão do tempo**, construída com **React** e **Vite**. O projeto utiliza a **API OpenWeatherMap** para obter informações climáticas em tempo real e previsões para os próximos 5 dias. A aplicação permite que o usuário consulte o clima de qualquer cidade, exibindo detalhes sobre a temperatura, umidade, pressão atmosférica, sensação térmica e muito mais.

## Funcionalidades

- **Clima Atual**: Exibe as condições meteorológicas atuais de uma cidade, incluindo temperatura, umidade, pressão, sensação térmica e descrição do clima.
- **Previsão dos Próximos 5 Dias**: Fornece a previsão do tempo para os próximos 5 dias, com informações sobre as temperaturas mínimas e máximas, além de ícones representando as condições climáticas de cada dia.
- **Interatividade**: O usuário pode digitar o nome de uma cidade para buscar as informações climáticas em tempo real.

## Como Funciona

A aplicação está estruturada para buscar dados da **OpenWeatherMap API**, que oferece informações climáticas detalhadas. Abaixo estão os principais componentes e como eles interagem:

### **Fluxo de Dados**

1. **Entrada do Usuário**: O usuário digita o nome de uma cidade na barra de pesquisa.
2. **Requisição para a API**: Quando o botão "buscar" é clicado, a aplicação faz duas requisições à API:
   - **Clima Atual**: Uma requisição para a rota `https://api.openweathermap.org/data/2.5/weather?q={cidade}&appid={chave}&lang=pt_br&units=metric` que retorna informações sobre o clima atual.
   - **Previsão de 5 Dias**: Uma segunda requisição para a rota `https://api.openweathermap.org/data/2.5/forecast?q={cidade}&appid={chave}&lang=pt_br&units=metric`, que retorna a previsão do tempo para os próximos 5 dias.
3. **Exibição dos Dados**: Após as requisições, as respostas são utilizadas para atualizar o estado da aplicação e renderizar as informações na tela.

### **API OpenWeatherMap**

A API utilizada no projeto é a **OpenWeatherMap**, que fornece dados climáticos em tempo real e previsões para os próximos dias. O processo de requisição da API é simples:

- **Chave de API**: Para utilizar a API, é necessário se registrar no site e obter uma chave de API (API Key).
- **Rota de Clima Atual**: A rota `/weather` é utilizada para obter informações sobre o clima atual de uma cidade.
  - Exemplo de URL: `https://api.openweathermap.org/data/2.5/weather?q={cidade}&appid={chave}&lang=pt_br&units=metric`
- **Rota de Previsão de 5 Dias**: A rota `/forecast` é usada para obter a previsão para os próximos 5 dias.
  - Exemplo de URL: `https://api.openweathermap.org/data/2.5/forecast?q={cidade}&appid={chave}&lang=pt_br&units=metric`

### **Componentes Principais**

A aplicação é composta por três componentes principais:

1. **`App.jsx`**: Componente de nível mais alto que gerencia o estado da aplicação e as requisições à API.
2. **`WeatherInformations.jsx`**: Componente responsável por exibir as informações do clima atual.
3. **`WeatherInformations5Days.jsx`**: Componente responsável por exibir a previsão para os próximos 5 dias.

#### **1. Componente `App.jsx`**

O **App.jsx** é o ponto central da aplicação. Ele contém o formulário de pesquisa (campo de entrada e botão) e gerencia o estado das informações climáticas.

- **Estados**: Usa `useState` para armazenar os dados do clima atual e da previsão dos próximos 5 dias.
- **Refs**: Usa `useRef` para acessar o valor do campo de entrada onde o usuário digita o nome da cidade.
- **Requisições à API**: Ao clicar no botão de busca, o método `searchCity` é chamado. Este método realiza duas requisições usando a biblioteca **Axios** para obter os dados climáticos atuais e a previsão de 5 dias.
- **Renderização Condicional**: As informações do clima e da previsão só são exibidas após a obtenção dos dados da API, usando a renderização condicional para verificar se os dados existem.

#### **2. Componente `WeatherInformations.jsx`**

Este componente é responsável por exibir as informações do clima atual da cidade. Ele exibe:

- **Temperatura atual**: A temperatura é mostrada em graus Celsius.
- **Condição do tempo**: Uma descrição do clima atual (ex: "Céu limpo", "Chuva").
- **Sensação térmica**: Mostra a temperatura que o corpo humano sente.
- **Umidade e Pressão**: Exibe as condições de umidade e pressão atmosférica.
- **Ícone**: Um ícone que representa visualmente o clima, obtido a partir do código do ícone fornecido pela API.

#### **3. Componente `WeatherInformations5Days.jsx`**

Este componente exibe a previsão do tempo para os próximos 5 dias:

- **Organização dos Dados**: A previsão é organizada por data, com o uso de um dicionário `dailyForecast` para agrupar as previsões diárias e mostrar as condições para cada dia.
- **Conversão de Data**: A data recebida da API é convertida para um formato legível, exibindo o dia da semana e a data.
- **Ícones e Temperaturas**: Assim como no componente anterior, os ícones de clima e as temperaturas mínimas e máximas são exibidos para cada um dos próximos 5 dias.

### **CSS**

A estilização da aplicação foi feita com CSS simples. O arquivo `App.css` contém as regras de estilo para a aparência geral da aplicação, enquanto o arquivo `WeatherInformations.css` e `WeatherInformations5Days.css` são usados para a estilização dos componentes específicos.

### **Exemplo de Requisição**

A requisição para a API OpenWeatherMap, realizada no `searchCity` (em **App.jsx**), é feita com o **Axios**. Aqui está um exemplo de como a URL da API é construída para obter os dados do clima atual:

```js
const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${key}&lang=pt_br&units=metric`
```
## Previsão de 5 Dias

Para obter a previsão de 5 dias, utilizamos a seguinte URL da **API OpenWeatherMap**:

```js
const url5Days = `https://api.openweathermap.org/data/2.5/forecast?q=${city}&appid=${key}&lang=pt_br&units=metric`
```
Essa URL é usada para fazer uma requisição à API, passando o nome da cidade, a chave de API e outros parâmetros para retornar os dados da previsão.

## Requisitos

Para rodar o projeto, você vai precisar das seguintes ferramentas:

- **React**: Biblioteca para construção de interfaces de usuário.
- **Vite**: Ferramenta de build super rápida que é utilizada para compilar e rodar o projeto.
- **Axios**: Biblioteca utilizada para realizar requisições HTTP à API OpenWeatherMap.

## Como Rodar o Projeto

Siga os passos abaixo para rodar o projeto localmente:

1. **Clone o repositório**:
   ```bash
   git clone <URL do repositório>
   cd <diretório do projeto>


## Instale as dependências:

```bash
npm install
```

## Inicie o servidor de desenvolvimento:
```
npm run dev
```

Acesse a aplicação no navegador em http://localhost:5173/.
