---
author: Colin A. Gross
title: BRAVO 2021
date: 2021-09-13
---

# Current State: API
Up to date & operational

## ✓ Dependency Updates
- marshmallow 
- pymongo
- pysam

## ✓ Refactor Framework Code

Explicit calls to web arg parsing
```python
@bp.route('/coverage', methods = ['GET'])
def get_coverage():
    arguments = {
       'chrom': fields.Str(required = True, validate ... ),
       'start': fields.Int(required = True, validate ...), }
    args = parser.parse(arguments,
    validate = partial(validate_coverage_http_request_args ...```
```

Framework decorator
```python
cov_argmap = {
    'chrom': fields.Str(required = True, validate ...),
    'start': fields.Int(required = True, validate ...), }

@bp.route('/coverage', methods=['GET'])
@use_args(cov_argmap, location='query', validate=validate_paging_args)
def get_coverage(args):
```

## ✓ Package
Allows for editable install to avoid local ENV complications.
```sh
python -m pip install -e .[dev,test]
```

Actual test tooling to separate integration & unit tests.
```ini
[pytest]
testpaths =
    tests
mongodb_fixture_dir = 
    tests/mongo_fixtures
markers =
    integration: using actual data or actual mongodb. (run using --integration)
    default: applied by top level conftest.py to otherwise unmarked tests.
```

## ✓ Define I/O Data
Mongo fixtures `tests/fixtures/genes.json`
```json
    "chrom": "5",
    "start": 10736171,
    "xstart": { "$numberLong": "5010736171" },
```

Endpoint expectations defined tests.
```python
GENE_RESULT = [
  {'chrom': '11', 'full_gene_name': 'hemoglobin subunit beta pseudogene 1',
    'gene_id': 'ENSG00000229988', 'gene_name': 'HBBP1')
```
