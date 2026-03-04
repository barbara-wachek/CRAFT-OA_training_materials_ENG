# Data Processing with Python

The following section is an invitation to the world of Python – a tool that can greatly simplify and automate many data processing tasks. This is not a full-scale programming course, but an overview of practical applications that show how even simple scripts can support everyday work. If you're just getting started with Python or looking for inspiration for your own projects, these examples can be a good starting point.

## Python and Jupyter Lab/Google Colab

**Python** is a general-purpose programming language that is popular for its simplicity and readability.

[Jupyter Lab](https://jupyter.org/try) and [Google Colab](https://colab.research.google.com/) are interactive environments that allow you to create and execute Python code directly in your browser. They are ideal for data mining, cleaning, reporting and visualization.

Typical tasks for which Python scripts can be used:

* Validation and completion of metadata (e.g. ORCID, DOI, affiliations).
* Exporting data to Crossref, PubMed, DOAJ
* Conversion of data between systems (e.g. from OJS to another platform)
* Automatic reporting and synchronization with API

### Metadata validation and standardization – Python scripts + Pandas library

**Example application:**

Validate the correctness of the DOI and ORCID in the OJS export file (we assume that the articles.csv file has DOI and ORCID columns):

```python
import pandas as pd
import re

df = pd.read_csv("articles.csv")

def validate_doi(doi):
    return bool(re.match(r"^10\.\d{4,9}/[-._;()/:A-Z0-9]+$", doi, re.I))

def validate_orcid(orcid):
    return bool(re.match(r"^https?://orcid\.org/\d{4}-\d{4}-\d{4}-\d{4}$", orcid))

df["DOI_status"] = df["DOI"].apply(lambda x: "OK" if validate_doi(str(x)) else "Invalid")
df["ORCID_status"] = df["ORCID"].apply(lambda x: "OK" if validate_orcid(str(x)) else "Invalid")

df.to_excel("validated_articles.xlsx", index=False)

```

{% hint style="info" %}
You can try the above code snippet using  [Google Colab ](https://colab.research.google.com/)(a Google account is required) or using [Jupyter Lab](https://jupyter.org/try).
{% endhint %}

### ETL – data extraction, transformation and loading

Presented below is an example of using Python and an SQL query to generate a report that will show a list of articles with titles and submission dates – in English only.

The SQL database that we will query can be, for example, the MySQL database associated with the OJS software.

**SQL query example:**

```sql
SELECT 
    s.submission_id, 
    s.date_submitted, 
    ps.setting_value AS title
FROM 
    submissions s
JOIN 
    publications p ON s.current_publication_id = p.publication_id
JOIN 
    publication_settings ps ON p.publication_id = ps.publication_id
WHERE 
    ps.setting_name = 'title' 
    AND ps.locale = 'en_US';
```

**This query returns:**

* Article ID
* Submission date
* Title in English

**Python script that connects to a SQL database and generates a report based on the above query**

```python
import pandas as pd
import mysql.connector

# OJS database connection configuration
conn = mysql.connector.connect(
    host="localhost",
    user="ojs_user",
    password="your_password",
    database="your_ojs_database_name"
)

# SQL query
query = """
SELECT 
    s.submission_id, 
    s.date_submitted, 
    ps.setting_value AS title
FROM 
    submissions s
JOIN 
    publications p ON s.current_publication_id = p.publication_id
JOIN 
    publication_settings ps ON p.publication_id = ps.publication_id
WHERE 
    ps.setting_name = 'title' 
    AND ps.locale = 'en_US';
"""

# Loading the data into the DataFrame
df = pd.read_sql(query, conn)

# Save as Excel file
df.to_excel("articles_report.xlsx", index=False)

# Close the connection
conn.close()

print("The report was saved as 'articles_report.xlsx'")
```

**If you'd like to see an example of a task that uses a Python script to register DOI numbers for archived articles, go to the section below.**

{% content-ref url="../../use-case-doi-registration.md" %}
[use-case-doi-registration.md](../../use-case-doi-registration.md)
{% endcontent-ref %}
