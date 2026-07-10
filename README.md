# Grants
Grant application assessment
A self-contained tool that extracts requirements, assessment criteria for downstreams to review, score, evaluate and report on grant submissions
The tool is intended as a test to understand potential and limitations of AI builds

## Deployment (Netlify + GitHub Actions)

This repository publishes the static harness located in the `harness/` directory to Netlify. A GitHub Actions workflow (`.github/workflows/deploy-netlify.yml`) will run on pushes to `main` and deploy the site automatically.

Setup steps:

1. Create a Netlify site (one-time) and note the **Site ID**. Generate a personal access token from Netlify (User settings → Applications → Personal access tokens).
2. Add the following GitHub repository secrets: `NETLIFY_AUTH_TOKEN` (the token) and `NETLIFY_SITE_ID` (the site id).
	- Using the GitHub CLI, for example:

```bash
gh secret set NETLIFY_AUTH_TOKEN --body "<your-token>" --repo OWNER/REPO
gh secret set NETLIFY_SITE_ID --body "<your-site-id>" --repo OWNER/REPO
```

3. Push changes to `main`. The Actions workflow will deploy the contents of the `harness/` directory to the configured Netlify site.

Local smoke test:

```bash
python3 -m http.server 8000 --directory harness
# open http://localhost:8000 to verify the harness pages render locally
```

If you prefer Netlify's native Git integration, you can instead connect this repository in the Netlify dashboard and set the publish directory to `harness` (or leave `netlify.toml` which already sets `publish = "harness"`).

### Adding GitHub repository secrets via UI

1. Go to your repository on GitHub → Settings → Secrets and variables → Actions → New repository secret.
2. Add `NETLIFY_AUTH_TOKEN` with the token value and `NETLIFY_SITE_ID` with the site id.

Once the secrets are set, push to `main` to trigger the workflow.

