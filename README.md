# 🔐 Segurança em SQL

Projeto prático de estudos sobre **segurança e controle de acesso em bancos de dados MySQL**, utilizando como exemplo o banco de dados de uma farmácia.

O objetivo é demonstrar como criar usuários, definir permissões específicas para cada função e administrar acessos para proteger informações sensíveis, como os salários dos funcionários.

## 🎯 Objetivos do projeto

- Criar um banco de dados e suas tabelas.
- Cadastrar dados de produtos e funcionários.
- Criar usuários para diferentes funções.
- Conceder permissões de acesso com `GRANT`.
- Remover permissões com `REVOKE`.
- Consultar privilégios com `SHOW GRANTS`.
- Alterar senhas de usuários.
- Bloquear e desbloquear contas.

## 🧰 Tecnologias

- **MySQL** — sistema de gerenciamento de banco de dados.
- **SQL** — linguagem utilizada para criação, consulta e administração dos dados e permissões.

## 🗂️ Estrutura do repositório

```
Seguran-a_SQL/
├── permissoes_sql.sql
├── Atendente_sql.sql
├── Gerente_sql.sql
└── README.md
```

## 🏥 Cenário utilizado: banco de dados de uma farmácia

O script principal cria o banco `farmacia_seg` e duas tabelas:

| Tabela | Informações |
|---|---|
| `produto` | Nome, preço e quantidade em estoque |
| `funcionario` | Nome, cargo e salário |

A tabela de funcionários contém informações sensíveis. Por isso, o projeto utiliza permissões diferentes para cada perfil de acesso.

## 👥 Perfis e permissões

### Atendente

O usuário `atendente` recebe permissão para consultar somente a tabela de produtos:

```sql
GRANT SELECT ON farmacia_seg.produto
TO 'atendente'@'localhost';
```

### Gerente

O usuário `gerente` recebe permissões de consulta, inserção e atualização no banco:

```sql
GRANT SELECT, INSERT, UPDATE ON farmacia_seg.*
TO 'gerente'@'localhost';
```

Em seguida, o script demonstra como remover a permissão de atualização com `REVOKE`. Ao final dessa etapa, o gerente mantém as permissões de consulta e inserção concedidas pelo exemplo.

## 📚 Arquivos SQL

| Arquivo | Descrição |
|---|---|
| `permissoes_sql.sql` | Cria o banco, as tabelas, insere dados e configura usuários e permissões. Também demonstra alteração de senha e bloqueio/desbloqueio de contas. |
| `Atendente_sql.sql` | Contém consultas de identificação do usuário e testes de acesso às tabelas. |
| `Gerente_sql.sql` | Contém consultas e um exemplo de atualização do preço de um produto. |

## ▶️ Como executar

1. Instale e inicie um servidor MySQL.
2. Abra o MySQL Workbench ou outro cliente SQL.
3. Conecte-se com uma conta administrativa que tenha permissão para criar bancos e usuários.
4. Abra e execute primeiro o arquivo `permissoes_sql.sql`.
5. Conecte-se com os usuários criados para testar os respectivos acessos.
6. Execute os arquivos `Atendente_sql.sql` e `Gerente_sql.sql` nas conexões correspondentes.

> **Importante:** os scripts são exemplos didáticos. As senhas demonstrativas presentes no arquivo SQL devem ser substituídas antes de qualquer uso real. Não utilize credenciais de teste em ambientes de produção.

## 🔒 Conceitos de segurança praticados

- **Princípio do menor privilégio:** cada usuário recebe apenas as permissões necessárias para sua função.
- **Controle de acesso:** separação das permissões entre atendente e gerente.
- **Proteção de dados sensíveis:** restrição de acesso às informações de funcionários.
- **Gerenciamento de contas:** alteração de senhas e bloqueio ou desbloqueio de usuários.
- **Auditoria de permissões:** consulta dos privilégios associados a cada usuário.

## 👨‍💻 Autor

Desenvolvido por **Ives Cezar** como atividade prática de aprendizado em SQL e segurança de bancos de dados.

- GitHub: [@IvesCezar](https://github.com/IvesCezar)

---

⭐ Se este projeto foi útil, considere deixar uma estrela no repositório.
