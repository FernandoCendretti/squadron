# Escolhe a imagem oficial do Node.js
FROM node:23.11.0-slim

# Cria e define o diretório de trabalho
WORKDIR /usr/src/app

# Copia o package.json e o package-lock.json
COPY package*.json ./

# Instala as dependências
RUN npm install

# Copia o restante dos arquivos
COPY . .

# Expõe a porta padrão do NestJS
EXPOSE 3000

# Comando para rodar o app
CMD ["npm", "run", "start:dev"]
