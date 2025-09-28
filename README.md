# 🌐 Projeto AWS - Infraestrutura em Nuvem

Este projeto tem como objetivo a criação de uma infraestrutura completa na **AWS**, utilizando VPC, Subnets, Security Groups, EC2, RDS, EFS e um **Application Load Balancer (ALB)**.

---

## 📋 Recursos Criados

- **VPC e Subnets personalizadas** (base da rede)
- **Security Groups** (regras de firewall)
- **Instâncias EC2** (teste e depois Auto Scaling)
- **RDS** (banco de dados relacional)
- **EFS** (armazenamento compartilhado)
- **Application Load Balancer (ALB)**

---

## 🚀 Passo 1 — Criar a VPC (rede)

### 1. Acessar o Console AWS
- Entrar em [console.aws.amazon.com](https://console.aws.amazon.com).
- No canto superior direito, escolha a **região Norte da Virgínia** (us-east-1).

### 2. Ir para o serviço **VPC**
- No menu superior, clique em **Services**.
- Pesquise por **VPC** e clique.

### 3. Criar nova VPC com assistente
- Clique em **Create VPC**.
- Escolha a opção **VPC and more** ✅.

### 4. Preencher os campos
- **Name tag auto-generation** → `PB - JUL 2025`
- **IPv4 CIDR block** → `10.0.0.0/16`
- **Number of Availability Zones (AZs)** → `2`
- **Number of public subnets** → `2`
- **Number of private subnets** → `4`
- **NAT gateways** → `1 NAT Gateway (mais barato)`
- **VPC endpoints** → `None`

### 5. Tags obrigatórias
No final do formulário, em **Tags**, adicione:

| Key         | Value             |
|-------------|-------------------|
| Name        | PB - JUL 2025     |
| CostCenter  | C092000024        |
| Project     | PB - JUL 2025VPC and more |

### 6. Criar a VPC
- Clique em **Create VPC**.
- Em alguns segundos a AWS cria:
  - VPC (rede principal)
  - 2 subnets públicas (com internet)
  - 4 subnets privadas (sem internet direta)
  - Internet Gateway
  - NAT Gateway
  - Route Tables configuradas automaticamente

---

## 📌 Próximos Passos
- Configurar **Security Groups**
- Criar instâncias **EC2**
- Criar banco de dados **RDS**
- Configurar **EFS**
- Configurar **Application Load Balancer (ALB)**

---

## 🏷️ Tags do Projeto
- **Name:** PB - JUL 2025
- **CostCenter:** C092000024
- **Project:** PB - JUL 2025VPC and more
