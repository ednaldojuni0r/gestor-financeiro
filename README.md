# 💎 Gestor Financeiro Pro — Ed

Aplicativo pessoal de gestão financeira integrado ao Google Sheets, hospedado no GitHub Pages. Permite visualizar receitas, despesas, gráficos e lançamentos diretamente no navegador, sem instalar nada.

🔗 **Acesse:** [ednaldojuni0r.github.io/gestor-financeiro](https://ednaldojuni0r.github.io/gestor-financeiro/)

---

## 📋 Visão Geral

O sistema é composto por três partes:

| Parte | O que é | Para que serve |
|---|---|---|
| **Google Sheets** | Planilha na nuvem | Armazena todos os dados financeiros |
| **Google Apps Script** | Código no Sheets | Recebe e processa os lançamentos do app |
| **GitHub Pages** | Site estático | Interface visual do aplicativo |

---

## 🗂️ Estrutura da Planilha (Google Sheets)

A planilha possui duas abas obrigatórias:

### Aba `Dados`
Onde ficam todos os lançamentos financeiros. Colunas:

| Coluna | Descrição | Exemplo |
|---|---|---|
| Tipo | Receita ou Despesa | `Despesa` |
| Data | Data do lançamento | `15/04/2026` |
| Descrição | O que foi gasto/recebido | `Netflix` |
| Valor | Valor em reais | `55.90` |
| Cartão / Banco | Banco ou cartão usado | `Nubank` |
| Categoria | Categoria principal | `Assinaturas` |
| Subcategoria | Detalhe da categoria | `Streaming` |
| Tags | Classificação extra | `Pessoal` |
| Recorrência | Tipo de lançamento | `Única` / `Fixa` / `Parcelada` |
| Parcelas | Ex: 2/12 | `1/1` |
| ID Agrupamento | Identificador interno | `GRP-1234567890` |
| Mês de Referência | Mês ao qual o gasto pertence | `abril/26` |
| Crédito? | Se foi no crédito | `Sim` / `Não` |

> ⚠️ **Importante:** O campo **Mês de Referência** deve estar no formato `mês/ano` com duas casas para o ano. Exemplos corretos: `janeiro/26`, `abril/26`, `dezembro/25`.

### Aba `Configuracoes`
Onde ficam os bancos e categorias disponíveis no app. Colunas:

| Coluna A | Coluna B | Coluna C | Coluna D |
|---|---|---|---|
| Banco/Cartão | Tipo | Categoria | Subcategoria |
| Nubank | Despesa | Alimentação | Supermercado |
| Itaú | Receita | Trabalho | Salário |

> O app lê esta aba automaticamente ao sincronizar, populando os dropdowns de categoria, subcategoria e banco.

---

## ⚙️ Configuração Inicial

### 1. Google Sheets — Publicar na Web

Para o app conseguir ler os dados, a planilha precisa estar publicada:

1. Abra a planilha no Google Sheets
2. Clique em **Arquivo → Compartilhar → Publicar na Web**
3. Selecione a aba **Dados** e o formato **CSV**
4. Clique em **Publicar** e confirme

### 2. Google Apps Script — Implantar

O Apps Script processa os lançamentos enviados pelo app:

1. Na planilha, clique em **Extensões → Apps Script**
2. Cole o código do arquivo `Apps Script.gs`
3. Clique em **Implantar → Nova implantação**
4. Tipo: **App da Web**
5. Executar como: **Eu**
6. Quem tem acesso: **Qualquer pessoa**
7. Clique em **Implantar** e copie a URL gerada
8. Cole a URL no arquivo `index.html` na variável `ASU`

### 3. GitHub Pages — Publicar o App

1. Faça upload do arquivo `index.html` no repositório
2. Vá em **Settings → Pages**
3. Source: **Deploy from a branch → main**
4. Aguarde 1-2 minutos e acesse o link gerado

---

## 📱 Como Usar o Aplicativo

### Ao entrar no site
O app carrega automaticamente todos os lançamentos da planilha. Aguarde o banner verde confirmar a sincronização.

### 📊 Dashboard
Visão geral do período selecionado:
- Cards com **Total Receitas**, **Total Despesas** e **Saldo**
- Insights: maior gasto, categoria mais cara, média diária, taxa de poupança
- Gráfico de **rosca** por categoria
- Lista das **Top Categorias** com barra de progresso

### 📈 Evolução
Análise histórica:
- Gráfico de **barras** Receitas vs Despesas por mês (ou trimestre)
- Gráfico de **linha** com saldo acumulado
- Gráfico **horizontal** de despesas por categoria

### 📋 Lançamentos
Tabela com todos os lançamentos:
- Filtros: **Todos / Receitas / Despesas**
- **Busca por texto** (descrição ou categoria)
- **Filtro por categoria**
- Ordenação por **Mês Ref.**, **Data** ou **Valor** (clique no cabeçalho)
- **Duplo clique** em qualquer linha para **editar ou excluir**

### ➕ Novo Lançamento
Formulário para cadastrar receitas e despesas:
- Selecione o **Tipo** (Receita ou Despesa)
- Preencha **Data**, **Mês de Referência** e **Ano**
- Informe **Descrição**, **Valor**, **Banco**, **Categoria**, **Subcategoria** e **Tag**
- Para despesas: escolha o **Tipo de Recorrência**
  - **Único**: lançamento avulso
  - **Fixo**: replica automaticamente por 12 meses
  - **Parcelado**: divide o valor e cria uma linha por parcela
- Clique em **💾 Salvar no Google Sheets**

### 🔄 Sincronizar
- O botão **Sincronizar** na barra superior força uma atualização manual
- A sincronização também ocorre automaticamente ao entrar no site, após salvar, editar ou excluir lançamentos

### 📅 Filtro de Período
- Use as **pills de mês** para filtrar por um mês específico
- Use o **range de datas** para filtrar um intervalo personalizado
- Clique em **Todos** para ver todos os meses

---

## ✏️ Editando e Excluindo Lançamentos

1. Vá na aba **📋 Lançamentos**
2. Dê **dois cliques rápidos** na linha desejada
3. Um modal abrirá com os dados preenchidos
4. Edite os campos e clique em **💾 Salvar** — ou clique em **🗑️ Excluir** para remover

> ⚠️ A exclusão é **permanente** e remove a linha diretamente da planilha. Não é possível desfazer.

---

## 🔧 Estrutura do Projeto

```
gestor-financeiro/
├── index.html          # Aplicativo completo (HTML + CSS + JS)
├── README.md           # Esta documentação
└── Apps Script.gs      # Código do Google Apps Script (referência)
```

---

## 🛠️ Tecnologias Utilizadas

| Tecnologia | Uso |
|---|---|
| HTML/CSS/JavaScript | Interface do aplicativo |
| Chart.js | Gráficos interativos |
| Google Sheets | Banco de dados |
| Google Apps Script | API de leitura e escrita |
| GitHub Pages | Hospedagem gratuita |

---

## 🚨 Solução de Problemas

| Problema | Solução |
|---|---|
| Site em branco | Verificar se o `index.html` foi salvo corretamente no GitHub |
| Dados não carregam | Verificar se a planilha está publicada na web |
| Erro ao salvar | Verificar se o Apps Script está implantado e a URL está correta no `index.html` |
| Mês aparece errado | Garantir que o campo Mês de Referência está no formato `mês/ano` (ex: `abril/26`) |
| Valor salvo errado | Digitar apenas números e vírgula no campo valor (ex: `1500,00`) |

---

## 👤 Autor

**Ednaldo Domingos (Ed)**  
Contador · Desenvolvido com apoio do Claude (Anthropic)

---

*Última atualização: Abril/2026*
