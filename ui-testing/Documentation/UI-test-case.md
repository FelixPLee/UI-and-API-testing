# Plano de Testes UI - Sauce Demo

Este documento detalha o plano de testes para a interface web da plataforma **Sauce Demo**. O objetivo é validar fluxos críticos, comportamentos de diferentes perfis de usuários e o tratamento de mensagens de erro.

---

## 1. Autenticação

### TC-001: Login - standard_user
* **Nome:** Login com usuário padrão.
* **Objetivo:** Validar que um usuário comum consegue acessar o sistema com sucesso.
* **Pré-requisitos:** Estar na página de login (`https://www.saucedemo.com/`).
* **Ações:**
    1. Inserir `standard_user` no campo Username.
    2. Inserir `secret_sauce` no campo Password.
    3. Clicar no botão "Login".
* **Resultado:** O sistema deve redirecionar para a página de inventário (`/inventory.html`) exibindo a lista de produtos.
* **Evidência:** <video src="../Evidences/Videos/video-tc001-login-sucesso.mp4" controls></video>

### TC-002: Login - locked_out_user
* **Nome:** Login com usuário bloqueado.
* **Objetivo:** Validar que usuários com status bloqueado não conseguem acessar a plataforma.
* **Pré-requisitos:** Estar na página de login.
* **Ações:**
    1. Inserir `locked_out_user` no campo Username.
    2. Inserir `secret_sauce` no campo Password.
    3. Clicar em "Login".
* **Resultado:** O acesso deve ser negado e a mensagem "Epic sadface: Sorry, this user has been locked out." deve ser exibida.
* **Evidência:** <video src="../Evidences/Videos/video-tc002-locked-ou.mp4" controls></video>

### TC-003: Login - problem_user
* **Nome:** Login com usuário com problemas visuais/funcionais.
* **Objetivo:** Verificar se o usuário `problem_user` pode ser acessado normalmente. 
* **Pré-requisitos:** Estar na página de login.
* **Ações:**
    1. Inserir `problem_user` no campo Username.
    2. Inserir `secret_sauce` no campo Password.
    3. Clicar em "Login".
* **Resultado:** O sistema deve redirecionar para a página de inventário (`/inventory.html`) exibindo a lista de produtos.
* **Evidência:** <video src="../Evidences/Videos/video-tc003-problem-user.mp4" controls></video>

### TC-004: Login - performance_glitch_user
* **Nome:** Login com usuário com atraso de performance.
* **Objetivo:** Validar o carregamento da página sob condições de latência (intencional).
* **Pré-requisitos:** Estar na página de login.
* **Ações:**
    1. Inserir `performance_glitch_user` no campo Username.
    2. Inserir `secret_sauce` no campo Password.
    3. Clicar em "Login".
* **Resultado:** O login deve ocorrer com sucesso, porém com um atraso perceptível (ex: 5 segundos) no carregamento da página de produtos.
* **Evidência:** <video src="../Evidences/Videos/video-tc004-performance-delay.mp4" controls></video>

### TC-005: Login - error_user
* **Nome:** Login com usuário de erro.
* **Objetivo:** Verificar se o usuário `error-user` pode ser acessado normalmente.
* **Pré-requisitos:** Estar na página de login.
* **Ações:**
    1. Inserir `error_user` no campo Username.
    2. Inserir `secret_sauce` no campo Password.
    3. Clicar em "Login".
* **Resultado:** O sistema deve redirecionar para a página de inventário (`/inventory.html`) exibindo a lista de produtos.
* **Evidência:** <video src="../Evidences/Videos/video-tc005-error-user.mp4" controls></video>

### TC-006: Login - visual_user
* **Nome:** Login com usuário visualmente inconsistente.
* **Objetivo:** Verificar se o usuário `visual_user` pode ser acessado normalmente.
* **Pré-requisitos:** Estar na página de login.
* **Ações:**
    1. Inserir `visual_user` no campo Username.
    2. Inserir `secret_sauce` no campo Password.
    3. Clicar em "Login".
* **Resultado:** O sistema deve redirecionar para a página de inventário (`/inventory.html`) exibindo a lista de produtos.
* **Evidência:** <video src="../Evidences/Videos/video-tc006-visual.mp4" controls></video>

---

## 2. Mensagens de Erro de autenticação

### TC-007: Erro - Acesso Direto Restrito
* **Nome:** Tentativa de acesso a página interna sem autenticação.
* **Objetivo:** Validar a segurança e mensagem de erro ao tentar burlar o login via URL.
* **Pré-requisitos:** Não ter realizado o login ainda ou ter realizado o logout.
* **Ações:**
    1. Tentar acessar diretamente `https://www.saucedemo.com/inventory.html`.
* **Resultado:** Redirecionamento para o login com a mensagem: "You can only access '${location.state.from.pathname}' when you are logged in."
* **Evidência:** ![Acesso Direto Restito](../Evidences/Images/screenshot-tc007-acesso-indireto.png)

### TC-008: Erro - Usuário Ausente
* **Nome:** Validação de campo "Username" obrigatório.
* **Objetivo:** Verificar se o sistema impede login sem preenchimento do usuário.
* **Pré-requisitos:** Estar na página de login.
* **Ações:**
    1. Deixar o campo Username vazio.
    2. Preencher Password com `secret_sauce`.
    3. Clicar em "Login".
* **Resultado:** Exibição da mensagem: "Epic sadface: Username is required".
* **Evidência:** ![Usuário Ausente](../Evidences/Images/screenshot-tc008-user-required.png)

### TC-009: Erro - Senha Ausente
* **Nome:** Validação de campo "Password" obrigatório.
* **Objetivo:** Verificar se o sistema impede login sem preenchimento da senha.
* **Pré-requisitos:** Estar na página de login.
* **Ações:**
    1. Preencher Username com `standard_user`.
    2. Deixar Password vazio.
    3. Clicar em "Login".
* **Resultado:** Exibição da mensagem: "Epic sadface: Password is required".
* **Evidência:** ![Senha Ausente](../Evidences/Images/screenshot-tc009-pass-required.png)

### TC-010: Erro - Credenciais Inválidas
* **Nome:** Tentativa de login com dados incorretos.
* **Objetivo:** Validar a mensagem genérica de erro de credenciais.
* **Pré-requisitos:** Estar na página de login.
* **Ações:**
    1. Inserir usuário inexistente ou senha incorreta.
    2. Clicar em "Login".
* **Resultado:** Exibição da mensagem: "Epic sadface: Username and password do not match any user in this service".
* **Evidência:** ![Credenciais Inválidas](../Evidences/Images/screenshot-tc010-invalid-creds.png)

### TC-011: Erro - Primeiro Nome Obrigatório
* **Nome:** Tentativa de login com dados incorretos.
* **Objetivo:** Validar a mensagem genérica de erro de credenciais.
* **Pré-requisitos:** Estar na página de login.
* **Ações:**
    1. Inserir usuário inexistente ou senha incorreta.
    2. Clicar em "Login".
* **Resultado:** Exibição da mensagem: "Epic sadface: Username and password do not match any user in this service".
* **Evidência:** ![Nome Obrigatório](../Evidences/Images/screenshot-tc011-first-name-required.png)

### TC-012: Erro - Sobrenome Obrigatório
* **Nome:** Tentativa de login com dados incorretos.
* **Objetivo:** Validar a mensagem genérica de erro de credenciais.
* **Pré-requisitos:** Estar na página de login.
* **Ações:**
    1. Inserir usuário inexistente ou senha incorreta.
    2. Clicar em "Login".
* **Resultado:** Exibição da mensagem: "Epic sadface: Username and password do not match any user in this service".
* **Evidência:** ![Sobrenome Obrigatório](../Evidences/Images/screenshot-tc012-last-name-required.png)

### TC-013: Erro - Código Postal Obrigatório
* **Nome:** Tentativa de login com dados incorretos.
* **Objetivo:** Validar a mensagem genérica de erro de credenciais.
* **Pré-requisitos:** Estar na página de login.
* **Ações:**
    1. Inserir usuário inexistente ou senha incorreta.
    2. Clicar em "Login".
* **Resultado:** Exibição da mensagem: "Epic sadface: Username and password do not match any user in this service".
* **Evidência:** ![Código Postal Obrigatório](../Evidences/Images/screenshot-tc013-zip-code-required.png)

---

## 3. Fluxo de Compra Básico

### TC-014: Fluxo de Compra Completo
* **Nome:** Realizar compra com sucesso.
* **Objetivo:** Validar o ciclo de vida completo de uma venda no e-commerce.
* **Pré-requisitos:** Usuário logado (`standard_user`).
* **Ações:**
    1. **Adicionar ao carrinho:** Clicar em "Add to cart" no produto "Sauce Labs Backpack".
    2. **Carrinho:** Clicar no ícone do carrinho no topo superior direito.
    3. **Checkout:** Na página do carrinho, clicar em "Checkout".
    4. **Informações:** Preencher First Name, Last Name e Zip Code. Clicar em "Continue".
    5. **Confirmação:** Na página "Checkout: Overview", clicar em "Finish".
* **Resultado:** Exibição da **Tela Final** com a mensagem "Thank you for your order!".
* **Evidência:** <video src="../Evidences/Videos/video-tc014-compra-completa.mp4" controls></video>

### TC-015: Fluxo de Compra Completo
* **Nome:** Realizar compra com sucesso.
* **Objetivo:** Validar o ciclo de vida completo de uma venda no e-commerce.
* **Pré-requisitos:** Usuário logado (`standard_user`).
* **Ações:**
    1. **Adicionar ao carrinho:** Clicar em "Add to cart" no produto "Sauce Labs Backpack".
    2. **Carrinho:** Clicar no ícone do carrinho no topo superior direito.
    3. **Checkout:** Na página do carrinho, clicar em "Checkout".
    4. **Informações:** Preencher First Name, Last Name e Zip Code. Clicar em "Continue".
    5. **Confirmação:** Na página "Checkout: Overview", clicar em "Finish".
* **Resultado:** A interface permite que o fluxo de compra seja realizado mesmo com o carrinho vazio".
* **Evidência:** <video src="../Evidences/Videos/video-tc015-carrinho-vazio-completa.mp4" controls></video>

---

## 4. Funções Adicionais

### TC-016: Remoção de Produto
* **Nome:** Remover item do carrinho.
* **Objetivo:** Validar que o usuário pode desistir de um item.
* **Pré-requisitos:** Produto adicionado ao carrinho.
* **Ações:**
    1. Acessar o carrinho.
    2. Clicar no botão "Remove" ao lado do produto.

    ou

    1. Clicar novamente em "Remove" na página de inventário para o mesmo produto.
* **Resultado:** O item deve ser removido da lista e o contador do ícone do carrinho deve ser atualizado.
* **Evidência:** <video src="../Evidences/Videos/video-tc016-remocao.mp4" controls></video>

### TC-017: Filtro de Produtos
* **Nome:** Filtragem de preços.
* **Objetivo:** Validar a ordenação dos produtos por preço.
* **Pré-requisitos:** Estar na página de inventário.
* **Ações:**
    1. Clicar no menu suspenso de filtro (top right).
    2. Selecionar uma das opções de filtro.
    3. Repetir com todas as opções de filtro
* **Resultado:** Os produtos devem ser reordenados exibindo os menores valores primeiro.
* **Evidência:** <video src="../Evidences/Videos/video-tc017-filtro..mp4" controls></video>

### TC-018: Visão Detalhada do Produto
* **Nome:** Ampliar visão/detalhes do produto.
* **Objetivo:** Validar a navegação para a página de detalhes de um item.
* **Pré-requisitos:** Estar na página de inventário.
* **Ações:**
    1. Clicar no nome ou na imagem do produto "Sauce Labs Bolt T-Shirt".
* **Resultado:** Abertura da página específica do produto com descrição detalhada, imagem ampliada e preço.
* **Evidência:** ![detalhes](../Evidences/Images/screenshot-tc018-detalhes.png)

### TC-019: Navegação e Logout
* **Nome:** Logout do sistema.
* **Objetivo:** Validar o encerramento da sessão.
* **Pré-requisitos:** Usuário logado.
* **Ações:**
    1. Clicar no menu lateral (hambúrguer).
    2. Clicar em "Logout".
* **Resultado:** O usuário deve ser redirecionado para a página de login e não deve conseguir voltar às páginas internas pelo botão "voltar" do navegador.
* **Evidência:** <video src="../Evidences/Videos/video-tc019-logout.mp4" controls></video>

### TC-020: Responsividade Mobile-Friendly
* **Nome:** Logout do sistema.
* **Objetivo:** Validar o encerramento da sessão.
* **Pré-requisitos:** Usuário logado.
* **Ações:**
    1. Acessar a interface de usuário através de um dispositivo mobile.
    2. Reproduzir o fluxo de compra semelhante ao TC-014.
* **Resultado:** O usuário deve ser capaz de realizar as funções básicas de compra em dispositivos mobile.
* **Evidência:**  <video src="../Evidences/Videos/video-tc020-mobile.mp4" controls></video>
