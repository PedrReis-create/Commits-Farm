# Commit Farm

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

**Commit Farm** is a Node.js project designed to experiment with **Git history, custom commit timestamps, and GitHub contribution graphs**.

The script generates dates within a defined period and creates Git commits using those timestamps. It can be customized to experiment with different commit distributions and contribution graph patterns.

> **Note:** This project is intended for educational and experimental purposes.

---

## ⚙️ How It Works

The project follows a simple process:

```text
Random values
     ↓
Generate a date
     ↓
Save date to data.json
     ↓
Create Git commit
     ↓
Push to remote repository
     ↓
Repeat
```

The main script uses `moment` to calculate dates and `simple-git` to execute Git commands.

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/PedrReis-create/commit-farm.git
cd commit-farm
```

### 2. Install dependencies

```bash
npm install
```

Or install the required packages manually:

```bash
npm install moment simple-git random jsonfile
```

### 3. Configure Git

Make sure your Git repository is correctly configured and that you have permission to push to the remote repository.

### 4. Run the project

```bash
node index.js
```

The script will generate commits according to the parameters defined in `index.js`.

---

## 📁 Project Structure

```text
commit-farm/
│
├── 📄 index.js
├── 📄 package.json
├── 📄 package-lock.json
└── 📁 node_modules/
```

### Files

| File | Description |
|------|-------------|
| `index.js` | Main script responsible for generating commits |
| `data.json` | Stores generated timestamp data |
| `package.json` | Project configuration and dependencies |
| `package-lock.json` | Locks installed dependency versions |

---

## 🛠️ Customization

The script can be modified to change how commits are generated.

### Commit quantity

Control how many commits the script generates.

### Date range

Change the period from which commit dates are generated.

### Commit density

Generate different numbers of commits across different days.

### Contribution patterns

Experiment with different distributions to create patterns on the GitHub contribution graph.

### Date distribution

Modify the randomization logic to control how dates are selected.

---

## 📦 Dependencies

| Package | Purpose |
|---------|---------|
| [`moment`](https://www.npmjs.com/package/moment) | Date and time manipulation |
| [`simple-git`](https://www.npmjs.com/package/simple-git) | Git command interface |
| [`random`](https://www.npmjs.com/package/random) | Random number generation |
| [`jsonfile`](https://www.npmjs.com/package/jsonfile) | JSON file management |

---

## 💻 Technologies

- **Node.js**
- **JavaScript**
- **Git**
- **npm**

---

## ⚠️ Disclaimer

Commit Farm is intended for **learning and experimentation** with Git, Node.js, commit timestamps, and GitHub contribution graphs.

Generated commits should **not** be represented as evidence of work that was not actually performed.

---

## 🙏 Credits

Huge thanks to **[fenrir2608](https://github.com/fenrir2608)** for the original **[goGreen](https://github.com/fenrir2608/goGreen)** project and for the inspiration behind this implementation.

This project was created independently as a learning and experimentation exercise.

---

<p align="center">
  Made with JavaScript & Git
</p>
