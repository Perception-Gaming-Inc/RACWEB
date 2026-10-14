# RACPHIL website

This repository contains the static website for RACPHIL, built with HTML, CSS, JavaScript, and local image/font assets. The site presents RACPHIL's trading and business solutions.

## Project files

- `index.html` — website content and page structure
- `style.css` — site-specific styles
- `assets/` — stylesheets, scripts, fonts, and images used by the site
- `CNAME` — custom domain configuration for the published site

## Preview locally

Open `index.html` in a browser, or serve the repository root with any local static-file server. No build step or dependency installation is currently required.

## Making changes

1. Create a topic branch; do not commit directly to the protected default branch.
2. Make and review the change locally in a browser, including desktop and mobile layouts where relevant.
3. Open a pull request, explain the change, and include screenshots for visible design changes.
4. Merge only after the required review and any configured checks pass.

Do not add credentials, private contact lists, unpublished business material, customer/vendor information, or other non-public data to this repository. Review images and documents for embedded personal or confidential information before adding them.

## Access and change control

Repository access should be granted through organization-managed GitHub teams using the least-privilege role needed. Contact the repository owner through the organization's approved internal channel to request access or report an access change; do not post access requests or personnel details in public issues.

The repository owner and an administrator should verify team membership, repository roles, default-branch protection, and publishing/deployment access in GitHub. The governance guide has the recommended role boundaries and a setup checklist. These controls must be configured and tested in GitHub; documentation alone does not enforce them.

## Security and governance

This is a public-facing website repository. Treat content committed here as potentially public, even if repository visibility or deployment settings change. Do not assume that GitHub permissions, branch protection, or deployment access have been configured just because they are described in documentation; verify those settings in GitHub.

- [AI and Data Usage Policy](docs/AI-AND-DATA-USAGE-POLICY.md) — concise rules for handling data in AI tools.
- [Security and GitHub Governance](docs/SECURITY-GOVERNANCE.md) — data classification, repository safeguards, and GitHub configuration checklist.

Report suspected credential exposure or an accidental data disclosure promptly to the organization's security or repository owner. Revoke exposed credentials first; deleting a file or commit does not remove it from Git history or copies.
