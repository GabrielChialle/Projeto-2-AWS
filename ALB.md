## 🌐 Criar Application Load Balancer (ALB)

### Passo 1 — Acessar o serviço
No Console AWS, vá em **EC2 → Load Balancers**.  
Clique em **Create Load Balancer** → escolha **Application Load Balancer**.

---

### Passo 2 — Configurações básicas
- **Name**: `pb-jul2025-alb`  
- **Scheme**: Internet-facing  
- **IP address type**: IPv4  

---

### Passo 3 — Network mapping
- **VPC**: selecione a VPC `PB - JUL 2025`  
- **Subnets**: escolha **duas subnets públicas** (ex.: `public-a` e `public-b`).  

---

### Passo 4 — Security Groups
- Selecione ou crie um Security Group para o ALB (`SG-ALB`).  
- Regras mínimas recomendadas:  
  - **HTTP (80)** → Source: `0.0.0.0/0` (internet)  

---

### Passo 5 — Listeners and routing
- Listener padrão: **HTTP : 80 → Forward to Target Group**  

Crie um novo **Target Group**:  
- **Target type**: Instances  
- **Name**: `pb-jul2025-tg`  
- **Protocol**: HTTP  
- **Port**: 80  
- **VPC**: `PB - JUL 2025`  
- **Health checks**:  
  - Protocol: HTTP  
  - Path: `/` (raiz do WordPress)  

---

### Passo 6 — Registrar targets
Neste momento, você pode **pular** a associação de instâncias.  
➡️ O Target Group será usado depois no Auto Scaling Group (ASG).  

---

### Passo 7 — Review e Create
Revise as configurações e clique em **Create load balancer**.  

---

📌 **Resultado esperado**  
- ALB criado (`pb-jul2025-alb`), público, acessível na porta 80.  
- Target Group (`pb-jul2025-tg`) configurado com health checks.  
- Nenhuma instância ainda → serão registradas via Auto Scaling Group.  
- Ao final, você terá um **DNS público do ALB** (ex.: `pb-jul2025-alb-123456.sa-east-1.elb.amazonaws.com`).  
