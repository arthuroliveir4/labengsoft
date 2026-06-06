# Terra da Esperança — Sistema de Gestão Institucional

> Sistema desenvolvido como protótipo para a disciplina de Laboratório de Engenharia de Software  
> FATEC Ribeirão Preto · Análise e Desenvolvimento de Sistemas · 2026

---

## Integrantes do Grupo

| Nome |
|------|
| Arthur Carvalho de Oliveira | — |
| Maycon Vinícius de Oliveira | — |
| Nicolas Ferreira Silva | — |

---

## Objetivo do Sistema

A **Terra da Esperança** é uma instituição voltada ao acolhimento de pessoas em processo de reintegração social e reinserção no mercado de trabalho após reabilitação. Toda a sua gestão atualmente é feita de forma manual — cadernos, planilhas isoladas e sem integração —, o que resulta em perda de informações, retrabalho e ineficiência operacional.

O objetivo deste sistema é **digitalizar e centralizar** os processos da instituição, oferecendo:

- Cadastro e acompanhamento de acolhidos
- Triagem e controle de vagas
- Gestão de voluntários com controle de perfis de acesso
- Registro e controle de doações e finanças
- Controle de estoque com alertas automáticos
- Gerenciamento de parcerias (instituições e empresas)
- Geração de relatórios mensais

---

## Módulo Escolhido para o Protótipo

O módulo escolhido para o protótipo funcional é o de **Gestão de Acolhidos**, por ser o núcleo central do sistema e o que mais diretamente impacta a missão da instituição. Ele engloba:

- Cadastro completo do acolhido
- Processo de triagem (aprovação, reprovação ou fila de espera)
- Acompanhamento diário (comportamento, atividades, busca de emprego)
- Controle de vagas disponíveis

---

## Requisitos Atendidos pelo Protótipo

### Requisitos Funcionais

| ID | Descrição | Status |
|----|-----------|--------|
| RF01 | Cadastro de usuários (voluntários) com perfil de acesso | ✅ Implementado |
| RF01.1 | Cadastro de acolhidos com dados completos | ✅ Implementado |
| RF01.2 | Cadastro de empresas doadoras | 🔲 Planejado |
| RF01.3 | Cadastro de empresas parceiras e oportunidades de emprego | 🔲 Planejado |
| RF02 | Registro e controle de recursos em estoque | 🔲 Planejado |
| RF03 | Registro de informações contábeis e financeiras | 🔲 Planejado |

### Requisitos Não Funcionais

| ID | Descrição | Status |
|----|-----------|--------|
| RNF01 | Interface intuitiva para usuários com baixo letramento digital | ✅ Considerado no design |
| RNF02 | Disponibilidade 24/7 | 🔲 Depende de infraestrutura futura |
| RNF03 | Segurança com hash de senha (bcrypt) e controle de perfis | ✅ Implementado na modelagem |
| RNF04 | Escalabilidade — arquitetura preparada para novas funcionalidades | ✅ Estrutura MVC modular |

---

## Tecnologias Utilizadas

| Camada | Tecnologia |
|--------|------------|
| Linguagem | Java |
| Interface gráfica | Java Swing (ou JavaFX) |
| Banco de dados | PostgreSQL |
| Conexão BD | JDBC |
| Controle de dependências | Maven (`pom.xml`) |
| Versionamento | Git / GitHub |
| Hash de senhas | bcrypt (via biblioteca jBCrypt) |

---

## Estrutura do Projeto

```
sistema-acolhimento/
│
├── src/
│   ├── model/                  
│   │   ├── Perfil.java
│   │   ├── Usuario.java
│   │   ├── Acolhido.java
│   │   ├── Triagem.java
│   │   ├── AcompanhamentoDiario.java
│   │   ├── InstituicaoParceira.java
│   │   ├── EmpresaParceira.java
│   │   ├── OportunidadeEmprego.java
│   │   ├── RelatorioMensal.java
│   │   ├── Doador.java
│   │   ├── Doacao.java
│   │   ├── Financa.java
│   │   ├── ItemEstoque.java
│   │   ├── AlertaEstoque.java
│   │   └── ControleVagas.java
│   │
│   ├── dao/                    
│   │   ├── PerfilDAO.java
│   │   ├── UsuarioDAO.java
│   │   ├── AcolhidoDAO.java
│   │   ├── TriagemDAO.java
│   │   ├── AcompanhamentoDiarioDAO.java
│   │   └── ...
│   │
│   ├── controller/             
│   │   ├── AuthController.java
│   │   ├── AcolhidoController.java
│   │   ├── TriagemController.java
│   │   ├── AcompanhamentoController.java
│   │   └── ...
│   │
│   ├── view/                   
│   │   ├── LoginView.java
│   │   ├── DashboardView.java
│   │   ├── AcolhidoView.java
│   │   ├── TriagemView.java
│   │   ├── AcompanhamentoView.java
│   │   └── ...
│   │
│   ├── util/                   
│   │   ├── ConexaoDB.java      
│   │   ├── Autenticacao.java   
│   │   ├── ValidacaoCPF.java
│   │   ├── ValidacaoCNPJ.java
│   │   └── Constantes.java
│   │
│   └── Main.java               
│
├── database/
│   ├── create_tables.sql       
│   ├── inserts_iniciais.sql    
│   └── views_relatorios.sql    
│
│
├── README.md
```

A arquitetura segue o padrão **MVC (Model-View-Controller)** com camada **DAO** separada, garantindo desacoplamento entre interface, regras de negócio e acesso a dados.

---

## O que Foi Implementado

- [x] Modelagem completa do banco de dados com 15 tabelas
- [x] Dicionário de Dados detalhado com tipos, restrições e descrições semânticas
- [x] Script SQL de criação das tabelas (`create_tables.sql`) com chaves primárias, estrangeiras e constraints
- [x] Estrutura de pastas e arquivos do projeto
- [x] Definição de todos os models Java correspondentes às entidades do banco
- [x] Planejamento dos controllers e DAOs para o módulo de Acolhidos
- [x] Definição do sistema de perfis de acesso com permissões granulares (visualizar, editar, excluir, gerar relatório)
- [x] Levantamento e documentação dos Requisitos Funcionais e Não Funcionais

---

## O que Ficou Apenas Planejado

- [ ] Implementação das classes DAO (queries JDBC para cada entidade)
- [ ] Implementação das classes Controller com regras de negócio
- [ ] Desenvolvimento das telas (Views) da interface gráfica
- [ ] Tela de login com autenticação e controle de sessão por perfil
- [ ] Módulo de triagem com lógica de aprovação, reprovação e fila de espera
- [ ] Módulo de acompanhamento diário dos acolhidos
- [ ] Módulo de controle de estoque com alertas automáticos
- [ ] Módulo de doações e controle financeiro
- [ ] Módulo de gestão de parcerias (instituições e empresas)
- [ ] Geração de relatórios mensais em PDF
- [ ] Testes unitários dos controllers
- [ ] Script de inserção de dados iniciais (perfis e administrador padrão)
- [ ] Deploy da aplicação no servidor cedido pelo provedor de internet da instituição

---

## Dificuldades Encontradas

- **Levantamento de requisitos:** Compreender o fluxo real da instituição a partir do texto descritivo.
- **Normalização do banco:** Algumas entidades possuem relacionamentos complexos (ex.: `ACOLHIDO_OPORTUNIDADE` como N:N, triagem que pode ou não gerar um acolhido), o que demandou atenção redobrada para manter a integridade referencial.
- **Definição do escopo do protótipo:** Com 15 entidades e múltiplos módulos, foi necessário priorizar o módulo central (Acolhidos) para garantir uma entrega funcional.
- **Consistência entre documentos:** Alinhar o dicionário de dados, o script SQL e os models Java para que todos reflitam a mesma versão da modelagem.

---

## Próximos Passos para Concluir o Desenvolvimento

1. **Implementar a camada DAO** — codificar os métodos de `INSERT`, `SELECT`, `UPDATE` e `DELETE` para cada entidade usando JDBC.
2. **Implementar os Controllers** — adicionar as regras de negócio (ex.: validar CPF único antes de cadastrar, calcular posição na fila de espera na triagem).
3. **Desenvolver as Views** — construir os formulários e telas de listagem para cada módulo, começando pelo fluxo principal: Login → Dashboard → Acolhidos → Triagem → Acompanhamento.
4. **Implementar o sistema de autenticação** — login com verificação de hash bcrypt e controle de menus/ações por perfil de acesso.
5. **Desenvolver os módulos restantes** — Estoque, Doações, Finanças e Parcerias, nessa ordem de prioridade.
6. **Implementar os alertas de estoque** — lógica automática que dispara notificação quando `quantidade_atual <= quantidade_minima`.
7. **Geração de relatórios** — implementar a exportação de relatórios mensais por acolhido em formato PDF.
8. **Testes** — escrever e executar os testes unitários planejados para os controllers críticos.
9. **Deploy** — configurar a aplicação no espaço de servidor disponibilizado pelo provedor de internet da instituição.
10. **Treinamento dos voluntários** — elaborar um manual de uso básico, dado que muitos usuários possuem baixo letramento digital (RNF01).

---

> Projeto desenvolvido para fins acadêmicos na disciplina de **Laboratório de Engenharia de Software**  
> FATEC Ribeirão Preto — 2026