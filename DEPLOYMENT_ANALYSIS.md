# Deployment Structure and Analysis

```text
ps164-pqc-readiness-scanner/
├── app.py
├── scanner.py
├── repository_scanner.py
├── container_scanner.py
├── unified_inventory.py
├── mosca_engine.py
├── cbom_formatter.py
├── pqc_recommendations.py
├── algorithm_patcher.py
├── requirements.txt
├── .gitignore
├── README.md
├── DEPLOYMENT_ANALYSIS.md
├── scanners/
│   ├── __init__.py
│   ├── source_scanner.py
│   ├── dependency_scanner.py
│   ├── protocol_scanner.py
│   ├── binary_scanner.py
│   ├── config_scanner.py
│   └── certificate_scanner.py
└── data/
    └── crypto_catalog.json
```

## Removed from the deploy package

The supplied ZIP contained many backup app versions, a dated backup directory, local tests, duplicate sample repositories/ZIPs, a Windows batch file, and legacy engine modules that import a missing `core/` package. Those are not required by the current `app.py` runtime import graph.

## Important finding from the previous Streamlit error

The supplied ZIP's current `app.py` imports:

```python
from mosca_engine import (
    derive_asset_context,
    evaluate_asset_risk,
)
```

The supplied `mosca_engine.py` defines both functions.

The Streamlit screenshot you showed earlier displayed an import of:

```python
from mosca_engine import calculate_mosca_risk
```

That function name is not present in the supplied ZIP. This strongly indicates that the deployed Streamlit app was running an older/different GitHub revision than the ZIP you have now.

## Validation performed

- Python compilation of the deploy-time `.py` files: passed.
- Current runtime local-module import graph: required local modules are present.
- The uploaded ZIP was not modified; the deployment package is a cleaned copy.
- Full Streamlit execution could not be run in this environment because external package installation/network access is unavailable here.
