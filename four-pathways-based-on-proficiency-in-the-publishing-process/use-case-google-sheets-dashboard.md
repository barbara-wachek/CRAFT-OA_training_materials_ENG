# USE CASE – Google Sheets dashboard

Below is an example of a dashboard created in Google Sheets based on data exported from OJS. The purpose of this example is to show how raw editorial data can be easily transformed into summaries and visualizations to support the monitoring of the publishing process.

This is not a finished production solution, but a demonstration of the possibilities. Below are also brief descriptions of how to make the various elements of the presented dashboard. This type of solution is easily customizable and can be developed as the scale of the data grows.

## Sample Dashboard in Google Sheets based on data exported from OJS

{% embed url="https://docs.google.com/spreadsheets/d/1pjYq1YSQZ6FFE7UjethJC-zIRHVCDgBAnDJTuZcFEMA/edit?usp=sharing" fullWidth="true" %}
Source: [https://docs.google.com/spreadsheets/d/1pjYq1YSQZ6FFE7UjethJC-zIRHVCDgBAnDJTuZcFEMA/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1pjYq1YSQZ6FFE7UjethJC-zIRHVCDgBAnDJTuZcFEMA/edit?usp=sharing)
{% endembed %}

### **1.** Number of submissions by status

#### **Goal: Track the current status of submissions (e.g. “Submitted”, “In Review”, ‘Accepted’, “Published”).**

#### How to do it:

1. Go to the `Dashboard` worksheet (create a new one if needed).
2. Select **Insert > Pivot table**.
3. **Data source:** Select the entire data range from your data sheet (e.g., `Dane_OJS_Surowe!A1:A1000`).
4. In the Pivot table editor:
   * **Rows:** Select `Status`
   * **Values:** Select any non-empty column, e.g., `Submission ID`, and set **Summarize by: COUNTA**&#x20;
5. Based on this pivot table, insert a column chart:
   * Click on the pivot table → **Insert > Chart** → **Column chart**.
6. Add chart title: **Submission Statuses**.

### **2.** Number of Assigned Submissions

#### **Goal:** Verify workload distribution among editors.

#### How to do it:

1. Create a pivot table:
   * **Rows:** Add `Given Name (Editor 1)` and `Family Name (Editor 1)` (or combine them into a single column beforehand using a formula like `=A2 & " " & B2`)
   * **Values:** Select `Submission ID` and set **Summarize by: COUNTA**.
2. Insert a **Bar chart (horizontal)** to visualize editor workloads.
3. Add chart title: **Number of Submissions Assigned to Editors**.

### **3.** Share of Submissions with ORCID

#### **Goal:** Assessment of metadata quality and compliance with ORCID number requirements.

#### How to do it:

1.  In a helper column, add the following formula:

    ```excel-formula
    =IF(OR(ISBLANK(D2); D2 = ""); "ORCID Invalid"; "ORCID OK")
    ```

    (Assuming column D contains ORCID iDs for Author 1.)
2. Create a pivot table summarizing the helper column:
   * **Rows:** Select the new column with ORCID status.
   * **Values:** Count any consistent non-empty column, e.g., `Submission ID`.
3. Insert a **Donut chart** based on this pivot table.
4. Add chart title: **Share of Submissions with ORCID**.

### 4. Monthly Submission Count

#### **Goal:** Track submission volume by month.

#### How to do it:

1. Add a **helper column** to extract the month and year from the submission date:
   1. Assuming submission dates are in column B, in column C enter:\
      `=TEXT(B2, "YYYY-MM")`. This formats the date into `2024-05`, enabling month-based grouping.
   2. Copy the formula down the column.
2. Create a pivot table:
   1. Select the full data range.
   2. Go to **Insert > Pivot table** and place it in a new sheet for clarity.
3. Configure the pivot table:
   1. **Rows:** Select the helper column with the `"YYYY-MM"` format (e.g., column C).
   2. **Values:** Use `Submission ID` (or another non-empty column) and set **Summarize by: COUNTA**.

Google Sheets will now display the number of requests grouped by month.
