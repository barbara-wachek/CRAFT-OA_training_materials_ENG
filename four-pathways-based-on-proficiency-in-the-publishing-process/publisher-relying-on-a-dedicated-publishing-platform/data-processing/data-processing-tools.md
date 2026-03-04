# Data Processing Tools

When working with data - whether managing requests, creating reports or analysing – it is worth taking advantage of the tools available that can greatly simplify and streamline these processes. The following examples show what can be achieved using popular and often free solutions such as spreadsheets or data cleaning tools.

This is not a user manual, but an overview of the possibilities – to help you choose an approach tailored to your own needs. The aim is to show the potential of tools that can improve data quality and automate some of the work.

### Spreadsheets

These tools are easily accessible and intuitive, ideal for simply organising, filtering and analysing data. They work particularly well when working with smaller collections and allow you to quickly detect deficiencies, create summaries or generate reports.

Examples of worksheet software:

1. Google Sheets
2. Excel
3. LibreOffice Calc

#### What can be done?

* Organise submission data (e.g. names, affiliations, ORCID).
* Automatically detect and flag deficiencies (e.g. no DOI, no reviewer).
* Create reports as PDF or editable text documents.

#### Example of operation:

1. **Import of data from a CSV file (e.g. export from OJS):**
   * **Excel:** Go to the **Data** tab → **From Text/CSV** → use **Power Query** to load the data and transform columns as needed.
   * **Google Sheets:** **File** → **Import** → **Upload** your CSV file.
2. **Adding a column with automatic DOI format validation (Google Sheets):**

Assuming that our data contains DOI information in column C, which most often has the following format 10.xxxx/xxxxx, we can check its correctness using regular expressions (RegEx, a markup language for finding patterns).

```excel-formula
=IF(REGEXMATCH(C2, "^10\.\d{4,9}/[-._;()/:A-Z0-9]+$"), "OK", "Incorrect DOI")
```

{% hint style="info" %}
`^10\.` – begins with ‘10.’

`\d{4,9}` – 4 to 9 digits

`/...` – slash, followed by a sequence of characters: letters, digits, special characters

`REGEXMATCH` returns `TRUE` or `FALSE`
{% endhint %}

### Data cleaning and data mining tools - [OpenRefine](https://openrefine.org/)

It is a tool for cleaning, organising and processing data. It allows the removal of duplicates, the consolidation of data from different sources and the transformation of data into appropriate formats. Its flexibility makes it suitable for both simple tasks and more complex data processing. With OpenRefine, data quality can be improved by removing errors and inconsistencies, which affects the accuracy of analyses and reports.

#### What can be done?

* Harmonise the names of institutions and authors.
* Seek out and correct inconsistent affiliations.
* Identify duplicate submissions or authors.

#### Exampl&#x65;**:**

1. **Importing data from CSV:**
   * Open OpenRefine → New project → select the CSV file with metadata.
2. **Faceting and clustering of data:**
   * Select the column "Affiliation" → "Facet" → "Text Facet" → see all unique values.
   * Merge similar entries (e.g., "Université de Paris” and “Paris University") using "Cluster and Edit".
3. **Data export:**
   * When finished → "Export" → CSV → data ready to be loaded back into the sheet.

{% hint style="info" %}
For details and examples of use, see the official OpenRefine documentation: [https://openrefine.org/docs](https://openrefine.org/docs).
{% endhint %}
