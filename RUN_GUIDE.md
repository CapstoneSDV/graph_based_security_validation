# ARXML Security Regression Detector - Execution & Testing Guide

This guide provides step-by-step instructions for running, testing, and visualizing the project on your system.

---

## 🚀 1. Master Evaluation & Figure Generation (Recommended)

Run the full automated suite to execute all unit tests, evaluate 11 real-world CVE scenarios, benchmark 285 mutation test cases, and generate all publication-ready IEEE figures and reports.

```powershell
python run_full_evaluation.py
```

### Generated Outputs:
- **`docs/results.md`**: Complete markdown report with Precision, Recall, F1, and FPR metrics.
- **`docs/results.json`**: Raw numerical experimental dataset.
- **`out/figures/`**: IEEE-formatted vector figures (`fig1_confusion_matrices`, `fig2_detection_by_category`, `fig3_composition_order`, `fig4_scenario_matrix`) in `.pdf`, `.svg`, and `.png`.
- **`scenario_runs/RESULTS.md`**: Summary grid for the 11 real-world CVE scenarios.

---

## 🖥️ 2. Desktop GUI Application

Launch the interactive desktop interface to browse for "Before" and "Updated" ARXML files, configure roles, and inspect side-by-side graph topology visualizations in your web browser.

```powershell
python gui.py
```

---

## 🛡️ 3. Real-World CVE Scenarios Suite

Run the 11 documented vehicle security exploit scenarios (Jeep Cherokee, BMW ConnectedDrive, Tesla 2016 OTA, Mitsubishi Outlander, FCA Recall, Nissan API, Spireon Fleet, SOME/IP, Supply Chain SDK, 2024 Kia Telematics, 2023 Toyota CAN Injection).

```powershell
python run_scenarios.py
```

---

## 🧪 4. Automated Unit Test Suite

Run the full `pytest` test suite containing 401 automated unit tests verifying parsers, graph building, SecOC resolution, reachability analysis, and gate logic.

```powershell
pytest tests/
```

---

## 💻 5. Manual CLI Analysis

Perform a security diff directly between two ARXML snapshots using the CLI:

```powershell
python -m arxml_secdiff --before tests/fixtures/scenario_b_v1.arxml --updated tests/fixtures/scenario_b_v2.arxml --roles tests/fixtures/scenario_b_roles.yaml --verbose
```

### CLI Flags Reference:
- `--before <file.arxml>`: Path to the baseline snapshot.
- `--updated <file.arxml>`: Path to the release candidate snapshot.
- `--roles <file.yaml>`: HARA/TARA seed roles (Entry Points & Critical Nodes).
- `--export-graphs`: Export attack topology diagrams to `.dot`, `.json`, and `.png`.
- `--format json`: Export machine-readable JSON report for CI/CD gates.

---

## 📁 Artifact Locations

| Artifact | Location |
|---|---|
| **Markdown Evaluation Report** | `docs/results.md` |
| **CVE Scenarios Results** | `scenario_runs/RESULTS.md` |
| **IEEE Publication Figures** | `out/figures/` |
| **Scenario Artifacts** | `scenario_runs/` |
