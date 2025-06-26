# CI Dataset Filtering and Collection Summary

This document summarizes the step-by-step filtering process used to prepare the dataset for analyzing GitHub Actions CI workflows in JavaScript repositories.

---

## Step 1: Initial Dataset Acquisition

* **Source**: [SEART GitHub Search Engine](https://seart-ghs.si.usi.ch/)
* **Criteria**: JavaScript projects with more than 10 commits
* **Format**: CSV
* **Total Projects Retrieved**: **237,215**
* **CSV File Size**: \~233.5 MB

This dataset serves as the foundational input for subsequent filtering and analysis.

---

## Step 2: Filter Active Projects

* **Goal**: Retain only repositories with at least one commit between **May 2024** and **May 2025**.
* **Method**: Applied a date filter using commit-related metadata from the CSV file (without cloning repositories).
* **Projects Remaining**: **38,763**

This step ensures the analysis focuses on currently maintained and active projects.

---

## Step 3: Filter Projects Using GitHub Actions CI

* **Goal**: Identify repositories that utilize **GitHub Actions** for CI/CD.
* **Method**: Used the GitHub API to detect `.yml`/`.yaml` workflow files under `.github/workflows/` directory.
* **Projects Identified with CI**: **14,763** (out of 38,763 active projects)

These repositories form the base for CI behavior and performance analysis.

---

## Step 4: Retrieve CI Workflow and Build Data

* **Tasks**:

  * Download CI configuration YAML files
  * Fetch metadata for the **most recent CI run** (on `main` or `master` branch) per project
  * Extract features: runner image, duration, job/step count, caching, matrix strategy, etc.

* **CI Run Records Retrieved**: **12,675**

* **Workflow Configuration Files Collected**: **13,730**

* **Repositories with Both Data Sets**: **11,800**

This final dataset represents the **clean and complete set of CI-active JavaScript repositories** used for analysis.

---

## Summary Table

| Step                         | Count   |
| ---------------------------- | ------- |
| Initial JS Projects          | 237,215 |
| Active (May 2024–May 2025)   | 38,763  |
| Using GitHub Actions         | 14,763  |
| Valid CI Runs Retrieved      | 12,675  |
| Workflow Files Collected     | 13,730  |
| Final Dataset (Intersection) | 11,800  |

---
