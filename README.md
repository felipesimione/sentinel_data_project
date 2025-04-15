# Fraud Detection Platform

![Status do Projeto](https://img.shields.io/badge/status-em%20desenvolvimento-yellow)
![Linguagens](https://img.shields.io/badge/linguagens-Python%20%7C%20SQL%20%7C%20NoSQL-blue)
![Infraestrutura](https://img.shields.io/badge/infra-AWS%20%7C%20Docker-orange)
![Licença](https://img.shields.io/badge/licença-MIT-green)

# Projeto de Engenharia de Dados para Detecção de Fraudes

Este repositório contém a estrutura e o código para um projeto abrangente de engenharia de dados focado na construção de uma plataforma robusta e escalável para detecção de fraudes. O objetivo é demonstrar as melhores práticas em arquitetura de dados, processamento batch e streaming, governança de dados e DataDevOps/MLOps, utilizando tecnologias modernas, principalmente no ecossistema AWS.

## Visão Geral

A detecção de fraudes é um desafio crítico para muitas empresas. Este projeto visa construir uma plataforma de dados completa que possa ingerir, processar, analisar e servir dados para identificar atividades fraudulentas em tempo real e em batch, suportando tanto análises exploratórias quanto modelos de machine learning.

## Fases do Projeto

O desenvolvimento está organizado em fases progressivas:

# Fases do Projeto de Detecção de Fraudes

## Fase 1: Fundação e Processamento Batch (3-4 meses)

### 1. Planejamento e Infraestrutura Base
- **Arquitetura e Design**
  - Desenho da arquitetura AWS completa
  - Modelagem de dados e definição de schemas
  - Estratégia de versionamento de dados e schemas
  - Definição de ambientes (dev/staging/prod)

- **Infraestrutura como Código (Terraform)**
  - Implementação completa da infraestrutura via Terraform
  - Módulos para networking, storage, compute e segurança
  - Pipeline de CI/CD para infraestrutura
  - Gestão de estados e workspace segregados por ambiente

- **Governança Básica**
  - Classificação inicial de dados (PII, transacional, comportamental)
  - Políticas de retenção e lifecycle no S3
  - Estrutura de controle de acesso (IAM)
  - Logs de auditoria centralizados (CloudTrail, CloudWatch)

### 2. Ingestão e Armazenamento
- **Data Lake Foundation**
  - Configuração de buckets S3 com particionamento otimizado
  - Estruturação em camadas (raw, cleaned, curated)
  - Estratégia de compressão e formatação (Parquet/ORC)
  - Catalogação básica com AWS Glue

- **Conectores de Ingestão**
  - Desenvolvimento de conectores para diversas fontes
  - Implementação de validações na ingestão
  - Sistema de tracking para arquivos/registros processados
  - Mecanismos de recuperação de falhas

### 3. Processamento e Transformação
- **Pipeline ETL**
  - Jobs Spark (AWS EMR/Glue) para transformações
  - Feature engineering para detecção de fraudes
  - Implementação de janelas temporais (agregações)
  - Validação de qualidade pós-transformação

- **Armazenamento Otimizado**
  - Modelagem dimensional para Redshift
  - Schemas otimizados para DynamoDB
  - Jobs de carga incremental
  - Indices e particionamento para queries frequentes

### 4. Orquestração e Monitoramento Inicial
- **Orchestração com Airflow**
  - DAGs para diferentes fluxos de processamento
  - Tratamento de dependências e falhas
  - Parametrização e configuração por ambiente
  - Backfills automatizados

- **Observabilidade Fundamental**
  - Métricas de execução de pipelines
  - Logs estruturados e centralizados
  - Alertas básicos para falhas críticas
  - Dashboards operacionais iniciais

## Fase 2: Processamento em Tempo Real e Observabilidade (2-3 meses)

### 1. Infraestrutura de Streaming
- **Serviços de Streaming**
  - Implementação de MSK (Kafka gerenciado) ou Kinesis
  - Configuração de tópicos e grupos de consumidores
  - Mecanismos de retenção e compactação
  - Estratégias de escalabilidade

- **Integração com Fontes em Tempo Real**
  - Conectores para sistemas transacionais
  - Captura de dados de mudança (CDC)
  - Simuladores para testes e desenvolvimento
  - Validações em tempo real dos dados ingeridos

### 2. Processamento de Streams
- **Aplicações de Processamento**
  - Implementação com Kafka Streams, Flink ou Spark Streaming
  - Operadores de windowing e agregação
  - Joins entre streams e dados de referência
  - Detecção de anomalias em tempo real

- **Integração Batch-Streaming**
  - Deduplicação entre processos batch e streaming
  - Consistência de visualizações em diferentes timeframes
  - Lambda/Kappa architecture conforme necessidade
  - Reconciliação de dados entre sistemas

### 3. Armazenamento e Serving Layer
- **Hot Storage**
  - Redis/ElastiCache para dados de acesso frequente
  - Mecanismos de TTL e expiração
  - Cache de features para scoring em tempo real
  - Estratégias de fallback

- **Serving Layer**
  - APIs para consulta em tempo real
  - Websockets para atualizações de dashboards
  - Integrações com sistemas de alerta
  - Endpoints para scoring de transações

### 4. Observabilidade Avançada
- **Monitoramento End-to-End**
  - Tracing distribuído (AWS X-Ray, Jaeger)
  - Métricas de latência por componente
  - Visibilidade de throughput e backpressure
  - Health checks avançados

- **Dashboards e Alertas**
  - Dashboards operacionais completos
  - Alertas com thresholds dinâmicos
  - Visualização de fluxo de eventos
  - KPIs de negócio (taxas de fraude, falsos positivos)

- **Diagnostic Tools**
  - Replay de eventos para debugging
  - Dead letter queues para mensagens problemáticas
  - Ferramentas de análise de logs em tempo real
  - Circuit breakers para proteção de sistemas downstream

## Fase 3: DevOps Avançado e Automação (1.5-2.5 meses)

### 1. CI/CD Completo
- **Pipeline para Código e Infraestrutura**
  - Integração contínua para todo código Python e SQL
  - Testes automatizados (unitários, integração, E2E)
  - Validação de infraestrutura (Checkov, tfsec)
  - Estratégias de deployment seguro (canário, blue/green)

- **Automação de Ambientes**
  - Criação de ambientes efêmeros para testes
  - Promoção automática entre ambientes
  - Sincronização de configurações
  - Gestão de segredos centralizada

### 2. Resiliência e Escalabilidade
- **Auto-scaling**
  - Políticas de escalabilidade para todos os componentes
  - Testes de carga automatizados
  - Otimização de custos via scaling dinâmico
  - Escalonamento preditivo baseado em padrões históricos

- **Resiliência**
  - Implementação de padrões de retry e circuit breaker
  - Testes de caos (chaos engineering)
  - Estratégias de fallback gracioso
  - Recuperação automática de falhas (self-healing)

### 3. Otimização Contínua
- **Performance**
  - Benchmarks automatizados
  - Query performance tuning
  - Otimização de código e configurações
  - Análise de padrões de acesso a dados

- **Gestão de Custos**
  - Dashboards detalhados de custos
  - Alertas para anomalias de custo
  - Otimização automática de recursos
  - Análise de ROI por componente

### 4. Documentação e Conhecimento
- **Documentação Automatizada**
  - Geração a partir de código e configurações
  - Wiki centralizada e atualizada automaticamente
  - Catálogo de códigos e scripts reutilizáveis
  - Runbooks para operações comuns

- **Transferência de Conhecimento**
  - Sessões de treinamento
  - Documentação de design decisions
  - Troubleshooting guides
  - Padrões e best practices

## Fase 4: Governança Avançada e MLOps (2-3 meses)

### 1. Governança de Dados Completa
- **Catálogo de Dados Avançado**
  - Implementação completa com AWS Glue ou Apache Atlas
  - Interface self-service para descoberta de dados
  - Documentação rica e searchable
  - Integração com processos de aprovação

- **Linhagem de Dados**
  - Rastreamento completo da origem ao uso
  - Visualização gráfica de dependências
  - Análise de impacto para mudanças
  - Auditoria de acesso e uso

- **Qualidade de Dados**
  - Framework completo (Great Expectations)
  - Monitoramento contínuo de qualidade
  - Scorecards por dataset
  - Alertas para degradação de qualidade

### 2. Compliance e Segurança
- **Frameworks de Compliance**
  - Implementação de controles para PCI-DSS
  - Conformidade com LGPD/GDPR
  - Relatórios automatizados
  - Remediação automática de desvios

- **Segurança Avançada**
  - Criptografia avançada
  - Tokenização de dados sensíveis
  - Controle de acesso baseado em atributos
  - Monitoramento de ameaças internas

### 3. MLOps
- **Feature Store**
  - Implementação centralizada para features
  - Consistência entre treinamento e inferência
  - Versionamento de features
  - Documentação e metadados

- **Pipeline de ML**
  - Automação de treinamento e deployment
  - Versionamento de modelos e dados
  - Experimentos rastreáveis
  - A/B testing automatizado

- **Monitoramento de Modelos**
  - Detecção de drift
  - Análise de performance
  - Alertas para degradação
  - Retreinamento automático

### 4. Ética e Responsabilidade
- **IA Responsável**
  - Framework para avaliação ética de modelos
  - Mitigação de vieses
  - Explicabilidade de decisões
  - Governança para uso de ML

- **Feedback Loop**
  - Captura de feedback de analistas
  - Incorporação de conhecimento de domínio
  - Melhoria contínua baseada em falsos positivos/negativos
  - Medição de impacto de negócio

## Cronograma

| Fase | Duração | Principais Entregas |
|------|---------|---------------------|
| **Fase 1:** Fundação e Processamento Batch | 3-4 meses | • Infraestrutura base implementada via Terraform<br>• Pipeline ETL completo para processamento batch<br>• Data Lake e Data Warehouse operacionais<br>• Governança básica e orquestração |
| **Fase 2:** Processamento em Tempo Real e Observabilidade | 2-3 meses | • Infraestrutura de streaming operacional<br>• Processamento em tempo real com detecção de anomalias<br>• Integração batch/streaming<br>• Sistema completo de observabilidade |
| **Fase 3:** DevOps Avançado e Automação | 1.5-2.5 meses | • CI/CD completo para código e infraestrutura<br>• Automação de operações e escalabilidade<br>• Otimização de performance e custos<br>• Documentação e processos operacionais |
| **Fase 4:** Governança Avançada e MLOps | 2-3 meses | • Catálogo de dados e linhagem completos<br>• Framework robusto de qualidade de dados<br>• Pipeline MLOps automatizado<br>• Monitoramento de modelos e governança ética |
| **Total** | 8.5-12.5 meses | |

## Arquitetura

A arquitetura é baseada principalmente nos serviços da AWS, projetada para ser escalável, resiliente e eficiente em custos. Os principais componentes incluem S3 para Data Lake, Glue para catálogo e ETL, EMR/Databricks para processamento Spark, Redshift para Data Warehouse, DynamoDB para acesso rápido a dados, Kinesis/MSK para streaming, Lambda para processamento serverless, Airflow para orquestração, e CloudWatch para monitoramento.

Diagramas detalhados da arquitetura podem ser encontrados no diretório `/docs/architecture/`.

## Tecnologias Principais

*   **Cloud:** AWS (S3, Glue, EMR, Redshift, DynamoDB, Kinesis/MSK, Lambda, ECS/EKS, CloudWatch, IAM)
*   **Processamento e Desenvolvimento:** Python, Spark, SQL
*   **Orquestração:** Apache Airflow
*   **IaC:** Terraform
*   **Streaming:** Kafka / AWS Kinesis
*   **Banco de Dados:** Redshift (Colunar), DynamoDB (NoSQL)
*   **Containerização:** Docker
*   **Versionamento:** Git
*   **Análise & ML:** Databricks (opcional, mas integrado)
*   **Qualidade de Dados:** Great Expectations (proposto)

## Estrutura do Repositório

O repositório está organizado da seguinte forma para promover modularidade e clareza:
```
sentinel_data_project/
├── .github/
│   ├── workflows/          # CI/CD pipelines (GitHub Actions)
│   └── CODEOWNERS          # Donos do código por diretório
├── docs/
│   ├── architecture/       # Diagramas e documentação da arquitetura
│   ├── data-dictionary/    # Documentação dos dados e schemas
│   └── operation/          # Runbooks e guias operacionais
├── infra/
│   ├── terraform/          # Módulos Terraform por componente AWS
│   ├── docker/             # Configurações Docker para desenvolvimento
│   └── kubernetes/         # Configurações K8s (se aplicável)
├── data-pipeline/
│   ├── batch/
│   │   ├── extraction/     # Jobs de extração (APIs, arquivos, DBs)
│   │   ├── transformation/ # Jobs de transformação e feature engineering (Spark)
│   │   └── load/           # Jobs de carga para DW, NoSQL
│   ├── streaming/
│   │   ├── producers/      # Conectores para fontes de streaming
│   │   ├── processors/     # Lógica de processamento em tempo real (Spark Streaming, Kinesis Analytics)
│   │   └── consumers/      # Consumidores e armazenamento de resultados de stream
│   └── common/             # Código compartilhado (libs, utils)
├── data-models/
│   ├── warehouse/          # Scripts DDL e modelos dimensionais (Redshift)
│   ├── nosql/              # Modelos e schemas para DynamoDB
│   └── feature-store/      # Definições de features (se aplicável)
├── orchestration/
│   ├── airflow/            # DAGs Airflow
│   └── scheduler/          # Configurações de schedulers (se não Airflow)
├── monitoring/
│   ├── alerts/             # Configurações de alertas (CloudWatch, etc.)
│   ├── dashboards/         # Definições de dashboards (CloudWatch, Grafana)
│   └── data-quality/       # Testes e configurações de qualidade de dados
├── notebooks/              # Notebooks para Análise Exploratória de Dados (EDA) e desenvolvimento
├── tests/                  # Testes automatizados (unitários, integração, E2E)
├── utils/                  # Scripts utilitários diversos
├── README.md               # Este arquivo
├── CONTRIBUTING.md         # Guia de como contribuir para o projeto
└── docker-compose.yml      # Configuração do ambiente de desenvolvimento local
```

## Cronograma Sugerido

*   **Fase 1 (Batch):** 2-3 meses
*   **Fase 2 (Streaming):** 1-2 meses
*   **Fase 3 (Governance):** 1-2 meses
*   **Fase 4 (DataDevOps):** 1-2 meses

## Como Começar

1.  Clone o repositório: `git clone https://github.com/felipesimione/sentinel_data_project.git`
2.  Configure o ambiente de desenvolvimento local utilizando `docker-compose up -d`. (Detalhes adicionais podem ser encontrados em `CONTRIBUTING.md`)
3.  Configure suas credenciais AWS.
4.  Explore os módulos Terraform em `infra/terraform/` para provisionar a infraestrutura.
5.  Comece a desenvolver ou executar os pipelines definidos em `data-pipeline/`.

*(Instruções mais detalhadas devem ser adicionadas conforme o desenvolvimento avança, possivelmente no `CONTRIBUTING.md` ou em guias específicos dentro de `docs/operation/`)*

## Contribuição

Consulte `CONTRIBUTING.md` para obter diretrizes sobre como contribuir para este projeto.