# 🔐 Gitleaks Custom Config – Ready for Secure Git Scanning

This repository provides a **production-ready `gitleaks.toml` config file** with custom rules to detect real-world secrets in Git repositories.

It helps DevSecOps teams, security engineers, and developers:

- Detect hardcoded secrets and credentials  
- Avoid false positives  
- Integrate easily into CI/CD pipelines

For organization Git accounts, please request a free commercial license at the  <a href="https://gitleaks.io/">Official Gitleaks Website</a>

---

## 🧠 What’s Inside?

✅ Custom rules for detecting:

- Passwords (`password`, `pass`, `passwd`, etc.)  
- Environment secrets (like `DB_PASSWORD`, `AUTH_TOKEN`)  
- API keys  
- Client secrets  
- Private keys  
- JWT tokens  
- Database-specific secrets  
- Generic auth credentials  

✅ Optimized for GitHub Actions or CLI usage  

---

## 📁 File Structure  
Choose your prefered scan method for your `.github/workflows/gitleaks.yml` from down below.  
Create the following file structure after cloning the repo you want to scan:  
```bash
repo
├── .gitleaks.toml # Custom rules file
└── .github
    └── workflows
        └── gitleaks.yml # Gitleaks main configuration file

```
## Activating a Scan
- To perform a scan, make a new commit and push the code back into your GitHub repo.
- It will initiate a GitHub Action automatically in your cloud GitHub repo.
- You can also initiate a local CLI scan, based on the details below.

## Scanning Last Commit Only (CI/CD Use)  
If you're using Gitleaks in a CI/CD pipeline and want to scan only the latest commit (not the full history):  
Copy the configuration from `conf/gitleaks-latest-commit.yml`, into `.github/workflows/gitleaks.yml` as of the above file structure.

This approach is ideal for fast, focused scans with minimal noise during push events or pull requests.

## Scanning Full Git History (All Commits)  
To scan the entire commit history of the branch, Copy the configuration from `conf/gitleaks-all-commits.yml`,  
into `.github/workflows/gitleaks.yml` as of the above file structure.

This is great for performing a full audit on legacy repositories or before open-sourcing a project.

## Scanning Locally (CLI)
To run Gitleaks manually with any of these configs (in the source code directory):

```bash
sudo apt update
sudo apt install gitleaks -y
gitleaks detect --source . --config .gitleaks.toml
```

```bash

    ○
    │╲
    │ ○
    ○ ░
    ░    gitleaks

Finding:     password = 123sdfasf
Secret:      password = 123sdfasf
RuleID:      generic-password
Entropy:     3.521928
File:        test-folder/pass.txt
Line:        1
Commit:      2a392ce1b4fe7d0c3830ba98b528bd8684873355
Author:      Amit Shafnir
Email:       [Commiter Email]
Date:        2025-04-20T17:24:28Z
Fingerprint: 2a392ce1b4fe7d0c3830ba98b528bd8684873355:test-folder/pass.txt:generic-password:1
```

## ✅ Compatibility  
Gitleaks v8.x+  
GitHub Actions  
May work but haven't been tested with GitLab CI, Bitbucket Pipelines, Jenkins, etc.  

For more information and custom settings, visit the official <a href="https://github.com/gitleaks/gitleaks-action">gitleaks-action</a> repo.
