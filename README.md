# Projeto 2: Estudo de Caso e Documentação de Arquitetura em Camadas
**Sistema Escolhido**: https://github.com/magento/magento2

**Grupo**:  
- **Eduardo Viegas Francisco (ra: 2525259)**
- **Rodrigo Aleixo Fidelis Faria (ra: 2503573)**

## Introdução
Magento é uma plataforma de e-commerce open-source, que oferece uma solução completa para gestão de lojas online, desde o cadastro de produtos até o processamento de pedidos e integração com sistemas de pagamento. Sua arquitetura é modular, permitindo fácil personalização e escalabilidade.

## Arquitetura em Camadas do Magento 2

### 1. Camada de Apresentação (Frontend)
- **Recursos:**
  - **Templates:** Arquivos `.phtml` que definem a estrutura HTML das páginas.
  - **Layouts:** Arquivos XML que organizam a estrutura das páginas, definindo quais blocos e templates serão carregados.
  - **JavaScript:** Scripts que adicionam interatividade às páginas, utilizando bibliotecas como jQuery e RequireJS.
  - **CSS:** Arquivos de estilo que definem a aparência visual das páginas, utilizando LESS ou SASS.
- **Processos:**
  - Renderização de Páginas: Geração do HTML final a partir dos templates e layouts.
  - Interação com o Usuário: Manipulação de eventos de usuário, como cliques e submissões de formulários.
  - Validação de Formulários: Verificação dos dados inseridos pelo usuário antes de enviá-los ao servidor.

### 2. Camada de Serviço (Backend) 
- **Recursos:**
  - **Controladores:** Classes que processam as requisições HTTP e retornam as respostas apropriadas.
  - **Modelos:** Classes que representam os dados e a lógica de negócios da aplicação.
  - **Helpers:** Classes utilitárias que fornecem funcionalidades auxiliares para outras partes do sistema.
  - **Serviços:** Classes que encapsulam a lógica de negócios e podem ser reutilizadas em diferentes partes da aplicação.
- **Processos:**
  - Lógica de Negócios: Implementação das regras de negócio, como cálculos de preços e validação de pedidos.
  - Manipulação de Dados: Criação, leitura, atualização e exclusão de dados no banco de dados.
  - Comunicação com o Banco de Dados: Execução de consultas SQL e mapeamento de resultados para objetos PHP.

## Referências
- **MARQUES, Abraão**. Magento 2 Architectural Layers. Publicado em 11 de março, 2021.

