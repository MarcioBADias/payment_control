# Controle Financeiro Pessoal

Este é um aplicativo web simples para controle financeiro pessoal, desenvolvido com React, que permite ao usuário registrar entradas e saídas de valores, calcular um saldo e visualizar o histórico de transações. Ele agora conta com uma gestão de estado refatorada usando `useReducer` e persistência de dados através do Supabase.

## Funcionalidades Atuais

* **Registro de Transações:** Adicione novas entradas e saídas de valores com descrição, valor, data de vencimento e mês de competência.
* **Gestão de Estado Otimizada:** Toda a lógica de estado foi refatorada para utilizar `useReducer` e React Context para uma gestão mais centralizada e previsível.
* **Persistência de Dados (Supabase):**
    * **Autenticação:** Gerenciamento de login e registro de usuários.
    * **Armazenamento de Transações:** Todas as transações são salvas e recuperadas de um banco de dados Supabase (`payment control`).
    * **Dados do Usuário:** Utiliza tabelas `user` e `moviments` no Supabase para gerenciar informações do usuário e suas transações.
* **Visualização Detalhada de Movimentos:**
    * Exibição clara de `Descrição`, `Vencimento`, `Tipo` e `Valor`.
    * **Status Dinâmico:** Ícones visuais para indicar o status da despesa:
        * `PENDING` (Em dia): Ícone de atenção amarelo.
        * `OVERDUE` (Atrasado): Ícone de atenção vermelho (se a data atual for maior que a data de vencimento).
        * `PAID` (Pago): Ícone de check verde.
    * **Detalhes na Interação:** Um ícone de informação ao lado do valor exibe a data da última modificação na transação (`change_date`) ao passar o mouse.
    * **Atualização de Status:** Ao clicar nos ícones de status (PENDING ou OVERDUE), um pop-up permite marcar a transação como 'Paga'.
* **Resumo Financeiro:** Cálculo automático e exibição de entradas, saídas e saldo total.
* **Exclusão de Lançamentos:** Capacidade de remover transações do histórico.

## Tecnologias Utilizadas

* **React:** Biblioteca JavaScript para construção de interfaces de usuário.
* **React Hooks (`useState`, `useEffect`, `useReducer`, `useContext`, `useCallback`):** Para gestão de estado local e global, efeitos colaterais e otimização de performance.
* **Supabase:** Plataforma de backend de código aberto que fornece banco de dados (PostgreSQL), autenticação, APIs instantâneas e mais.
    * `@supabase/supabase-js`: SDK oficial do Supabase para JavaScript.
* **Styled Components:** Para estilização de componentes com CSS-in-JS.
* **React Icons:** Biblioteca de ícones populares para React.
* **Javascript (Filter, Map, Reduce):** Para manipulação de dados de forma eficiente.

## Como Utilizar

1.  **Clone o Repositório:**
    ```bash
    git clone [https://github.com/marciobadias/controle-financeiro.git](https://github.com/marciobadias/controle-financeiro.git)
    cd controle-financeiro
    ```

2.  **Instale as Dependências:**
    ```bash
    npm install
    # ou
    yarn install
    ```

3.  **Configure o Supabase:**
    * Crie um novo projeto no Supabase.
    * No seu projeto Supabase, crie as tabelas `user` e `moviments` com as seguintes colunas:
        * **`user`**: `login`, `password`, `group_id`, `email`, `url_profile_photo`
        * **`moviments`**: `name`, `expected_date`, `value`, `type`, `status`, `change_date`, `competence_month`, `user_name`, `user_photo`
    * Obtenha sua `Project URL` e `anon public key` na seção `Settings > API` do seu projeto Supabase.
    * Crie um arquivo `.env.local` na raiz do projeto (se ainda não existir) e adicione suas credenciais:
        ```env
        REACT_APP_SUPABASE_URL=SUA_URL_SUPABASE_AQUI
        REACT_APP_SUPABASE_ANON_KEY=SUA_CHAVE_ANON_SUPABASE_AQUI
        ```
        (Lembre-se de substituir `SUA_URL_SUPABASE_AQUI` e `SUA_CHAVE_ANON_SUPABASE_AQUI` pelos valores reais).

4.  **Inicie a Aplicação:**
    ```bash
    npm start
    # ou
    yarn start
    ```

    A aplicação será aberta em `http://localhost:3000` (ou outra porta disponível).

## Minha Experiência com o Projeto

Este projeto tem sido uma jornada incrível no aprendizado de React. Começou com os fundamentos de componentização e estilização com Styled Components, o que me permitiu organizar o código de forma limpa e modular. Aprofundei meus conhecimentos ao refatorar a gestão de estado com `useReducer` e React Context, percebendo como isso aprimora a previsibilidade e manutenção do estado da aplicação. A integração com o Supabase foi um marco, pois me permitiu explorar soluções de backend, autenticação e persistência de dados de forma eficiente e escalável, indo além do `localStorage`. Cada etapa solidificou minha compreensão sobre a construção de aplicações web modernas.

## Demonstração

Para ver o aplicativo em ação, você pode acessá-lo aqui:
