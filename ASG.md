## ⚖️ Criar Auto Scaling Group (ASG)

### Passo 1 — Acessar o serviço
No Console AWS, vá em **EC2 → Auto Scaling Groups**.  
Clique em **Create Auto Scaling group**.

---

### Passo 2 — Configurações básicas
- **Name**: `pb-jul2025-asg`  
- **Launch template**: selecione o Launch Template criado anteriormente (`pb-jul2025-lt`).  
- **Version**: sempre usar **Latest**.  

---

### Passo 3 — Network
- **VPC**: `PB - JUL 2025`.  
- **Subnets**: escolha **as duas subnets públicas** (ex.: `public-a` e `public-b`).  

---

### Passo 4 — Load Balancing
- Marque **Attach to an existing load balancer**.  
- Selecione **Choose from your load balancer target groups**.  
- Escolha o Target Group criado com o ALB (`pb-jul2025-tg`).  

---

### Passo 5 — Group size
Defina a capacidade do grupo:  
- **Desired capacity**: 2 instâncias  
- **Minimum capacity**: 1 instância  
- **Maximum capacity**: 3 instâncias  

*(Isso garante alta disponibilidade e escalabilidade básica.)*

---

### Passo 6 — Scaling policies (opcional)
Você pode deixar **None** (manual) ou configurar:  
- **Target tracking policy**  
  - Exemplo: Manter CPU em 50%  
  - Minimum: 1, Maximum: 3  

---

### Passo 7 — Notifications (opcional)
Pode deixar em branco (não obrigatório para o projeto).  

---

### Passo 8 — Tags
Adicione as tags obrigatórias:  
- **Name** = `PB - JUL 2025`  
- **CostCenter** = `C092000024`  
- **Project** = `PB - JUL 2025`  

---

### Passo 9 — Criar
Clique em **Create Auto Scaling group**.  

---

📌 **Resultado esperado**
- Auto Scaling Group (`pb-jul2025-asg`) criado.  
- Instâncias iniciadas automaticamente a partir do Launch Template.  
- ALB (`pb-jul2025-alb`) distribuirá o tráfego entre as instâncias.  
- Health checks do ALB garantem que apenas instâncias saudáveis recebam tráfego.  
