# Data Processing Workflow

In order to effectively use data in analyses, reports and decision-making processes within a scientific publishing environment, it is necessary to prepare the data properly. The process of data processing involves several key steps – from the acquisition of data from sources, to its cleaning, to its transformation into a usable form for further activities. Each of these steps directly affects the quality of the final results and the possibility of further use and interpretation.

### How does the data processing workflow proceed?

1.  Identifying data sources and ensuring access

    The first step is to identify where the data will come from and ensure appropriate access. For scientific publishers, this could be:

    * Scientific databases (e.g. Scopus, Web of Science, PubMed).
    * Journal management systems (e.g. OJS – Open Journal Systems).
    * Institutional repositories (e.g. arXiv, Zenodo, Europe PMC).
    * CSV or Excel files containing article and author information.
    * APIs of external services (e.g. CrossRef API for retrieving DOIs and publication metadata).


2.  Data cleaning and validation

    Data extracted from different sources often contains errors and inconsistencies and therefore requires thorough cleaning and validation.

    * Removing duplicates – It can happen that the same articles appear several times, e.g. in different databases. Identification of duplicates can be done on the basis of DOI, title, author and publication date.
    * Handling missing values – Missing author names, publication dates or affiliations can affect analyses. These can be completed based on other sources (e.g. CrossRef API).
    * Anomaly detection and removal – A typical example of anomalous data is erroneous values outside the intended range (e.g. year 1023 instead of 2023). It is also important to catch other errors, such as incorrectly assigned identifiers (e.g. DOI, ORCID, ISSN).
    * Normalisation of values – Standardisation of author name notation. Formatting of dates (YYYY-MM-DD instead of DD/MM/YYYY). Standardisation of units (e.g. number of citations in thousands).


3.  Data transformation and integration

    Once the data has been cleaned, the next step is to transform it into a uniform format and combine information from different sources.

    * Data aggregation – Grouping of publications by category (e.g. by field of study, institution). Aggregating the number of citations for individual authors and journals. Calculation of average indicators (e.g. article acceptance rate, average review time).
    * Conversion of data formats – CSV → JSON for compatibility with API systems. XML → CSV for better readability in spreadsheets. BibTeX → RIS for export of scientific references.
    * Integrating data from different sources – Combining knowledge from different sources significantly increases the quality and potential of the data produced. In extracting additional information about authors, for example, one can try combining data from ORCID, Google Scholar and Scopus. For metadata, DOIs can be used and information can be extracted using the CrossRef API.



Following the steps described – from thoughtful data acquisition, validation and normalisation to integration and aggregation – helps to ensure a high level of data quality, consistency of analysis and transparency in the process. This not only avoids errors and inconsistencies, but also builds a reliable and reproducible basis for scientific publications, evaluation reports or impact analyses.
