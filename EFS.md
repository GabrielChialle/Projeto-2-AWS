---

## 📂 Passo 5 — Criar EFS (Elastic File System)

O **Amazon EFS** será usado para armazenamento compartilhado entre as instâncias EC2, garantindo que o diretório `wp-content` do WordPress seja persistente e sincronizado.

---

### 1. Acessar o serviço
- No Console AWS, vá em **EFS (Elastic File System)**.  
- Clique em **Criar sistema de arquivos**.  

---

### 2. Configurações básicas
- **Nome:** `pb-jul2025-efs`  
- **VPC:** `PB - JUL 2025`  
- Clique em **Personalizar** (para ajustar as opções).  

---

### 3. Rede
- Em **Pontos de montagem (Mount targets)**, selecione as **duas AZs** utilizadas no projeto.  
- Para cada AZ, escolha uma **subnet privada**.  
- Em **Grupos de segurança**, selecione o **SG-EFS** (criado no Passo 2, permitindo tráfego NFS/2049 vindo do SG-EC2).  

---

### 4. Políticas de ciclo de vida (opcional)
- Pode deixar o padrão: **Sem política de ciclo de vida**.  

---

### 5. Criptografia
- Mantenha **Ativar criptografia em repouso** (default).  

---

### 6. Tags
Adicionar as **tags obrigatórias**:  

| Key        | Value         |
|------------|---------------|
| Name       | PB - JUL 2025 |
| CostCenter | C092000024    |
| Project    | PB - JUL 2025 |

---

### 7. Criar
- Clique em **Criar**.  
- Aguarde alguns minutos até o status mudar para **Disponível**.  
