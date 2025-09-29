## 🏗️ Launch Template

O Launch Template foi criado para automatizar o provisionamento das instâncias EC2 do projeto WordPress.  

### Configurações Principais

- **Nome:** PB - JUL 2025  
- **AMI (Amazon Machine Image):** Ubuntu Server 22.04 LTS  
- **Tipo de instância:** t3.micro  
- **Rede:** VPC PB - JUL 2025  
- **Subnet:** Subnet pública (auto-assign public IP habilitado)  
- **Security Group:** SG-EC2 (permite acesso HTTP apenas do ALB)  
- **Key Pair:** Criada para acesso SSH (ou usar Session Manager para maior segurança)  
- **Storage:** 8 GB padrão (gp2/gp3)  
- **User Data:** Script de inicialização que instala Docker, WordPress, monta EFS e configura o banco de dados

### Tags Aplicadas

- **Name:** PB - JUL 2025  
- **CostCenter:** C092000024  
- **Project:** PB - JUL 2025  

### Observações

- O User Data garante que a instância EC2 esteja pronta para servir o WordPress automaticamente.
- Substitua os valores em "XXXXX" por suas informações.

## 🖥️ User Data - Launch Template PB JUL 2025

O script abaixo é usado no **Launch Template** para automatizar a instalação do WordPress, montar o EFS e conectar ao RDS.

```bash
#!/bin/bash
# ==========================
# Script User Data - Projeto PB JUL 2025
# ==========================

# Atualizar pacotes
apt update -y
apt upgrade -y

# Instalar dependências
apt install -y curl nfs-common

# Instalar Docker
curl -fsSL https://get.docker.com | sh
systemctl enable docker
systemctl start docker

# Montar EFS (substitua fs-XXXXXXXX e região correta)
mkdir -p /mnt/efs
mount -t nfs4 -o nfsvers=4.1 fs-XXXXXXXX.efs.sa-east-1.amazonaws.com:/ /mnt/efs
echo "fs-XXXXXXXX.efs.sa-east-1.amazonaws.com:/ /mnt/efs nfs4 defaults,_netdev 0 0" >> /etc/fstab

# Criar diretório do projeto
mkdir -p /home/ubuntu/wordpress-project
cd /home/ubuntu/wordpress-project

# Criar arquivo docker-compose.yml
cat > docker-compose.yml << 'EOF'
version: '3.8'
services:
  wordpress:
    image: wordpress:latest
    restart: unless-stopped
    ports:
      - "80:80"
    environment:
      WORDPRESS_DB_HOST: "XXXXXX":3306
      WORDPRESS_DB_USER: "XXXXXX"
      WORDPRESS_DB_PASSWORD: "XXXXXX"
      WORDPRESS_DB_NAME: "XXXXXX"
    volumes:
      - /mnt/efs/wp-content:/var/www/html/wp-content
EOF

# Subir containers
docker compose up -d
