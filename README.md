# Factory Optimizer - Frontend 💻

Esta é a interface do usuário para o sistema de otimização de produção industrial, desenvolvida com **Vue.js 3**.

## 🎨 Funcionalidades
- **Gestão de Produtos**: Cadastro e visualização dos produtos fabricados.
- **Gestão de Insumos**: Controle de estoque de matérias-primas.
- **Receitas (Vínculos)**: Interface para associar matérias-primas e quantidades necessárias para cada produto.
- **Painel de Otimização**: Visualização da sugestão de produção baseada no maior lucro possível. 

## 🛠️ Tecnologias
- **Vue.js 3**: Framework progressivo para construção da interface.
- **Vite**: Ferramenta de build rápida para o desenvolvimento.
- **Axios**: Cliente HTTP para comunicação com o backend Spring Boot. 

## ⚙️ Pré-requisitos
- **Node.js**: v18.0 ou superior.
- **Backend rodando**: A interface depende da API disponível em `http://localhost:8080`. 

## 🚀 Instalação e Execução
1. Entre na pasta do frontend:
   ```bash
   cd frontend
   ```
2. Instale as dependências:
   ```bash   
   npm install
   ```
3. Inicie o servidor de desenvolvimento:
   ```bash   
   npm run dev
   ```