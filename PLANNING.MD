planning_content = """# Personal Budget Manager — Planning

## 1. Purpose
Build a simple, menu-driven Python program that helps a user track their personal finances. The user should be able to:
1. Add a new transaction (income or expense),
2. View all transactions,
3. View the current balance,
4. Save the data to a CSV file and exit.

The program must:
- use **pandas** to store and update transactions,
- use **pyinputplus** to validate all user input,
- load from an existing `budget.csv` if it is present,
- otherwise create an empty DataFrame with the correct columns,
- be organised using **functions**.

---

## 2. Data Design

### 2.1 Data structure
All transactions are stored in a **pandas DataFrame** with these columns:

- `date` — string, format `YYYY-MM-DD`
- `description` — short text about the transaction
- `type` — either `"income"` or `"expense"`
- `amount` — float, must be positive
- `category` — for expenses, one of: `"transport"`, `"food"`, `"shopping"`, `"bills"`, `"other"`;  
  for income, we will just store `"income"` in this column.

This DataFrame represents the “in-memory” version of the budget.

### 2.2 File
- File name: **`budget.csv`**
- On program start:
  - try to read `budget.csv`
  - if it exists → load it into a DataFrame
  - if it does **not** exist → create an empty DataFrame with the 5 columns above
- On “Save and exit”:
  - sort by date (optional, for nicer output)
  - write the DataFrame back to `budget.csv` (overwrite)

---

## 3. Program Flow

1. **Start program**
2. **Load or create** the budget DataFrame
3. **Run a test** on the balance function (assignment requirement: `assert`)
4. Enter a **loop**:
   - show menu
   - get user choice (validated with pyinputplus)
   - call the function that matches the menu choice
   - repeat until user chooses “Save and exit”
5. **Save** the DataFrame to CSV
6. **Exit**

---

## 4. Menu Design

The menu is shown on each loop:

1. Add transaction  
2. View all transactions  
3. View current balance  
4. Save and exit

User input for the menu is validated using:

```python
pyip.inputChoice(["1", "2", "3", "4"])
