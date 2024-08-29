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

### 3. Camada de Persistência (Banco de Dados)
- **Recursos:**
  - **Tabelas:** Estruturas que armazenam os dados em formato tabular.
  - Índices: Estruturas que melhoram a velocidade de consultas ao banco de dados.
  - Stored Procedures: Conjuntos de instruções SQL armazenadas no banco de dados que podem ser executadas como uma única unidade.
  
  **Processos:**
  - **Armazenamento e Recuperação de Dados:** Inserção, atualização, exclusão e consulta de dados nas tabelas.
  - **Transações:** Execução de operações de banco de dados de forma atômica, garantindo a integridade dos dados.
  - **Consultas SQL:** Execução de instruções SQL para manipulação e recuperação de dados.
 
  ### 4. Camada de Integração
- **Recursos:**
  - **APIs:** Interfaces de programação que permitem a comunicação entre diferentes sistemas.
  - **Webhooks:** Mecanismos que permitem que um sistema notifique outro sobre eventos em tempo real.
  - **Serviços Externos:** Integrações com sistemas de terceiros, como gateways de pagamento e serviços de envio.
- **Processos:**
  - Integração com Sistemas de Terceiros: Comunicação com APIs externas para realizar operações como processamento de pagamentos e cálculo de frete.
  - Comunicação via APIs REST e GraphQL: Utilização de APIs REST e GraphQL para expor funcionalidades do Magento a outros sistemas e consumir serviços externos.

## Propostas de Melhoria

### Estratégias de Escalabilidade

**Objetivo:** Melhorar a capacidade do Magento 2 para lidar com grandes volumes de tráfego e garantir um desempenho consistente.

#### 1. Escalabilidade Horizontal

**Balanceamento de Carga:**
- **Ferramentas:** Nginx, HAProxy
- **Detalhamento:** Utilizar Nginx ou HAProxy para distribuir o tráfego entre múltiplos servidores web, evitando a sobrecarga de um único servidor. O balanceador de carga monitora a carga de cada servidor e redistribui o tráfego para otimizar o desempenho.

**Cluster de Servidores:**
- **Ferramentas:** Kubernetes, Docker Swarm
- **Detalhamento:** Configurar um cluster de servidores web e banco de dados usando Kubernetes ou Docker Swarm. Essas ferramentas de orquestração de contêineres permitem escalar o ambiente rapidamente, garantindo alta disponibilidade e distribuição eficiente de carga.

**Serviços de Cache:**
- **Ferramentas:** Redis, Varnish
- **Detalhamento:** Implementar Redis para cachear sessões e dados frequentemente acessados, reduzindo a carga no banco de dados. Varnish pode ser configurado como um cache reverso para armazenar páginas HTML geradas e serví-las diretamente aos usuários, melhorando a velocidade de carregamento das páginas.

#### 2. Escalabilidade Vertical

**Otimização do Banco de Dados:**
- **Ferramentas:** MySQL, Percona Server
- **Detalhamento:** Ajustar parâmetros de configuração do MySQL, como `innodb_buffer_pool_size` e `query_cache_size`, para otimizar o desempenho. Percona Server pode ser usado para fornecer uma versão otimizada do MySQL, com melhor gerenciamento de recursos.

**Aprimoramento de Hardware:**
- **Ferramentas:** Atualização de servidores, SSDs, memória RAM
- **Detalhamento:** Aumentar a capacidade do hardware existente adicionando mais memória RAM, utilizando SSDs para armazenamento de banco de dados, e processadores mais rápidos. Isso melhora a capacidade de processamento e o desempenho geral do sistema.

### Estratégias de Refatoração

**Objetivo:** Melhorar a eficiência, a legibilidade e a manutenibilidade do código do Magento 2.

#### 1. Modularização

**Criação de Módulos Customizados:**
- **Ferramentas:** Magento 2 Module Creator, Composer
- **Detalhamento:** Modularizar o código dividindo-o em módulos menores e independentes, cada um responsável por uma funcionalidade específica. O Magento 2 Module Creator facilita a criação de novos módulos, enquanto Composer gerencia as dependências entre esses módulos.

**Utilização de Dependências:**
- **Ferramentas:** Composer, Dependency Injection (DI)
- **Detalhamento:** Utilizar Composer para gerenciar bibliotecas e dependências de código, permitindo o compartilhamento controlado de recursos entre módulos. A injeção de dependências (DI) permite que as classes recebam suas dependências necessárias de maneira declarativa, promovendo flexibilidade e reduzindo o acoplamento entre componentes do sistema.

#### 2. Otimização de Código

**Revisão de Código:**
- **Ferramentas:** Git, SonarQube
- **Detalhamento:** Realizar revisões regulares de código utilizando Git para controle de versões e SonarQube para análise estática de código. Identificar problemas de performance e manutenibilidade, e adotar padrões de codificação consistentes.

**Testes Automatizados:**
- **Ferramentas:** PHPUnit, Selenium, Magento Functional Testing Framework (MFTF)
- **Detalhamento:** Implementar testes unitários com PHPUnit para validar a funcionalidade de componentes individuais, e utilizar Selenium para testes de interface de usuário. O Magento Functional Testing Framework (MFTF) é recomendado para testes funcionais, garantindo que as interações entre módulos estejam funcionando corretamente após alterações no código.

## Referências
- **ADOBE.** Adobe Commerce Developer Documentation. Disponível em: [https://developer.adobe.com/commerce/docs/](https://developer.adobe.com/commerce/docs/). Acesso em: 26 ago. 2024.
- **ADOBE.** Platform Architecture. Disponível em: [https://business.adobe.com/products/magento/platform-architecture.html](https://business.adobe.com/products/magento/platform-architecture.html). Acesso em: 26 ago. 2024.
- **MARQUES, Abraão**. Magento 2 Architectural Layers. Publicado em 11 de março, 2021.
- **COMUNIDADE CLOUD.** Estratégias de Migração para a Nuvem. Disponível em: [https://comunidadecloud.com/estrategias-de-migracao-para-nuvem/](https://comunidadecloud.com/estrategias-de-migracao-para-nuvem/). Acesso em: 26 ago. 2024.

