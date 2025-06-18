# Arquitetura Geral

Descreve componentes e fluxos de dados do sistema.

## Visão em alto nível
O sistema consiste em:
- **Dispositivos IoT**: publicam dados via MQTT (tópico `device/data`).
- **Backend**:
  - Servidor HTTP (Express) expõe API REST para o frontend e outros consumidores.
  - Listener MQTT que escuta tópicos, processa e persiste dados em banco.
  - Banco de dados (MongoDB ou PostgreSQL), armazena usuários, dispositivos, leituras.
- **Frontend**: Aplicativo Expo React Native, consome API REST e exibe dados ao usuário.
- **Infraestrutura** (opcional):
  - Broker MQTT (Mosquitto, EMQX, etc).
  - Servidor de aplicação (contêiner Docker, Kubernetes, etc).
  - Hospedagem do frontend (Expo ou build nativo).
  - Serviço de autenticação externa, se aplicável.

## Diagrama de Componentes
> Insira aqui diagrama exportado (PNG/SVG) de ferramenta visual, ou mermaid se preferir. Exemplo Mermaid:
```mermaid
graph TD
  IoT[Dispositivo IoT] -->|MQTT publish| MQTTBroker
  MQTTBroker --> BackendListener
  BackendListener --> BancoDados[(Banco de Dados)]
  Frontend -->|HTTP REST| BackendAPI
  BackendAPI --> BancoDados

