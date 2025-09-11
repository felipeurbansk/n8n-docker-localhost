# N8N - Ambiente de Automação Completo

Este projeto fornece um ambiente completo para execução do N8N, uma poderosa plataforma de automação de fluxos de trabalho, junto com todos os serviços necessários para uma operação robusta e escalável.

## 🚀 Características

- **N8N v1.108.1** com arquitetura distribuída
- Banco de dados PostgreSQL com suporte a vetores
- Redis para cache e filas
- Evolution API para integrações
- Interface Coolify para gerenciamento
- Sistema de e-mail com Mailpit
- Armazenamento MinIO
- Websockets com Soketi
- Monitoramento e testes

## 🛠️ Componentes Principais

### Core N8N
- **n8n-app**: Aplicação principal do N8N
- **n8n-webhook**: Serviço dedicado para webhooks
- **n8n-worker**: Processamento de tarefas em background

### Banco de Dados e Cache
- **n8n-postgresql**: Banco de dados principal (pgvector)
- **n8n-redis**: Cache e gerenciamento de filas

### Serviços Auxiliares
- **evolution-api**: API para integrações externas
- **coolify-app**: Interface de gerenciamento
- **coolify-soketi**: Servidor de WebSocket
- **coolify-mailpit**: Servidor de e-mail para desenvolvimento
- **coolify-minio**: Armazenamento de objetos compatível com S3

## 📋 Pré-requisitos

- Docker
- Docker Compose
- Mínimo de 4GB de RAM
- 20GB de espaço em disco

## 🔧 Configuração

1. Clone o repositório:
\`\`\`bash
git clone <repository-url>
cd n8n
\`\`\`

2. Copie o arquivo de exemplo de ambiente:
\`\`\`bash
cp .env.example .env
\`\`\`

3. Configure as variáveis de ambiente no arquivo .env:
\`\`\`env
# Portas dos serviços
N8N_PORT=8181
WEBHOOK_PORT=8282
WORKER_PORT=8383
EVOLUTION_PORT=8484
APP_PORT=8080

# Configurações do PostgreSQL
POSTGRES_USER=postgres
POSTGRES_PASSWORD=password
POSTGRES_DB=n8n

# Configurações do Redis
REDIS_PASSWORD=your_redis_password

# Outras configurações
SERVICE_BASE64_N8N=your_encryption_key
GENERIC_TIMEZONE=America/Sao_Paulo
\`\`\`

## 🚀 Inicialização

1. Inicie os serviços:
\`\`\`bash
docker-compose up -d
\`\`\`

2. Verifique se todos os serviços estão rodando:
\`\`\`bash
docker-compose ps
\`\`\`

## 📍 Portas e Endpoints

- **N8N Interface**: http://localhost:8181
- **N8N Webhook**: http://localhost:8282
- **N8N Worker**: http://localhost:8383
- **Evolution API**: http://localhost:8484
- **Coolify App**: http://localhost:8080
- **Mailpit Dashboard**: http://localhost:8025
- **MinIO Console**: http://localhost:9001

## 🔍 Monitoramento

O projeto inclui healthchecks para os principais serviços:
- PostgreSQL: Verifica conexão a cada 5s
- Redis: Verifica conexão a cada 30s
- N8N: Verifica endpoint a cada 5s

## 💾 Volumes

- **n8n-data**: Dados do N8N
- **n8n-postgresql-data**: Dados do PostgreSQL
- **n8n-redis-data**: Dados do Redis
- **coolify-data**: Dados do Coolify
- **coolify-backups-data**: Backups
- **coolify-minio-data**: Dados do MinIO
- **evolution-data**: Dados da Evolution API

## 🔒 Limites de Recursos

### N8N App
- CPU: 1 core
- Memória: 1000MB

### N8N Webhook & Worker
- CPU: 0.5 core
- Memória: 512MB

### Evolution API
- CPU: 1 core
- Memória: 1000MB

### Coolify App
- CPU: 1 core
- Memória: 1000MB

## 🛠️ Manutenção

### Backups
O sistema inclui configuração para backups automáticos através do Coolify e MinIO.

### Logs
Logs podem ser acessados através do comando:
\`\`\`bash
docker-compose logs -f [service-name]
\`\`\`

## 🔐 Segurança

- Todas as senhas e chaves sensíveis são configuradas via variáveis de ambiente
- Serviços isolados em rede Docker dedicada
- Limites de recursos definidos para cada container
- Healthchecks para monitoramento de saúde dos serviços

## 🤝 Contribuição

1. Faça um Fork do projeto
2. Crie uma Branch para sua Feature (\`git checkout -b feature/AmazingFeature\`)
3. Faça o Commit de suas mudanças (\`git commit -m 'Add some AmazingFeature'\`)
4. Faça o Push para a Branch (\`git push origin feature/AmazingFeature\`)
5. Abra um Pull Request

## 📝 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.
