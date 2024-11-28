# Manual de Execução do Projeto  
**Blazor em .NET 6**  

Este manual descreve as etapas para configurar a string de conexão no arquivo `appsettings.json`, executar as migrations e inicializar um projeto Blazor em .NET 6.

---

## 1. Pré-requisitos  
Certifique-se de ter os seguintes itens instalados e configurados:  
- .NET SDK 6.0 ou superior.  
- SQL Server configurado no projeto.  
- Um editor de código, como Visual Studio Code ou Visual Studio.  

---

## 2. Configurando a String de Conexão  

### 1. Abrir o arquivo `appsettings.json`  
- Navegue até a raiz do projeto.  
- Localize e abra o arquivo `appsettings.json`.  

### 2. Adicionar ou atualizar a string de conexão  
- Insira a string de conexão na seção `"ConnectionStrings"`.  
- Substitua os valores de exemplo pelos dados reais do seu ambiente:  
```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=SEU_SERVIDOR;Database=SEU_BANCO;User Id=SEU_USUARIO;Password=SUA_SENHA;"
  }
}
```

---

## 3. Executando as Migrations  

### 1. Abrir o terminal ou prompt de comando  
- Navegue até o diretório do projeto onde está localizado o arquivo `.csproj`.  

### 2. Aplicar as migrations ao banco de dados  
- Execute o comando abaixo para criar o banco de dados e aplicar as migrations:  
```bash
dotnet ef database update
```  
- Caso o pacote `Microsoft.EntityFrameworkCore.Tools` não esteja instalado, use:  
```bash
dotnet add package Microsoft.EntityFrameworkCore.Tools
```  

### 3. Verificar o banco de dados  
- Após a execução bem-sucedida do comando, acesse seu banco de dados e confirme se as tabelas foram criadas corretamente.  

---

## 4. Executar o Projeto  

### 1. Inicializar o projeto no servidor local  
- No terminal, ainda no diretório do projeto, execute o comando:  
```bash
dotnet run
```  

### 2. Acessar no navegador  
- Após a inicialização, será exibida a URL do servidor, geralmente algo como:  
  `https://localhost:5001`  
- Abra o navegador e acesse o endereço informado.  

---

## 5. Configurando Segredos de Usuário (Opcional)  

Caso o projeto utilize **User Secrets** para armazenar credenciais sensíveis:  

### 1. Inicializar o gerenciador de segredos  
```bash
dotnet user-secrets init
```  

### 2. Adicionar credenciais  
- Configure valores sensíveis com:  
```bash
dotnet user-secrets set "Chave" "Valor"
```  
**Exemplo:**  
```bash
dotnet user-secrets set "Authentication:Google:ClientId" "SUA_CLIENT_ID"
```  

### 3. Validar configurações  
- Utilize o `IConfiguration` no código para acessar os valores armazenados.  

---

## 6. Solução de Problemas  

### **Erro: Banco de dados não encontrado**  
- Verifique a string de conexão no `appsettings.json`.  
- Confirme se o servidor de banco de dados está em execução.  

### **Erro: Comando `dotnet ef` não reconhecido**  
- Instale as ferramentas do Entity Framework Core:  
```bash
dotnet tool install --global dotnet-ef
```  

### **Erro: Não foi possível localizar o projeto**  
- Certifique-se de estar no diretório correto ou use a opção `--project`:  
```bash
dotnet ef database update --project "Caminho/Para/SeuProjeto.csproj"
```  

---

Com este guia, você poderá configurar, executar e solucionar problemas do seu projeto Blazor em .NET 6 com facilidade! 🚀  
