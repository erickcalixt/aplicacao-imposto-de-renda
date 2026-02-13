# Documentação de Sistema: Lion App

Esta documentação descreve a estrutura e o propósito do arquivo `Lion App.xlsx`, um sistema de organização e controle financeiro projetado para facilitar o preparo e a declaração do **Imposto de Renda da Pessoa Física (IRPF)**.

O arquivo atua como um banco de dados relacional simples, dividido em quatro abas (planilhas) principais:

---

## 1. Aba: `TITULAR`
**Objetivo:** Armazenar os dados cadastrais sensíveis e as informações pessoais do declarante (Pessoa Física). Estas informações espelham as exigências da folha de rosto do programa da Receita Federal.

| Campo | Descrição | Exemplo de Preenchimento |
| :--- | :--- | :--- |
| **NOME** | Nome completo do declarante. | ELIZABETH GRANT DEL REY |
| **CPF** | Cadastro de Pessoa Física (apenas números). | 70454189901 |
| **NASCIMENTO** | Data de nascimento no formato `YYYY-MM-DD`. | 2001-09-28 |
| **TÍTULO DE ELEITOR** | Número do título de eleitor do titular. | 31713388 |
| **CÔNJUGE** | Nome completo do cônjuge, se houver. | LACOSTE CÉSAR COURO |
| **RUA** | Endereço residencial completo. | Avenida Abel Cabral, Nova Parnamirim, Nº 608 |
| **RUA ABREVIADA** | Versão curta do endereço para relatórios. | Av. Abel Cabral, NP, Nº 608 |
| **CEP** | Código de Endereçamento Postal. | 30158932 |
| **TELEFONE / CELULAR** | Números de contato (apenas números). | 9432234310 / 94958212230 |
| **E-MAIL** | Endereço de correio eletrônico. | ELIZABETHGRANTDELREY@GMAIL.COM |
| **HOUVE ALTERAÇÕES...** | Flag indicando mudança de dados (`Sim`/`Não`). | Sim |
| **DEPENDENTE CÔNJUGE** | Flag indicando se o cônjuge é dependente (`Sim`/`Não`). | Não |
| **RESIDENTE DO EXTERIOR** | Flag sobre residência fiscal (`Sim`/`Não`). | Sim |

---

## 2. Aba: `INFORMES`
**Objetivo:** Consolidar os saldos e rendimentos bancários vinculados ao titular, servindo como um índice de referência para os arquivos de comprovação em PDF.

* **TOTAL:** Guarda o somatório de todos os valores atuais dos bancos listados (ex: `20646000`).
* **Estrutura dos Bancos:** A aba é dividida em blocos sequenciais (1º Banco, 2º Banco, etc.) com a seguinte estrutura:

| Campo | Descrição |
| :--- | :--- |
| **BANCO** | Código COMPE e nome da instituição financeira. Ex: `260 - Nubank`. |
| **VALOR ATUAL** | Saldo financeiro ou valor de rendimento na instituição. |
| **ANEXO 🖇️** | Nome do arquivo PDF do informe de rendimentos (ex: `NUBANK.PDF`). |

---

## 3. Aba: `NOTAS`
**Objetivo:** Registrar o extrato de holerites e notas bancárias, funcionando como um livro-caixa detalhado das entradas financeiras (receitas) do titular.

| Campo | Descrição | Regras de Preenchimento |
| :--- | :--- | :--- |
| **DATA** | Data do recebimento do valor. | Formato `YYYY-MM-DD` (ex: 2026-02-13). |
| **CATEGORA*** | Classificação da origem da receita. | Valores mapeados: `FREELANCER`, `HOLERITE`, `CNPJ`. |
| **VALOR** | Valor financeiro da entrada. | Formato numérico bruto (ex: `3000`). |

*\*Nota: Recomenda-se corrigir o cabeçalho no arquivo original de "CATEGORA" para "CATEGORIA".*

---

## 4. Aba: `TABELAS`
**Objetivo:** Atuar como um "Dicionário de Dados" (Tabela de Domínio).

* **Conteúdo:** Contém a lista oficial de códigos e nomes dos bancos brasileiros (Código COMPE). Ex: `1 - Banco do Brasil`, `33 - Banco Santander`, `260 - Nubank`.
* **Aplicação:** Esta aba deve ser utilizada para alimentar validações de dados (menus suspensos) na aba `INFORMES`, garantindo padronização na entrada de dados e evitando erros de digitação.
