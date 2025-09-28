---

## 🖥️ Passo 3 — Criar uma instância EC2

Nesta etapa vamos criar a primeira instância EC2 para testes, que futuramente poderá ser usada como base para **Auto Scaling**.

---

### 1. Acessar EC2
- No console AWS, vá em **EC2 → Instances → Launch instance**.

---

### 2. Configurar a instância
- **Name:** `PB - JUL 2025 - Test Instance`
- **Tags:**
  | Key        | Value         |
  |------------|---------------|
  | Name       | PB - JUL 2025 |
  | CostCenter | C092000024    |
  | Project    | PB - JUL 2025 |

- **AMI (Amazon Machine Image):** Ubuntu (última versão disponível)  
- **Instance type:** `t3.micro` *(elegível para Free Tier)*

---

### 3. Configurar rede
- **VPC:** selecione `PB - JUL 2025` (criada no passo 1)  
- **Subnet:** escolha uma das **subnets públicas** (ex.: `public-a`)  
- **Auto-assign Public IP:** `Enable` (necessário para acessar via internet)

---

### 4. Security Group
- Selecione o **SG-EC2** (criado no passo 2).  
- **Opcional:** adicionar regra de SSH (TCP 22) → somente para **seu IP**.  
- 🔒 **Melhor prática:** usar **AWS Systems Manager (SSM)** em vez de SSH.

---

### 5. Key Pair (para acesso)
- Caso não tenha, crie um **Key Pair (RSA)** e baixe o arquivo `.pem`.  
- Esse arquivo será necessário para **acessar a instância por SSH**.  
  Exemplo de comando no terminal:  

  ```bash
  ssh -i "minha-chave.pem" ubuntu@<Public-IP>

### 6. Storage
Manter o padrão de **8 GB (gp2 ou gp3)**.

---

### 7. User Data (opcional)
Em **Advanced details → User data**, é possível adicionar um script de inicialização  
(por exemplo, instalar Apache ou Nginx automaticamente).

> ℹ️ Nesta documentação não incluímos o script, mas pode ser adicionado futuramente.

---

### 8. Launch
Clique em **Launch instance**.  
Acompanhe em **EC2 → Instances** até o status mudar para *running*.

---

📌 **Resultado esperado**  
Ao final, você terá uma instância **EC2 rodando no Ubuntu**, acessível pela internet (via IP público), protegida pelo **SG-EC2**, pronta para receber configuração manual ou via *User Data*.

