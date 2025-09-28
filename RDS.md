---

## 🛠️ Passo 4 — Criar RDS MySQL

Agora vamos criar o banco de dados MySQL no serviço **Amazon RDS**, que será utilizado pelo WordPress.

---

### 1. Acessar o serviço
- No Console AWS, vá em **RDS**.  
- Clique em **Bancos de dados**.  
- Clique em **Criar banco de dados**.  

---

### 2. Escolher engine
- **Opções de mecanismo:** `MySQL`  
- **Versão:** MySQL 8.0 (mais recente)  

---

### 3. Modelos
- Em **Templates**, selecione **Dev/Test**.  

---

### 4. Configurações básicas
- **Identificador da instância do banco de dados:** `pb-jul2025-rds`  
- **Nome do usuário mestre:** `wpuser`  
- **Senha mestre:** crie uma senha forte (exemplo: `Wp1234!Segura`)  
- **Confirmar senha:** repita a senha  
- *(Opcional)* Nome do banco de dados inicial: `wordpress`  

---

### 5. Tamanho da instância
- **Classe da instância:** `db.t3g.micro` ⚠️ *(requisito do projeto)*  

---

### 6. Alta disponibilidade (Multi-AZ)
- **Implantação Multi-AZ:** `Não criar instância em espera`  
⚠️ Multi-AZ deve ficar **desativado** no projeto.  

---

### 7. Armazenamento
- **Tipo de armazenamento:** `gp3`  
- **Armazenamento alocado:** `20 GiB`  
- **Escalonamento automático de armazenamento:** desmarcado  

---

### 8. Conectividade
- **VPC:** `PB - JUL 2025`  
- **Grupo de sub-redes do banco de dados:** selecione o grupo com as **4 subnets privadas**  
- **Acesso público:** `Não`  
- **Grupo de segurança da VPC:** `SG-RDS` (somente conexões vindas do **SG-EC2**)  
- **Zona de disponibilidade:** `Sem preferência`  

---

### 9. Configurações adicionais
- **Nome do banco inicial:** `wordpress` (caso não tenha colocado antes)  
- **Período de retenção de backup:** `1 dia`  
- **Proteção contra exclusão:** desmarcar  

---

### 10. Tags
Adicionar as **3 tags obrigatórias**:  

| Key        | Value         |
|------------|---------------|
| Name       | PB - JUL 2025 |
| CostCenter | C092000024    |
| Project    | PB - JUL 2025 |

---

### 11. Criar
- Clique em **Criar banco de dados**.  
- O status ficará **Criando** → aguarde até aparecer **Disponível** (5 a 10 minutos).  

---

### 12. Pegar o endpoint
- Clique no banco criado.  
- Na aba **Conectividade e segurança**, copie o **Endpoint**  
  Exemplo:  
