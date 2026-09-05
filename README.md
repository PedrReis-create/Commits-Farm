# 🌱 Commit Farm

<p align="center">
  <strong>Generate Git commits with custom timestamps and experiment with GitHub contribution graphs.</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Node.js-22.x-339933?style=for-the-badge&logo=node.js&logoColor=white" alt="Node.js">
  <img src="https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript">
  <img src="https://img.shields.io/badge/Git-Version%20Control-F05032?style=for-the-badge&logo=git&logoColor=white" alt="Git">
</p>

---

## 📌 About

**Commit Farm** is a Node.js project for experimenting with **Git history, custom commit timestamps, and GitHub contribution graphs**.

The script generates commit dates within a configurable period, creates Git commits using those timestamps, and pushes them to the configured remote repository.

It is designed as a practical exercise for understanding how Git commits, timestamps, Node.js modules, and GitHub contribution data work together.

> **Note:** This project is intended for educational and experimental purposes. Generated commits should not be presented as evidence of work that was not actually performed.

---

## ✨ Features

- Generate a configurable number of commits.
- Generate random commit dates within a custom date range.
- Set commit timestamps using Git's `--date` option.
- Automatically commit and push changes.
- Store the generated date in `data.json`.
- Experiment with different contribution graph distributions.

---

## 🧠 How It Works

The process is:

```text
Define the date range
        ↓
Generate a random number of days
        ↓
Calculate the commit date
        ↓
Save the date to data.json
        ↓
Create the Git commit
        ↓
Push to the remote repository
        ↓
Repeat until all commits are generated
```

The main logic is contained in `index.js`.

- `moment` handles date calculations.
- `random` generates random values.
- `jsonfile` writes the generated date to `data.json`.
- `simple-git` executes Git operations.

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/PedrReis-create/commit-farm.git
cd commit-farm
```

### 2. Install dependencies

Install all dependencies listed in `package.json`:

```bash
npm install
```

The project uses:

- `moment`
- `simple-git`
- `random`
- `jsonfile`

You do **not** need to install them individually if you already ran `npm install`.

### 3. Configure Git

Before running the script, make sure Git is configured:

```bash
git config user.name "Your Name"
git config user.email "your-email@example.com"
```

Check your configuration with:

```bash
git config --list
```

The repository must also have a remote configured:

```bash
git remote -v
```

### 4. Configure the script

Open:

```text
index.js
```

You can change the number of commits and the date range before running the script.

See **[DATE-GUIDE.md](DATE-GUIDE.md)** for detailed instructions on changing dates.

### 5. Run the script

```bash
node index.js
```

The script will generate commits according to the configuration in `index.js`.

---

## ⚙️ Configuration

### Number of commits

At the bottom of `index.js`:

```javascript
makeCommits(300);
```

Change `300` to the desired number:

```javascript
makeCommits(100);
```

This generates 100 commits.

---

### Date range

The date range is controlled by:

```javascript
const startDate = moment("2025-01-01");
const endDate = moment("2025-12-31");
```

For example, to use all of 2024:

```javascript
const startDate = moment("2024-01-01");
const endDate = moment("2024-12-31");
```

To use 2024 through 2026:

```javascript
const startDate = moment("2024-01-01");
const endDate = moment("2026-12-31");
```

For custom ranges:

```javascript
const startDate = moment("2025-06-01");
const endDate = moment("2025-09-30");
```

The date format is:

```text
YYYY-MM-DD
```

For more examples, see **[DATE-GUIDE.md](DATE-GUIDE.md)**.

---

## 📁 Project Structure

```text
commit-farm/
│
├── .gitignore
├── DATE-GUIDE.md
├── index.js
├── LICENSE
├── package.json
├── package-lock.json
├── README.md
└── data.json
```

### Files

| File | Description |
|------|-------------|
| `index.js` | Main script that generates dates and commits |
| `data.json` | Stores the timestamp generated for the current commit |
| `DATE-GUIDE.md` | Detailed guide for changing date ranges |
| `package.json` | Project configuration and dependencies |
| `package-lock.json` | Locks dependency versions |
| `README.md` | Project documentation |
| `LICENSE` | Project license |
| `.gitignore` | Files and directories excluded from Git |

> `node_modules/` is created automatically by npm and should not be committed to the repository.

---

## 📦 Dependencies

| Package | Purpose |
|---------|---------|
| [`moment`](https://www.npmjs.com/package/moment) | Date and time manipulation |
| [`simple-git`](https://www.npmjs.com/package/simple-git) | Git command interface |
| [`random`](https://www.npmjs.com/package/random) | Random number generation |
| [`jsonfile`](https://www.npmjs.com/package/jsonfile) | JSON file management |

---

## 🛠️ Customization

The project can be extended in several ways:

- **Commit quantity** — Change the total number of generated commits.
- **Date range** — Define the earliest and latest possible dates.
- **Commit distribution** — Change how dates are randomly selected.
- **Commit density** — Control how frequently commits occur across the selected period.
- **Patterns** — Experiment with different distributions on the contribution graph.

The current implementation selects each date independently, so multiple commits can be generated for the same day.

---

## ⚠️ Important Notes

### GitHub contribution graph

A commit timestamp does **not automatically guarantee** that GitHub will count the commit as a contribution.

GitHub applies its own contribution rules, including repository and commit requirements.

### Future dates

Although Git can store timestamps in the future, GitHub does not treat future activity as ordinary historical contributions before the corresponding dates occur.

### Git identity

The author and committer information used by Git must be configured correctly:

```bash
git config user.name
git config user.email
```

---

## 🔐 Privacy

If you are experimenting with contribution graphs, consider using a **private repository**.

A private repository prevents users without access from viewing its commits and files. GitHub may still display anonymized private contribution activity on your profile depending on your contribution settings.

---

## 📚 Documentation

For detailed instructions on changing the date range:

**[📅 Read the Date Guide](DATE-GUIDE.md)**

---

## 🙏 Credits

Huge thanks to **[fenrir2608](https://github.com/fenrir2608)** for the original **[goGreen](https://github.com/fenrir2608/goGreen)** project and the inspiration behind this implementation.

This project was developed independently as a learning and experimentation exercise.

---

<p align="center">
  Made with JavaScript & Git
</p>
