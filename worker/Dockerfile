# Usa a imagem base do Go
FROM golang:1.24.2-alpine

# Define o diretório de trabalho
WORKDIR /usr/src/app

# Copia o código Go para o container
COPY . .

# Baixa dependências Go
RUN go mod tidy

# Expõe a porta que o worker irá rodar
EXPOSE 8080

# Comando para rodar o worker
CMD ["go", "run", "main.go"]
