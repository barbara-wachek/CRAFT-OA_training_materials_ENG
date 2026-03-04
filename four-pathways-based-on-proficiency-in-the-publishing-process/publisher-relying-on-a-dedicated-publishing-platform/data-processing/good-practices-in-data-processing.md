# Good Practices in Data Processing

Data processing plays a key role in ensuring the quality, reliability and reproducibility of analyses and reports produced for scientific publications. Standardised approaches not only increase the efficiency of the work, but also promote transparency and compliance with ethical and legal standards.

### **Data quality**

* **Regular cleaning and validation** – Data should be systematically checked for consistency, duplicates, deviations from expected values (e.g. dates out of range, typos errors in institution names). Validation should also include validation of data types (e.g. numeric, dates).
* **Avoiding errors and incomplete data** – Missing data should be identified and flagged and coping strategies implemented. Good practice also includes validation for data entry and version control to avoid unintended overwrites.

### Using tools to simplify working with data

* It is worthwhile to reach for available IT tools that support the automation and organisation of data processing. These can range from simple scripts to more advanced solutions that enable the extraction, transformation and organisation of data from different sources (e.g. editorial systems, repositories, spreadsheets or analytical tools). This approach reduces repetitive, manual steps, improves data consistency and facilitates further analysis.

### Safety and regulatory compliance

* **Anonymisation of sensitive data** – Data containing information about authors, reviewers or research participants should be pseudonymised or anonymised for analysis purposes. It is good practice to separate personal identifiers from the main data sets.
* **Compliance with GDPR –** Every stage of processing should comply with the applicable data protection legislation. This includes the right to inspect, correct or delete data and the obligation to keep data only for the necessary time.

### Efficiency and optimisation

* **Use of databases instead of file storage** – For larger or dynamic datasets, the use of relational (e.g. PostgreSQL) or non-relational (e.g. MongoDB) databases significantly improves query speed, security and scalability.

### Documentation of processes

* **Description of transformation, cleaning and analysis methods –** Each step of data processing should be documented in detail, with an explanation of the decisions taken (e.g. which cleaning rules were applied, which filters were implemented).
* **Recording metadata** – Creating and updating metadata (e.g. data sources, acquisition dates, processing authors) is key to ensuring transparency and auditability.
