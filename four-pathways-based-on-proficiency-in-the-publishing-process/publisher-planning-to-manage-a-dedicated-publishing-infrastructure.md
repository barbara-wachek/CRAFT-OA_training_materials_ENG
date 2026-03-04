---
icon: face-monocle
---

# Publisher planning to manage a dedicated publishing infrastructure

The process of transitioning to a self-managed publishing infrastructure is not just a technological decision, but more importantly an operational and organizational transformation. For the change to be effective and bring long-term benefits, it is worth taking care of several strategic areas:

#### 1. Develop a realistic transformation map

Before the organization takes technical action, it is necessary to prepare a detailed transition map. It should include:

* Audit of current infrastructure and dependencies (hosting, management systems, external APIs),
* Identify components that can be taken over internally (e.g., publishing system, user management),
* Identify which services will require gradual decoupling (e.g., DOI, backup, technical support).

{% hint style="info" %}
A publisher using third-party OJS hosting can first run a test OJS instance on its own server to build competence before production migration.
{% endhint %}

#### 2. Building internal technical competence

Moving to your own infrastructure doesn't have to mean a full IT team right away, but it should assume:

* Hiring (or developing) a technical person familiar with the basics of Linux, database and PHP system administration (OJS),
* Developing a basic understanding of versioning systems (e.g., Git) and plugin structures,
* Investment in training and documentation – both internally and using the resources of the open source community (PKP Docs, PKP Forum).

{% hint style="info" %}
The editorial team does not have to be technical, but they should understand the structure of the system's work and know which processes can be automated.
{% endhint %}

#### 3. Gradual assumption of responsibility for system components

It is not necessary to build everything at once. It's worth starting with:

* System configuration management (e.g., `config.inc.php` in OJS),
* Self-upgrade the software (e.g., upgrade to the latest OJS version),
* Integration of official plug-ins (Crossref, ORCID, XML export),
* Testing local modifications on the development environment.
