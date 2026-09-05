# 📅 Changing Commit Dates

This guide explains how to change the date range used by **Commit Farm**.

The date is controlled directly in `index.js`, where `moment()` is used to calculate the timestamp assigned to each commit.

---

## 🔧 Basic Configuration

The relevant section is:

```javascript
const startDate = moment("2024-01-01");
const endDate = moment("2026-12-31");

const totalDays = endDate.diff(startDate, "days");
const randomDays = random.int(0, totalDays);

const date = startDate
  .clone()
  .add(randomDays, "d")
  .format();
```

There are two values you need to change:

```javascript
const startDate = moment("2024-01-01");
const endDate = moment("2026-12-31");
```

- `startDate` defines the **first possible date**.
- `endDate` defines the **last possible date**.

The expected format is:

```text
YYYY-MM-DD
```

For example:

```text
2025-01-01
```

means **January 1, 2025**.

---

# 🗓️ Examples

## Only 2025

To generate dates exclusively within 2025:

```javascript
const startDate = moment("2025-01-01");
const endDate = moment("2025-12-31");
```

The possible range becomes:

```text
01/01/2025 → 31/12/2025
```

---

## Only 2024

```javascript
const startDate = moment("2024-01-01");
const endDate = moment("2024-12-31");
```

Range:

```text
01/01/2024 → 31/12/2024
```

---

## Only 2026

```javascript
const startDate = moment("2026-01-01");
const endDate = moment("2026-12-31");
```

Range:

```text
01/01/2026 → 31/12/2026
```

---

## 2024 + 2025 + 2026

To allow dates across all three years:

```javascript
const startDate = moment("2024-01-01");
const endDate = moment("2026-12-31");
```

This creates a continuous range:

```text
2024-01-01
     ↓
2024
     ↓
2025
     ↓
2026
     ↓
2026-12-31
```

The script then randomly selects a day within that entire period.

---

# 🎯 Custom Date Ranges

You are not limited to complete years.

For example, to generate dates from June 1, 2025 through September 30, 2025:

```javascript
const startDate = moment("2025-06-01");
const endDate = moment("2025-09-30");
```

Or from October 15, 2024 through February 20, 2025:

```javascript
const startDate = moment("2024-10-15");
const endDate = moment("2025-02-20");
```

Any valid `YYYY-MM-DD` range can be used.

---

# 🔢 Changing the Number of Commits

The number of generated commits is controlled by:

```javascript
makeCommits(300);
```

Change `300` to the desired amount.

For example:

```javascript
makeCommits(100);
```

or:

```javascript
makeCommits(500);
```

The number of commits and the date range are independent settings.

For example:

```javascript
makeCommits(300);
```

with:

```javascript
const startDate = moment("2025-01-01");
const endDate = moment("2025-12-31");
```

means the script will generate **300 commits with randomly selected dates within 2025**.

> Multiple commits can receive the same date because each date is selected independently.

---

# ⚙️ Complete Example

Here is the complete date-generation section:

```javascript
const makeCommits = (n) => {
  if (n === 0) return simpleGit().push();

  const startDate = moment("2025-01-01");
  const endDate = moment("2025-12-31");

  const totalDays = endDate.diff(startDate, "days");
  const randomDays = random.int(0, totalDays);

  const date = startDate
    .clone()
    .add(randomDays, "d")
    .format();

  const data = {
    date: date,
  };

  console.log(date);

  jsonfile.writeFile(path, data, () => {
    simpleGit()
      .add([path])
      .commit(
        date,
        { "--date": date },
        makeCommits.bind(this, --n)
      );
  });
};

makeCommits(300);
```

---

# 🧠 How the Date Calculation Works

The script first defines the boundaries:

```javascript
const startDate = moment("2025-01-01");
const endDate = moment("2025-12-31");
```

Then it calculates how many days exist between them:

```javascript
const totalDays = endDate.diff(startDate, "days");
```

A random number of days is selected:

```javascript
const randomDays = random.int(0, totalDays);
```

Finally, that number is added to the starting date:

```javascript
const date = startDate
  .clone()
  .add(randomDays, "d")
  .format();
```

Conceptually:

```text
Start Date
    │
    ├── Random number of days
    │
    ▼
Generated Date
    │
    ▼
Git Commit
```

---

# ⚠️ Important Notes

### Future dates

Git allows commit objects to contain timestamps in the future, but GitHub's contribution graph does not necessarily treat future-dated commits as normal contributions until the relevant date.

### Repository configuration

The generated commits must belong to the Git repository you intend to use, and your Git identity must be configured correctly.

### Contribution graph

The GitHub contribution graph has its own rules for counting contributions. A commit timestamp alone does not guarantee that GitHub will count the commit as a contribution.

---

# 🧪 Recommended Setup for Testing

When experimenting with the project, start with a small number of commits:

```javascript
makeCommits(5);
```

After confirming that everything works correctly, increase the number if necessary.

---

## 📌 Quick Reference

| Goal | `startDate` | `endDate` |
|------|-------------|-----------|
| 2024 only | `2024-01-01` | `2024-12-31` |
| 2025 only | `2025-01-01` | `2025-12-31` |
| 2026 only | `2026-01-01` | `2026-12-31` |
| 2024–2026 | `2024-01-01` | `2026-12-31` |
| Custom period | Your date | Your date |

---

<p align="center">
  Made for experimentation with Git dates and history.
</p>
