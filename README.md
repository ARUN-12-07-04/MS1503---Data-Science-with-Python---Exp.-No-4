# Experiment 7 (`exp5.pdf`): Yearly Revenue Growth Visualization Using Matplotlib

## 🎯 Aim

To visualize the yearly trend of company revenue and expenses from 2017 to 2023 using Matplotlib by plotting multi-line charts with customized markers, labels, legends, gridlines, and point annotations.

## 📊 Dataset

The dataset tracks yearly financial figures (in **Lakhs**) across **7 years** (`2017–2023`):

| Year | Revenue (in Lakhs) | Expenses (in Lakhs) | Net Profit (in Lakhs) |
| :---: | :---: | :---: | :---: |
| **2017** | 20 | 15 | 5 |
| **2018** | 25 | 18 | 7 |
| **2019** | 28 | 22 | 6 |
| **2020** | 35 | 27 | 8 |
| **2021** | 40 | 30 | 10 |
| **2022** | 45 | 33 | 12 |
| **2023** | 52 | 38 | 14 |

## ⚙️ Algorithm

1. **Start** the program.
2. **Import Libraries**: Import `matplotlib.pyplot` as `plt` for plotting and `numpy` as `np` for numeric array generation and index lookup.
3. **Initialize Dataset**:
   * Generate an array `years` spanning `2017` to `2023` using `np.arange(2017, 2024)`.
   * Define lists `revenue` and `expenses` representing annual amounts in Lakhs.
4. **Configure Figure & Plot Lines**:
   * Initialize a figure canvas of size $8 \times 5$ inches using `plt.figure(figsize=(8, 5))`.
   * Plot `revenue` against `years` as a solid green line with circular markers (`marker='o'`).
   * Plot `expenses` against `years` as a dashed red line (`linestyle='--'`) with square markers (`marker='s'`).
5. **Format Chart Aesthetics**:
   * Add a bold chart title (`plt.title()`) and axis labels (`plt.xlabel()`, `plt.ylabel()`).
   * Enable dashed semi-transparent gridlines (`plt.grid()`) and place the legend in the upper-left corner (`plt.legend(loc='upper left')`).
6. **Annotate Peak Values**:
   * Find the indices of maximum revenue and maximum expenses using `np.argmax()`.
   * Highlight both peak data points on the chart with directional arrows and text callouts using `plt.annotate()`.
7. **Adjust Layout & Display**:
   * Prevent label clipping via `plt.tight_layout()` and render the final plot with `plt.show()`.
8. **Stop** the program.

### 📝 Pseudocode

```text
BEGIN
    IMPORT matplotlib.pyplot AS plt
    IMPORT numpy AS np

    years    ← ARANGE(2017, 2024)
    revenue  ← [20, 25, 28, 35, 40, 45, 52]
    expenses ← [15, 18, 22, 27, 30, 33, 38]

    CREATE FIGURE(8, 5)
    PLOT(years, revenue, style="solid", marker="o", color="green", label="Revenue")
    PLOT(years, expenses, style="dashed", marker="s", color="red", label="Expenses")

    SET TITLE("Company Revenue and Expense Trends (2017 - 2023)")
    SET XLABEL("Year"), YLABEL("Amount (in Lakhs)")
    ENABLE GRID(True), LEGEND(loc="upper left")

    max_rev_idx ← ARGMAX(revenue)
    max_exp_idx ← ARGMAX(expenses)

    ANNOTATE("Highest Revenue", AT (years[max_rev_idx], revenue[max_rev_idx]))
    ANNOTATE("Highest Expense", AT (years[max_exp_idx], expenses[max_exp_idx]))

    ADJUST TIGHT_LAYOUT()
    SHOW PLOT()
END
```

## 🛠️ Functions and Methods Used

| Category | Function / Method | Purpose / Description |
| :--- | :--- | :--- |
| **Numerical Operations** | `np.arange()` | Generates evenly spaced integer years (`2017` through `2023`) |
| | `np.argmax()` | Returns the array index of the maximum revenue and expense values |
| **Line Plotting** | `plt.figure()` | Initializes a new figure window with custom dimensions |
| | `plt.plot()` | Draws line plots with customized markers, colors, line styles, and widths |
| **Chart Formatting** | `plt.title()`, `plt.xlabel()`, `plt.ylabel()` | Adds descriptive title and axis labels with custom font sizes |
| | `plt.grid()`, `plt.legend()` | Adds background gridlines and displays series labels in the upper left |
| **Annotations & Display** | `plt.annotate()` | Places text labels with arrows pointing to peak revenue and expense points |
| | `plt.tight_layout()`, `plt.show()` | Optimizes spacing to avoid overlapping elements and renders the figure |

## 💻 Program / Code

```python
# Company Revenue and Expense Visualization using Matplotlib
import matplotlib.pyplot as plt
import numpy as np

# Step 1: Create dataset
years = np.arange(2017, 2024)
revenue = [20, 25, 28, 35, 40, 45, 52]   # in lakhs
expenses = [15, 18, 22, 27, 30, 33, 38]  # in lakhs

# Step 2: Plot Revenue and Expenses
plt.figure(figsize=(8, 5))
plt.plot(years, revenue, marker='o', color='green', linewidth=2, label='Revenue')
plt.plot(years, expenses, marker='s', color='red', linestyle='--', linewidth=2, label='Expenses')

# Step 3: Add titles, labels, and grid
plt.title("Company Revenue and Expense Trends (2017 - 2023)", fontsize=13, fontweight='bold')
plt.xlabel("Year", fontsize=11)
plt.ylabel("Amount (in Lakhs)", fontsize=11)
plt.grid(True, linestyle='--', alpha=0.6)

# Step 4: Add legend
plt.legend(loc='upper left')

# Step 5: Annotate highest revenue and expense
max_rev_index = np.argmax(revenue)
max_exp_index = np.argmax(expenses)

plt.annotate(
    f"Highest Revenue: {revenue[max_rev_index]}L",
    xy=(years[max_rev_index], revenue[max_rev_index]),
    xytext=(years[max_rev_index] - 1.2, revenue[max_rev_index] + 1.5),
    arrowprops=dict(facecolor='black', arrowstyle='->')
)

plt.annotate(
    f"Highest Expense: {expenses[max_exp_index]}L",
    xy=(years[max_exp_index], expenses[max_exp_index]),
    xytext=(years[max_exp_index] - 1.2, expenses[max_exp_index] + 2.0),
    arrowprops=dict(facecolor='black', arrowstyle='->')
)

# Step 6: Adjust layout and show plot
plt.ylim(12, 57)  # Add headroom so top annotation does not overlap the title
plt.tight_layout()
plt.show()
```

## 📈 Key Insights from Visualization

* **Consistent Growth:** Both revenue and expenses exhibit steady upward trajectories over the 7-year span from 2017 to 2023.
* **Peak Performance (2023):** Revenue peaked at **52 Lakhs** ($+160\%$ growth since 2017) while expenses reached **38 Lakhs** ($+153\%$ increase since 2017).
* **Expanding Profit Margin:** The vertical gap between the revenue curve and expense curve widens consistently each year, growing from **5 Lakhs** in 2017 to **14 Lakhs** in 2023.

## ✅ Result

The program successfully creates datasets for yearly company revenue and expenses and renders an annotated multi-line comparison chart using Matplotlib.

## 🚀 How to Run

1. Install Matplotlib and NumPy (if not already installed):
   ```bash
   pip install matplotlib numpy
   ```
2. Run the script:
   ```bash
   python exp5_revenue_visualization.py
   ```