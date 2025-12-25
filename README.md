# manage-repo-variable
Set GitHub repository variables in CI workflows.

This action allows you to create or update repository-level variables using the GitHub REST API. It is useful for bootstrapping workflows, preparing environments, or synchronizing configuration during CI.

## Usage

- Inputs:
	- `var_name` (required): Name of the repository variable to create/update.
	- `var_value` (required): Value to set for the variable.
	- `token` (required): GitHub token with permission to manage repository variables.

Example workflow (see `.github/workflows/example-use.yml`):

```
jobs:
  manage-repo-var:
    runs-on: ubuntu-latest
    steps:
      - uses: hegde5/manage-repo-variable@v1
        with:
          variable_name: MY_VAR
          variable_value: "MY_VAL"
          token: ${{ secrets.REPO_VARIABLE_TOKEN }}
```

Where `REPO_VARIABLE_TOKEN` is a fine-grained PAT with: Variables -> Read and write access
