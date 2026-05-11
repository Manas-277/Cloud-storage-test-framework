# Cloud Storage Tiering System — Test Automation Framework

A pytest-based test automation framework built to validate a FastAPI cloud storage tiering system.  
Covers functional correctness, performance benchmarking, and fault injection scenarios across 38 test cases.

**Tech Stack:** Python, pytest, FastAPI, httpx, pytest-benchmark, pytest-cov, GitHub Actions

![CI](https://github.com/Manas-277/Cloud-storage-test-framework/actions/workflows/tests.yml/badge.svg)
---

## Project Overview

This project demonstrates end-to-end test automation for a cloud storage service that manages data
across hot, warm, and cold storage tiers. The framework is structured across three test categories
with supporting documentation for test strategy and defect reporting.


## What This Project Demonstrates

Risk-based test strategy with three-tier coverage (functional, performance, fault injection)
FastAPI service testing using httpx async client with pytest fixtures
Performance benchmarking with latency thresholds and throughput assertions
Fault injection patterns simulating network failures and storage layer errors
GitHub Actions CI pipeline with automated coverage reporting
---

## Project Structure

```
cloud-storage-test-framework/
├── src/
│   └── storage_service.py          # FastAPI storage service implementation
├── tests/
│   ├── conftest.py                 # Shared fixtures across all test modules
│   ├── functional/
│   │   ├── test_file_operations.py # File upload, download, delete tests
│   │   ├── test_stats.py           # Storage stats & metadata validation
│   │   └── test_tiering.py         # Hot/warm/cold tiering logic tests
│   ├── performance/
│   │   └── test_performance.py     # Latency & throughput benchmarks
│   └── fault_injection/
│       └── test_fault_injection.py # Resilience under simulated failures
├── docs/
│   ├── TEST_STRATEGY.md            # Risk-based prioritisation & coverage rationale
│   └── BUGS_AND_IMPROVEMENTS.md   # Defect reports with reproduction steps
├── .github/workflows/              # GitHub Actions CI/CD pipeline
├── requirements.txt
└── README.md
```

## Test Coverage (38 Tests)

| Category | Files | What's Tested |
|---|---|---|
| Functional | test_file_operations.py, test_tiering.py, test_stats.py | API correctness, tiering logic, data integrity, storage stats |
| Performance | test_performance.py | Latency thresholds under load, throughput benchmarks |
| Fault Injection | test_fault_injection.py | System resilience, failure recovery behaviour |

---

## Running Tests

**Setup:**
```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

**Run all tests:**
```bash
pytest tests/
```

**Run by category:**
```bash
pytest tests/functional/
pytest tests/performance/
pytest tests/fault_injection/
```

**Run with coverage report:**
```bash
pytest tests/ --cov=src --cov-report=term-missing
```

---

## CI/CD

GitHub Actions pipeline auto-triggers the full test suite on every push.  
See `.github/workflows/`.

---

## Documentation

- `docs/TEST_STRATEGY.md` — test scope, risk-based prioritisation, coverage decisions  
- `docs/BUGS_AND_IMPROVEMENTS.md` — bugs found during testing with reproduction steps and improvement recommendations