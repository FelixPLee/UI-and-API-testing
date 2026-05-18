# 🎯 Projeto de Quality Assurance: UI & API Testing

Bem-vindo ao repositório do desafio técnico de QA. Este projeto contém a documentação, os roteiros de teste e as evidências de validação para duas aplicações distintas: a interface web **Sauce Demo** e a API **Restful-Booker**.

O objetivo deste repositório é demonstrar a aplicação de boas práticas em testes de software, análise de requisitos, identificação de vulnerabilidades e documentação de bugs.

---

## 📂 Estrutura de Diretórios e Navegação

O projeto foi segmentado em duas frentes principais (UI e API) para facilitar a navegação. Abaixo está o guia de onde encontrar cada artefato:

### 1. `/api-testing`
Esta pasta concentra todo o escopo de testes voltado para o back-end e validação de contratos da API Restful-Booker.

*   **`/Documentation`**: O coração dos testes de API. Aqui você encontrará:
    *   `API-test-case.md`: O plano de testes detalhado, contendo os cenários (identificados como TC-API-XXX), objetivos, pré-requisitos e resultados esperados para cada endpoint.
    *   `relatorio-testes-api.md`: Um relatório analítico profundo sobre a qualidade da API, incluindo sugestões de melhorias arquitetônicas e um mapeamento crítico de vulnerabilidades de segurança (como falhas de limitação de taxa e riscos de força bruta).
    *   Arquivos `.json`: A Collection exportada e o Environment (com as variáveis de ambiente, como `{{base_url}}` e `{{token}}`) prontos para serem importados e executados no Postman.
*   **`/Evidences`**:
    *   `/Images`: Capturas de tela dos *status codes*, *payloads* de requisição e respostas do servidor.
    *   `/Videos`: Gravações curtas demonstrando fluxos complexos, como o ciclo de vida completo de uma reserva (CRUD).

### 2. `/ui-testing`
Esta pasta contém as validações funcionais, visuais e de acessibilidade da plataforma de e-commerce Sauce Demo.

*   **`/Documentation`**:
    *   `UI-test-case.md`: O descritivo passo a passo dos casos de teste (identificados como TC-XXX), cobrindo desde a autenticação até o fluxo de *checkout* completo e o tratamento de mensagens de erro.
    *   `relatorio-testes-ui.md`: Uma análise holística da interface, detalhando o comportamento de diferentes perfis de usuários (incluindo falhas injetadas propositalmente), problemas de acessibilidade e falhas lógicas no fluxo de compra.
*   **`/Evidences`**:
    *   `/Images`: Capturas de tela demonstrando os bugs visuais, falhas de alinhamento e mensagens de sistema disparadas durante os testes.
    *   `/Videos`: Gravações de tela evidenciando comportamentos dinâmicos, como lentidão extrema (falhas de performance) ou travamentos durante a navegação.

---

## 🚀 Como Executar os Testes

### Para os testes de API:
1. Clone este repositório.
2. Abra o seu cliente de API favorito (recomendado: Postman).
3. Vá em `Import` e selecione os arquivos JSON localizados na pasta `api-testing/Documentation`.
4. Selecione o ambiente (Environment) importado no canto superior direito.
<!--TODO AJUSTAR!!!!-->

### Para a leitura dos roteiros de UI:
1. Navegue diretamente pela interface do GitHub até a pasta `ui-testing/Documentation`.
2. Todos os arquivos `.md` contêm links relativos para as imagens e vídeos localizados na pasta de evidências, permitindo uma leitura fluida e integrada diretamente pelo navegador.

---

## 🛠️ Ferramentas Utilizadas

*   **Postman**: Para orquestração, envio de requisições e validação da API.
*   **Markdown**: Para a construção de relatórios analíticos e rastreabilidade dos casos de teste.
*   **Ferramentas de Captura**: Para a documentação visual (screenshots e gravações) das evidências reportadas.