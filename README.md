# DevOps Quartile Analysis Project for Novices

Welcome to your hands-on project for learning DevOps quartile analysis! This project is designed to be completely free and online, requiring no software installations.

## Project Goal

To understand how to calculate and interpret quartiles for common DevOps metrics, specifically "Lead Time for Changes."

---

## What are Quartiles?

Quartiles divide a dataset into four equal parts:
* **Q1 (First Quartile):** The value below which 25% of the data falls.
* **Q2 (Second Quartile / Median):** The value below which 50% of the data falls.
* **Q3 (Third Quartile):** The value below which 75% of the data falls.
* **Interquartile Range (IQR):** The range between Q1 and Q3 ($IQR = Q3 - Q1$), representing the middle 50% of the data.

---

## Step-by-Step Guide

### Step 1: Access the Raw Data

Our simulated DevOps metric data is in `devops_metrics.csv`.

1.  Click on the `devops_metrics.csv` file in this repository.
2.  Click the "**Raw**" button. This will show you the plain CSV data.
3.  **Copy all the data** (including the header "LeadTimeForChanges_Hours").

### Step 2: Analyze Data in Google Sheets (or Excel Online)

We'll use a spreadsheet for easy calculation and visualization.

1.  **Open Google Sheets:** Go to [sheets.google.com](https://docs.google.com/spreadsheets/create) and create a new blank spreadsheet. (If you prefer, you can use Excel Online via your Microsoft account).
2.  **Paste Data:** Paste the copied raw CSV data into cell **A1** of your new spreadsheet. Make sure "LeadTimeForChanges_Hours" is in A1, and your numbers are in A2 down to A21.
3.  **Sort the Data:**
    * Select the entire column containing your data (**Column A**).
    * Go to **Data -> Sort range**.
    * Check "Data has header row" and select "LeadTimeForChanges_Hours" for sorting.
    * Choose "**A -> Z**" (ascending order).
4.  **Calculate Quartiles using Functions:**
    In separate cells (e.g., B1, B2, B3), enter the following formulas. **Ensure your data is in the range A2:A21.** If your data range is different (e.g., if you have more or less data points), you **must** adjust the `A2:A21` part of the formulas accordingly.

    * **Q1 (25th percentile):**
        ```excel
        =QUARTILE(A2:A21, 1)
        ```
        *Enter this into an empty cell, for example, cell B1.*

    * **Q2 (Median/50th percentile):**
        ```excel
        =QUARTILE(A2:A21, 2)
        ```
        *Enter this into an empty cell, for example, cell B2.*

    * **Q3 (75th percentile):**
        ```excel
        =QUARTILE(A2:A21, 3)
        ```
        *Enter this into an empty cell, for example, cell B3.*

    * **IQR (Interquartile Range):**
        ```excel
        =B3-B1
        ```
        *Enter this into an empty cell, for example, cell B4. This formula assumes you placed the Q1 calculation in cell B1 and the Q3 calculation in cell B3. If you put them in different cells, update `B3` and `B1` to match their actual locations.*

    You will now see the calculated quartile values.

### Step 3: Verify with an Online Quartile Calculator

It's good practice to cross-check your calculations.

1.  **Copy Just the Numbers:** From your sorted Google Sheet, copy only the numerical data (e.g., A2:A21).
2.  **Go to an online calculator:** Visit a website like [https://www.calculatorsoup.com/calculators/statistics/quartile-calculator.php](https://www.calculatorsoup.com/calculators/statistics/quartile-calculator.php) (or search for "online quartile calculator").
3.  **Paste Data:** Paste your numbers into the input box (usually one number per line or separated by commas).
4.  **Calculate:** Click the "Calculate" or "Compute" button.
5.  **Compare:** Verify that the Q1, Q2, and Q3 values match what you calculated in Google Sheets.

---

### Step 4: Interpret the Results for DevOps

Let's assume your calculated quartiles are something like:
* **Q1:** ~2.1 hours
* **Q2 (Median):** ~3.0 hours
* **Q3:** ~3.9 hours
* **IQR:** ~1.8 hours

**What does this mean for "Lead Time for Changes"?**

* **Q1 (2.1 hours):** 25% of your changes are deployed in 2.1 hours or less. This is your fastest quartile!
* **Q2 (3.0 hours):** Half of your changes are deployed in 3.0 hours or less. This is your typical lead time.
* **Q3 (3.9 hours):** 75% of your changes are deployed in 3.9 hours or less. The remaining 25% (the slowest ones) take longer than 3.9 hours.
* **Interquartile Range (1.8 hours):** The middle 50% of your deployments have a lead time spread of 1.8 hours.

**Actionable Insights:**

* **Identify Bottlenecks:** The gap between Q2 and Q3 (or Q3 and the maximum value) can highlight areas where processes are slower. For instance, if Q3 is significantly higher than Q2, it indicates that the last 25% of deployments are taking much longer, potentially due to manual approvals, slow testing, or waiting for infrastructure.
* **Benchmark Performance:** You can compare your median (Q2) or Q1 with industry benchmarks for "elite" or "high-performing" DevOps teams.
* **Set Targets:** Instead of aiming to reduce the "average" lead time (which can be skewed by outliers), you can aim to reduce your Q3, meaning you're improving the speed of your slower deployments. Or, strive to get more deployments into the Q1 category.
* **Outlier Detection:** Look at data points significantly above Q3 + (1.5 * IQR). These are potential outliers that indicate exceptional issues (e.g., a deployment that took 10+ hours when most are under 4). Investigate these specific cases!

---

### Step 5: Visualize with a Box Plot (Optional but Recommended)

A box plot is the best way to visualize quartiles.

1.  **In Google Sheets:**
    * Select your data column (e.g., A1:A21).
    * Go to **Insert -> Chart**.
    * Under "Chart type," look for "**Box chart**" (sometimes called "Box and whisker chart").
    * Google Sheets will generate a box plot showing Q1, Q2 (median), Q3, and often outliers.



This visual will make it much easier to grasp the distribution of your lead times.

---

### Step 6: Expand Your Learning (Self-Directed)

* **Try other metrics:** Create new CSV files (or add columns) for "Deployment Frequency," "Change Failure Rate" (e.g., 0 for success, 1 for failure), or "Mean Time To Restore (MTTR)" and perform the same analysis.
* **More Data:** Add more data points to your `devops_metrics.csv` and re-run the analysis to see how quartiles change.
* **Research DORA Metrics:** The "Lead Time for Changes" is one of the four key [DORA metrics](https://cloud.google.com/devops/state-of-devops/metrics). Research the others and consider how quartile analysis applies to them.

---

Good luck with your DevOps quartile analysis journey! Feel free to fork this repository or create your own to continue practicing.
