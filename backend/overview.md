# Backend: Visão Geral

Este serviço implementa a API e funcionalidades de servidor para o projeto Candago-4. É construído com Node.js e TypeScript, usando Express para rotas HTTP e um listener MQTT para ingestão de dados de dispositivos IoT.

### Principais responsabilidades
- **Autenticação**: registro, login e validação de token JWT.
- **Gestão de Dispositivos**: operações CRUD de dispositivos (registrar, listar, atualizar, remover).
- **Coleta de Dados via MQTT**: listener que recebe mensagens de dispositivos (ex.: posições GPS, velocidade, etc) e persiste em banco de dados.
- **Estatísticas e Relatórios**: endpoints que retornam estatísticas (por ex., uso, métricas de dispositivos).
- **Persistência**: comunicação com banco de dados (MongoDB, PostgreSQL ou outro, conforme configuração).
- **Outras rotas auxiliares**: home/status, validação de token, etc.

### Tecnologias e dependências principais
- **Node.js** (v18+)
- **TypeScript**
- **Express**
- **MQTT** (conexão a broker para ingestão IoT)
- **Banco de Dados**: (ex.: MongoDB ou PostgreSQL) — verificar `ORM` ou cliente usado no código.
- **Bibliotecas auxiliares**: 
  - `jsonwebtoken` para JWT
  - `dotenv` para variáveis de ambiente
  - `mongoose` ou `pg`/`typeorm` conforme implementação
  - Testes: Jest ou outro framework configurado
- **Scripts** configurados em `package.json`.

### Estrutura de pastas (resumida)
- `src/routes/` – rotas Express (e.g., login.ts, register.ts, devices.ts, deviceStats.ts, gps.ts, persistence.ts, validate-token.ts, home.ts etc).
- `src/server/` – inicialização do servidor Express e MQTT listener.
- `src/services/` – lógica de negócio e integração com banco/MQTT.
- `src/models/` – esquemas ou entidades (se presentes).
- `src/config/` – leitura de variáveis de ambiente, configuração de conexões.
- `src/utils/` – utilitários comuns.
- `tsconfig.json` – configuração TypeScript.

### Fluxo de dados
1. **Autenticação**: o cliente faz `POST /login` / `POST /register`; recebe JWT.
2. **Operações em Dispositivos**: cliente envia requisições autenticadas para CRUD de devices (`/devices`).
3. **MQTT**: dispositivos IoT publicam em tópicos (ex.: `device/data`); o listener MQTT recebe mensagens JSON, processa e persiste no banco.
4. **Estatísticas**: cliente requisita estatísticas via HTTP (`/deviceStats`, etc), baseada nos dados armazenados.
5. **Validação de Token**: middleware para proteger rotas sensíveis.
6. **Rotas auxiliares**: `/home` ou `/status` para verificar saúde do serviço.

### Observações
- Ajuste as configurações de broker MQTT e banco de dados via variáveis de ambiente (`.env`).
- Garanta que o código de listener MQTT lide com reconexões e formatos de mensagem corretos.
- Adicione logs e tratamento de erros robustos.

Links:
- Repositório Backend: https://github.com/candago-4/backend

