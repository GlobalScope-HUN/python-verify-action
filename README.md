# python-verify-action
Python code quality gate: build, analyze and test python code

## Features

- Check code style with flake8
- Check static typing with mypy
- Run tests with coverage
- Enforce coverage threshold
- Add optional PR comment with coverage summary
- Report coverage percentage

## Inputs

 - `python-version`: Python version to use (default: `3.9`)
 - `coverage-threshold`: Coverage threshold to use (default: `100`)
 - `add-coverage-comment`: Add a comment to the PR with coverage summary (default: `true`)

## Outputs
    
- `coverage`: Coverage percentage

## Example usage
    
```yaml
      - uses: actions/checkout@v4
      - id: quality-gate
        uses: GlobalScope-HUN/python-verify-action@v1
        with:
          python-version: '3.12'
          coverage-threshold: '95'
          add-coverage-comment: 'true'
      - run: echo "Current code coverage is $COVERAGE_PERCENT%"
        shell: bash
        env:
          COVERAGE_PERCENT: ${{ steps.quality-gate.outputs.coverage }}
```
