# Information Gathering Using theHarvester

## Overview

This lab focuses on information gathering using **theHarvester**, an Open-Source Intelligence (OSINT) tool used during the reconnaissance phase of penetration testing.

theHarvester collects publicly available information associated with a target domain from supported public sources. Depending on the source, this information can include email addresses, employee names, hostnames, and subdomains.

The exercise explores installing theHarvester on Kali Linux, executing domain reconnaissance, and exporting collected information for documentation.

## Lab Objectives

- Understand the fundamentals of Open-Source Intelligence (OSINT).
- Explore theHarvester and its role in information gathering.
- Install and configure theHarvester on Kali Linux.
- Perform domain reconnaissance.
- Identify publicly discoverable subdomains and related information.
- Understand how reconnaissance supports penetration testing.
- Export reconnaissance results for further analysis.

## Lab Environment

| Component | Details |
|---|---|
| Operating System | Kali Linux |
| Tool | theHarvester |
| Tool Category | Open-Source Intelligence (OSINT) |
| Target Domain | vulnweb.com |
| Data Source | crt.sh |
| Lab Category | Information Gathering and Reconnaissance |

## Understanding theHarvester

theHarvester is an OSINT tool designed to gather publicly available information associated with a target domain.

It queries supported search engines, public databases, and other information sources to identify information that may help security professionals understand an organization's external attack surface.

Information that may be discovered includes:

- Email addresses.
- Employee names.
- Subdomains.
- Hostnames.
- IP addresses and related infrastructure information, depending on the data source.

## Practical Implementation

### Task 1: Preparing the Kali Linux Environment

The first task involved starting Kali Linux and opening a terminal.

Since newer Kali Linux versions use `pipx` to manage Python applications in isolated environments, the installation process began by checking whether pipx was available.

**Check pipx installation:**

```bash
pipx --version
```

If pipx was not installed, the following commands could be used:

```bash
sudo apt update
sudo apt install -y pipx
```

### Task 2: Installing theHarvester

There are two installation approaches provided in the lab instructions.

**Option 1: Installing through pipx**

```bash
pipx install git+https://github.com/laramies/theHarvester.git
```

This installs theHarvester from its official GitHub repository in an isolated Python environment.

**Option 2: Installing through Kali's APT repositories**

```bash
sudo apt update
sudo apt install theharvester
```

This installs the package maintained in Kali's repositories.

**Note:** These are alternative installation methods. Using both is generally unnecessary and may create PATH or version conflicts. Choose one installation method for the environment.

### Task 3: Verifying the Installation

After installation, the next step is to confirm that theHarvester is accessible from the terminal.

**Command:**

```bash
theHarvester -h
```

The `-h` option displays the available command-line options and usage information.

A successful display of the help menu confirms that the command is available.

### Task 4: Performing Domain Reconnaissance

The next task involved performing a basic information-gathering exercise against a practice domain.

The target selected for this lab was:

`vulnweb.com`

TheHarvester was configured to use `crt.sh` as its information source.

**Command:**

```bash
theHarvester -d vulnweb.com -l 100 -b crtsh
```

**Command Breakdown:**

| Option | Description |
|---|---|
| `-d` | Specifies the target domain. |
| `-l` | Sets the maximum number of results requested. |
| `-b` | Specifies the data source used for information gathering. |
| `crtsh` | Uses the Certificate Transparency search source crt.sh. |

**Purpose:**

The command performs domain reconnaissance using Certificate Transparency information available through crt.sh.

Certificate Transparency logs are publicly accessible records of issued TLS certificates. They can reveal domain names and subdomains included in certificate records.

This makes crt.sh useful for discovering publicly visible subdomains associated with a target domain.

**Selected Data Source:** `crtsh`

Only crt.sh was used as the source for this exercise.

### Task 5: Exporting Reconnaissance Results

theHarvester supports exporting collected information for documentation and further analysis.

The `-f` option specifies an output filename.

**Command:**

```bash
theHarvester -d vulnweb.com -l 100 -b crtsh -f lab_recon
```

This runs the reconnaissance command and saves the results using the specified output filename.

The generated report format depends on the installed version of theHarvester.

Exporting results makes it easier to preserve and review reconnaissance findings.

## Key Concepts Covered

| Concept | Description |
|---|---|
| OSINT | Gathering intelligence from publicly available information sources. |
| theHarvester | A tool for automated domain-related information gathering. |
| Domain Reconnaissance | Collecting information associated with a target domain. |
| Subdomain Enumeration | Identifying subdomains associated with a primary domain. |
| Certificate Transparency | Public logging of issued TLS certificates. |
| crt.sh | A searchable Certificate Transparency log database. |

## Key Learning Outcomes

Through this lab, I explored:

1. The fundamentals of Open-Source Intelligence.
2. The role of theHarvester in penetration testing reconnaissance.
3. Installing Python-based security tools using pipx.
4. Installing security tools through Kali Linux package repositories.
5. Performing domain reconnaissance using theHarvester.
6. Using crt.sh as a Certificate Transparency information source.
7. Understanding how publicly issued certificates can reveal subdomains.
8. Exporting reconnaissance findings for documentation and analysis.

## Security Relevance

Information gathering is an important phase of penetration testing because it helps security professionals understand the publicly exposed information associated with an organization.

Tools such as theHarvester support:

- **External Reconnaissance:** Gathering publicly available information about a target.
- **Subdomain Discovery:** Identifying additional domain assets.
- **Attack Surface Assessment:** Understanding publicly visible infrastructure.
- **OSINT Investigations:** Collecting information from public sources.
- **Security Assessments:** Identifying assets that may require further investigation.

## Conclusion

This lab introduced theHarvester as an OSINT tool for domain information gathering and reconnaissance.

It covered installation, command-line usage, domain enumeration using crt.sh, and exporting collected information.

The exercise demonstrates how publicly available information can provide valuable insight into an organization's external digital footprint.

Understanding OSINT techniques is an important foundation for penetration testing, vulnerability assessment, and broader cybersecurity operations.

## Tools and References

- **Operating System:** Kali Linux
- **Tool:** theHarvester
- **Target Domain:** vulnweb.com
- **Data Source:** crt.sh
- **Official GitHub Repository:** https://github.com/laramies/theHarvester
- **Certificate Transparency Search:** https://crt.sh/

## Security Note

This lab uses a practice domain for educational reconnaissance.

Only gather information on domains and systems within the scope of an authorized security assessment. Public availability of information does not automatically grant permission to conduct further testing.
