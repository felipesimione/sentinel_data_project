# Guia de Contribuição - Plataforma de Detecção de Fraudes

Toda contribuição é bem-vinda, desde a correção de bugs e melhorias na documentação até a implementação de novas funcionalidades. Para garantir um processo organizado e colaborativo, pedimos que siga as diretrizes abaixo.

## Código de Conduta

Esperamos que todos os participantes sigam nosso [Código de Conduta](CODE_OF_CONDUCT.md). Por favor, leia-o para entender os padrões de comportamento esperados em nossa comunidade. Queremos manter um ambiente acolhedor e respeitoso para todos.

## Como Contribuir?

Existem várias maneiras de contribuir:

*   **Reportando Bugs:** Se encontrar um bug, por favor, acesse nosso slack e envie no canal `@bugs`.
*   **Sugerindo Melhorias ou Novas Funcionalidades:** Tem uma ideia para melhorar o projeto ou adicionar uma nova funcionalidade? Envie no nosso canal `@melhorias` dentro do nosso slack.
*   **Enviando Pull Requests:** Se você deseja corrigir um bug, implementar uma funcionalidade ou melhorar a documentação, pode fazer isso através de um Pull Request (PR). Siga os passos detalhados na seção "Processo de Desenvolvimento (Pull Request)" abaixo.

## Configuração do Ambiente de Desenvolvimento

Para começar a desenvolver, siga estes passos:

1.  **Pré-requisitos:**
    *   Git
    *   Docker e Docker Compose
    *   Python (verifique a versão recomendada no projeto, ex: 3.9+)
    *   (Opcional, dependendo da tarefa) AWS CLI configurada
    *   (Opcional, dependendo da tarefa) Terraform

2.  **Fork o Repositório:** Crie um fork deste repositório na sua conta do GitHub.

3.  **Clone o seu Fork:**
    ```bash
    git clone https://github.com/SEU_USUARIO/fraud-detection-platform.git
    cd fraud-detection-platform
    ```

4.  **Configure o Ambiente Local (usando Docker):**
    A maneira recomendada de configurar o ambiente de desenvolvimento é usando Docker Compose. Isso garante consistência entre os ambientes.
    ```bash
    docker-compose up -d
    ```
    *Nota: Pode haver passos adicionais dependendo da configuração específica (ex: criação de arquivos `.env`, configuração de credenciais AWS para testes locais). Consulte a documentação principal ou guias específicos em `/docs`.*

## Processo de Desenvolvimento (Pull Request)

1.  **Crie uma Branch:** A partir da branch principal (`main` ou `master`), crie uma nova branch para suas alterações. Use um nome descritivo, prefixado com `feature/`, `fix/`, `docs/`, `refactor/`, etc.
    ```bash
    git checkout main  # Ou a branch principal do projeto
    git pull origin main # Garanta que sua branch principal local esteja atualizada
    git checkout -b feature/minha-nova-funcionalidade # Exemplo
    # ou
    git checkout -b fix/corrige-bug-login # Exemplo
    ```

2.  **Faça suas Alterações:** Implemente sua funcionalidade, correção ou melhoria. Siga as [Diretrizes de Código](#diretrizes-de-código) e [Padrões de Teste](#testes).

3.  **Escreva Testes:** Adicione testes unitários e/ou de integração para cobrir suas alterações. Queremos garantir a qualidade e a estabilidade do código. Coloque os testes no diretório `tests/`.

4.  **Execute Testes e Linters:** Antes de submeter, garanta que todos os testes passam e que o código está formatado corretamente e sem erros de lint.
    ```bash
    # Exemplo (os comandos reais podem variar)
    docker-compose exec meu-servico pytest tests/
    docker-compose exec meu-servico flake8 .
    docker-compose exec meu-servico black . --check
    ```
    *Nota: Pode haver um comando `make test` ou `make lint` configurado para facilitar.*

5.  **Faça Commits:** Escreva mensagens de commit claras e descritivas. Recomendamos seguir o padrão [Conventional Commits](https://www.conventionalcommits.org/).
    *   Exemplo: `feat: Adiciona endpoint para consulta de transações por usuário`
    *   Exemplo: `fix: Corrige cálculo de agregação na janela de 1 hora`
    *   Exemplo: `docs: Atualiza README com instruções de setup`

6.  **Envie para o seu Fork:**
    ```bash
    git push origin feature/minha-nova-funcionalidade
    ```

7.  **Abra um Pull Request (PR):** Vá até o repositório original no GitHub e abra um Pull Request da sua branch para a branch principal (`main` ou `master`) do repositório original.
    *   **Título:** Use um título claro e conciso, seguindo o padrão dos commits se possível.
    *   **Descrição:** Descreva *o quê* foi alterado e *por quê*. Se o PR corrige uma Issue existente, mencione-a usando `Closes #ID_DA_ISSUE` ou `Fixes #ID_DA_ISSUE`. Inclua detalhes sobre como testar suas alterações, se aplicável.

8.  **Revisão de Código:** Os mantenedores do projeto revisarão seu PR. Esteja preparado para responder a comentários e fazer ajustes solicitados. A colaboração é chave!

9.  **Merge:** Após a aprovação, um mantenedor fará o merge do seu PR. Parabéns e obrigado pela sua contribuição!

## Diretrizes de Código

*   **Python:** Siga as convenções do [PEP 8](https://www.python.org/dev/peps/pep-0008/). Use ferramentas como `Black` para formatação automática e `Flake8` ou `Pylint` para linting.
*   **Terraform:** Siga as boas práticas de escrita de código Terraform (ex: use módulos, variáveis, formate o código com `terraform fmt`).
*   **Clareza:** Escreva código legível e bem comentado (quando o comentário adicionar valor e não apenas repetir o código).
*   **Documentação:** Se suas alterações introduzem novas funcionalidades, APIs ou modificam comportamentos existentes, atualize a documentação relevante (README, arquivos em `/docs`, docstrings).

## Testes

*   Testes são fundamentais neste projeto.
*   Adicione testes unitários para funções e classes individuais.
*   Adicione testes de integração para fluxos que envolvem múltiplos componentes (ex: um pipeline ETL, interação com banco de dados).
*   Garanta que seus testes cubram os casos de sucesso e os casos de erro/borda.
*   Todos os testes devem passar antes de um PR ser considerado para merge.

## Dúvidas?

Se tiver alguma dúvida sobre como contribuir, sobre o processo ou sobre alguma parte específica do código, sinta-se à vontade para enviar sua dúvida no nosso canal `@duvidas` no nosso slack.

Obrigado novamente por dedicar seu tempo e esforço a este projeto!