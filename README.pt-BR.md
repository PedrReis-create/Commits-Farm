# 🌱 Commit Farm

<p align="center">

  <strong>Gere commits Git com timestamps personalizados e experimente com gráficos de contribuições do GitHub.</strong>

</p>

<p align="center">

  <img src="https://img.shields.io/badge/Node.js-22.x-339933?style=for-the-badge&logo=node.js&logoColor=white" alt="Node.js">

  <img src="https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript">

  <img src="https://img.shields.io/badge/Git-Version%20Control-F05032?style=for-the-badge&logo=git&logoColor=white" alt="Git">

</p>

README in English → [🇺🇸 English](README.md)

---

## 📌 Sobre

**Commit Farm** é um projeto em Node.js para experimentar com **histórico do Git, timestamps personalizados de commits e gráficos de contribuições do GitHub**.

O script gera datas de commits dentro de um período configurável, cria commits Git utilizando esses timestamps e os envia para o repositório remoto configurado.

Ele foi desenvolvido como um exercício prático para entender como commits Git, timestamps, módulos do Node.js e dados de contribuições do GitHub funcionam em conjunto.

> **Nota:** Este projeto é destinado a fins educacionais e experimentais. Commits gerados não devem ser apresentados como evidência de trabalho que não foi realmente realizado.

---

## ✨ Funcionalidades

- Gerar uma quantidade configurável de commits.
- Gerar datas aleatórias de commits dentro de um período personalizado.
- Definir timestamps dos commits utilizando a opção `--date` do Git.
- Criar commits e realizar push automaticamente.
- Armazenar a data gerada no arquivo `data.json`.
- Experimentar diferentes distribuições no gráfico de contribuições.

---

## 🧠 Como funciona

O processo é:

```text
Definir o período das datas 
(Cuidado: Não coloque datas que ainda não chegaram (colocar datas futuras)).

        ↓

Gerar um número aleatório de dias

        ↓

Calcular a data do commit

        ↓

Salvar a data em data.json

        ↓

Criar o commit Git

        ↓

Enviar para o repositório remoto

        ↓

Repetir até que todos os commits sejam gerados
```

A lógica principal está localizada no arquivo `src/index.js`.

- `moment` realiza os cálculos de data.
- `random` gera valores aleatórios.
- `jsonfile` grava a data gerada em `data.json`.
- `simple-git` executa as operações do Git.

---

## 🚀 Começando

### 1. Clone o repositório

```bash
git clone https://github.com/PedrReis-create/commit-farm.git

cd commit-farm
```

### 2. Instale as dependências

Instale todas as dependências listadas no `package.json`:

```bash
npm install simple-git moment random jsonfile
```

O projeto utiliza:

- `moment`
- `simple-git`
- `random`
- `jsonfile`

### 3. Configure o Git

Antes de executar o script, certifique-se de que o Git está configurado:

```bash
git config user.name "Seu Nome"

git config user.email "seu-email@example.com"
```

Verifique sua configuração com:

```bash
git config --list
```

O repositório também precisa ter um remote configurado:

```bash
git remote -v
```

### 4. Configure o script

Abra:

```text
src/index.js
```

Você pode alterar a quantidade de commits e o período das datas antes de executar o script.

Consulte **[DATE-GUIDE.md](docs/DATE-GUIDE.md)** para obter instruções detalhadas sobre como alterar as datas. (Cuidado: Não coloque datas que ainda não chegaram (colocar datas futuras)).

### 5. Execute o script

```bash
node src/index.js
```

O script irá gerar os commits de acordo com a configuração definida no `src/index.js`.

---

## ⚙️ Configuração

### Quantidade de commits

Na parte inferior do `src/index.js`:

```javascript
makeCommits(300);
```

Altere `300` para a quantidade desejada:

```javascript
makeCommits(100);
```

Isso irá gerar 100 commits.

---

### Período das datas

O período das datas é controlado por:

```javascript
const startDate = moment("2025-01-01");

const endDate = moment("2025-12-31");
```

Por exemplo, para utilizar todo o ano de 2024:

```javascript
const startDate = moment("2024-01-01");

const endDate = moment("2024-12-31");
```

Para utilizar o período de 2024 até 2026:

```javascript
const startDate = moment("2024-01-01");

const endDate = moment("2026-12-31");
```

Para períodos personalizados:

```javascript
const startDate = moment("2025-06-01");

const endDate = moment("2025-09-30");
```

O formato das datas é:

```text
YYYY-MM-DD
```

Para mais exemplos, consulte **[DATE-GUIDE.md](docs/DATE-GUIDE.md)**.

---

## 📁 Estrutura do projeto

```text
commit-farm/
│
├── docs/
│   └── DATE-GUIDE.md
├── src/
│   └── index.js
├── .gitignore
├── LICENSE
├── package.json
├── package-lock.json
├── README.md
├── README.pt-BR.md
└── data.json
```

### Arquivos

| Arquivo | Descrição |
|------|-------------|
| `src/index.js` | Script principal que gera as datas e os commits |
| `docs/DATE-GUIDE.md` | Guia detalhado para alterar os períodos das datas |
| `data.json` | Armazena o timestamp gerado para o commit atual |
| `package.json` | Configuração do projeto e suas dependências |
| `package-lock.json` | Bloqueia as versões das dependências |
| `README.md` | Documentação do projeto em inglês |
| `README.pt-BR.md` | Documentação do projeto em português brasileiro |
| `LICENSE` | Licença do projeto |
| `.gitignore` | Arquivos e diretórios excluídos do Git |

> `node_modules/` é criado automaticamente pelo npm e não deve ser enviado para o repositório.

---

## 📦 Dependências

| Pacote | Finalidade |
|---------|---------|
| [`moment`](https://www.npmjs.com/package/moment) | Manipulação de datas e horários |
| [`simple-git`](https://www.npmjs.com/package/simple-git) | Interface para comandos Git |
| [`random`](https://www.npmjs.com/package/random) | Geração de números aleatórios |
| [`jsonfile`](https://www.npmjs.com/package/jsonfile) | Manipulação de arquivos JSON |

---

## 🛠️ Personalização

O projeto pode ser estendido de várias maneiras:

- **Quantidade de commits** — Alterar o número total de commits gerados.

- **Período das datas** — Definir a data mais antiga e a mais recente possíveis.

- **Distribuição dos commits** — Alterar a forma como as datas são selecionadas aleatoriamente.

- **Densidade dos commits** — Controlar a frequência dos commits ao longo do período selecionado.

- **Padrões** — Experimentar diferentes distribuições no gráfico de contribuições.

A implementação atual seleciona cada data de forma independente. Portanto, vários commits podem ser gerados no mesmo dia.

---

## ⚠️ Observações importantes

### Gráfico de contribuições do GitHub

Um timestamp de commit **não garante automaticamente** que o GitHub irá contabilizar o commit como uma contribuição.

O GitHub aplica suas próprias regras de contabilização de contribuições, incluindo requisitos relacionados ao repositório e ao commit.

### Datas futuras

Embora o Git possa armazenar timestamps no futuro, o GitHub não trata atividades futuras como contribuições históricas comuns antes que as respectivas datas ocorram.

### Identidade do Git

As informações de autor e committer utilizadas pelo Git precisam estar configuradas corretamente:

```bash
git config user.name

git config user.email
```

---

## 🔐 Privacidade

Se você estiver experimentando com gráficos de contribuições, considere utilizar um **repositório privado**.

Um repositório privado impede que usuários sem acesso visualizem seus commits e arquivos. O GitHub ainda pode exibir atividades de contribuições privadas de forma anonimizada no seu perfil, dependendo das configurações de contribuições.

---

## 📚 Documentação

Para obter instruções detalhadas sobre como alterar o período das datas:

**[📅 Ler o Guia de Datas](docs/DATE-GUIDE.md)**

---

## 🙏 Créditos

Um enorme agradecimento a **[fenrir2608](https://github.com/fenrir2608)** pelo projeto original **[goGreen](https://github.com/fenrir2608/goGreen)** e pela inspiração para esta implementação.

Este projeto foi desenvolvido de forma independente como um exercício de aprendizado e experimentação.

---

<p align="center">

  Feito com JavaScript & Git

</p>