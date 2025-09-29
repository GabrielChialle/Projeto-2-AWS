## 🔐 Passo 2 — Criar Security Groups (SG)

Nesta etapa, vamos configurar os **grupos de segurança** que funcionam como firewall virtual da VPC, controlando o tráfego de entrada e saída dos recursos.

---

### 1. Security Group do Load Balancer (SG-ALB)

- Vá em **EC2 → Security Groups → Create security group**
- **Name:** `PB - JUL 2025 - SG-ALB`
- **Description:** `Security Group do Application Load Balancer`
- **VPC:** selecione a VPC criada no passo anterior

**Inbound rules:**
- HTTP (TCP 80) → `0.0.0.0/0`
- HTTPS (TCP 443) → `0.0.0.0/0` *(se for usar SSL depois)*

**Outbound rules:**
- All traffic → `0.0.0.0/0`

**Tags:**
| Key        | Value         |
|------------|---------------|
| Name       | PB - JUL 2025 |
| CostCenter | C092000024    |
| Project    | PB - JUL 2025 |

Clique em **Create**.

---

### 2. Security Group das instâncias EC2 (SG-EC2)

- **Name:** `PB - JUL 2025 - SG-EC2`
- **Description:** `Security Group das instâncias WordPress`
- **VPC:** mesma VPC criada anteriormente

**Inbound rules:**
- HTTP (TCP 80) → Source: **SG-ALB** (apenas o Load Balancer acessa as EC2)
- *(Opcional)* SSH (TCP 22) → Source: **Seu IP** (se necessário, mas o ideal é usar SSM)

**Outbound rules:**
- All traffic → `0.0.0.0/0`

**Tags:** iguais ao anterior.

Criar.

---

### 3. Security Group do Banco de Dados (SG-RDS)

- **Name:** `PB - JUL 2025 - SG-RDS`
- **Description:** `Security Group do banco MySQL/MariaDB`
- **VPC:** mesma VPC

**Inbound rules:**
- MySQL/Aurora (TCP 3306) → Source: **SG-EC2** (somente os servidores de aplicação acessam o banco)

**Outbound rules:**
- All traffic → `0.0.0.0/0`

**Tags:** iguais ao anterior.

Criar.

---

### 4. Security Group do EFS (SG-EFS)

- **Name:** `PB - JUL 2025 - SG-EFS`
- **Description:** `Security Group do Elastic File System`
- **VPC:** mesma VPC

**Inbound rules:**
- NFS (TCP 2049) → Source: **SG-EC2** (somente as instâncias montam o EFS)

**Outbound rules:**
- All traffic → `0.0.0.0/0`

**Tags:** iguais ao anterior.

Criar.

---

### 📌 Resultado

Agora você terá **4 Security Groups criados**:

- **SG-ALB** → aberto para internet  
- **SG-EC2** → só recebe tráfego do ALB  
- **SG-RDS** → só recebe tráfego das EC2  
- **SG-EFS** → só recebe tráfego das EC2  

Ou seja, a **segurança da arquitetura está configurada** 🔒
