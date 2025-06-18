# 🚀 Deploy - Frontend (React + Expo Dev)

Este documento descreve como configurar e executar o frontend do projeto, que utiliza React (Web/Mobile), Expo Dev para desenvolvimento mobile, e Docker para facilitar o ambiente de execução.

---

## 📦 Pré-requisitos

Certifique-se de que os seguintes softwares estão instalados:

- [Node.js](https://nodejs.org/)
- [npm](https://www.npmjs.com/) ou [yarn](https://yarnpkg.com/)
- [Docker](https://www.docker.com/)
- [Expo CLI](https://docs.expo.dev/get-started/installation/)
- [MongoDB](https://www.mongodb.com/try/download/community) (local ou remoto)
- Dispositivo físico ou emulador (Android/iOS) com o app **Expo Go**

---

## 🐳 Usando Docker (opcional)

Se o projeto possuir um `Dockerfile` ou `docker-compose.yml`, você pode rodar o frontend via container:

```bash
# Construir e subir os containers
docker-compose up --build
