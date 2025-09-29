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

<img width="1101" height="492" alt="image" src="https://github.com/user-attachments/assets/78e1e175-6ee3-45b1-a4e3-bd6d1a301458" />

---

## 🎯 Objetivo do Projeto

Este projeto tem como objetivo desenvolver competências práticas em:

- **Infraestrutura como código**  
- **Provisionamento de recursos em nuvem**  
- **Arquiteturas resilientes**  

utilizando ferramentas modernas e os serviços oferecidos pela **AWS**.

---

## 🛠️ Tecnologias Utilizadas

O projeto foi implementado na AWS utilizando os seguintes serviços e tecnologias:

### ☁️ AWS Cloud
- **Amazon VPC** – Rede isolada para os recursos do projeto.  
- **Amazon EC2** (Ubuntu 22.04 LTS, t3.micro) – Instâncias para rodar o WordPress.  
- **Amazon RDS for MySQL 8.0** (db.t3g.micro) – Banco de dados relacional.  
- **Amazon EFS** – Sistema de arquivos elástico para compartilhamento do diretório `wp-content`.  
- **Elastic Load Balancer (ALB)** – Balanceador de carga para distribuir tráfego entre instâncias EC2.  
- **Security Groups** – Controle de acesso entre camadas (EC2, RDS, EFS).  
- **Launch Template** – Automação do provisionamento de instâncias EC2 com User Data.  

### 🐧 Sistema Operacional
- **Ubuntu Server 22.04 LTS (Jammy Jellyfish)**

### 🐳 Containers
- **Docker 26.x** (instalado via apt no Ubuntu)  
- **Docker Compose v2.x**  

### 🌐 Aplicação
- **WordPress (latest, baseado em PHP 8.2 + Apache 2.4)**  

### 🗄️ Banco de Dados
- **MySQL 8.0 (via Amazon RDS)**  

### 📂 Armazenamento
- **EFS (NFSv4.1)** para persistência do diretório `/wp-content`.  


