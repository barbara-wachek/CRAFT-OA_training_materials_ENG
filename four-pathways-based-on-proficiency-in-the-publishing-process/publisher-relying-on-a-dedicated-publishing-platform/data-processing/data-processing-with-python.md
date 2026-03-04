# Data Processing with Python

The following section is an invitation to the world of Python – a tool that can greatly simplify and automate many data processing tasks. This is not a full-scale programming course, but an overview of practical applications that show how even simple scripts can support everyday work. If you're just getting started with Python or looking for inspiration for your own projects, these examples can be a good starting point.

## Python and Jupyter Lab/Google Colab

**Python** is a general-purpose programming language that is popular for its simplicity and readability.

[Jupyter Lab](https://jupyter.org/try) and [Google Colab](https://colab.research.google.com/) are interactive environments that allow you to create and execute Python code directly in your browser. Ideal for data mining, cleaning, reporting and visualization.

Typical tasks for which Python scripts can be used:

* Validation and completion of metadata (e.g. ORCID, DOI, affiliations).
* Exporting data to Crossref, PubMed, DOAJ
* Conversion of data between systems (e.g. from OJS to another platform)
* Automatic reporting and synchronization with API

### APIs of publishing systems (OJS, Crossref, ORCID)

One common activity that Python is used for is interacting with the APIs (Application Programming Interface) of various services. APIs allow data from systems such as OJS, Crossref or ORCID to be accessed programmatically – without having to manually search the interfaces.

**Examples of API usage:**

* Downloading data on published articles from OJS
* Verifying that each article has a valid DOI (Crossref)
* Download ORCID data of authors (e.g., affiliations)

**An example of checking whether the indicated DOI is in the Crossref system using the Python language and the `requests` library**

```python
import requests

doi = '10.18778/8088-337-6'
response = requests.get(f"https://api.crossref.org/works/{doi}")
if response.status_code == 200:
    print("DOI OK")
else:
    print("DOI does not exist")
```

{% hint style="info" %}
You can try the above code snippet using [Google Colab ](https://colab.research.google.com/)(a Google account is required) or using [Jupyter Lab](https://jupyter.org/try).
{% endhint %}

Using interactive environments and the Python language, you can also:

* Process CSV files with editorial data.
* Create automated publication reports.
* Create charts: number of submissions per month, number of reviews, etc.

**Example of data filtering and analysis**

Assuming we have a CSV file that contains a `date_submitted` column with dates, we can visualize how many submissions fall into each month.

```python
import pandas as pd
df = pd.read_csv('submissions.csv')
df['data'] = pd.to_datetime(df['date_submitted'])
df.groupby(df['data'].dt.month)['id'].count().plot(kind='bar')
```

**Filtering articles without a DOI:**

Assuming that our sheet has a `DOI` column, we can easily filter out articles that do not have a number assigned.

```python
without_doi = df[df['DOI'].isnull()]
print(without_doi[['title', 'author', 'date_submitted']])
```

By developing your skills in using Python and using APIs, you can significantly expand your ability to work with the data produced during the publishing process.

**If you'd like to see an example of a task that uses a Python script to register DOI numbers for archived articles, go to the section below.**

{% content-ref url="../../use-case-doi-registration.md" %}
[use-case-doi-registration.md](../../use-case-doi-registration.md)
{% endcontent-ref %}
