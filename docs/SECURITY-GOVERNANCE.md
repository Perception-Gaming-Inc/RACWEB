# Security and GitHub Governance

- **Status:** Implementation guidance; verify settings in GitHub
- **Applies to:** This repository and repositories adopting this baseline
- **Owner:** Organization-designated repository and security owners

## 1. Data classification

Classify information before storing it in a repository, sending it to a service, or sharing it with an AI tool. Use the strictest applicable legal, contractual, customer, or organizational requirement.

| Classification | Examples | Repository handling | AI-tool handling |
| --- | --- | --- | --- |
| **Public** | Approved website copy, published branding, public documentation | May be committed when approved for publication. Review assets and metadata first. | May be used only with an organization-approved tool and only when otherwise appropriate. |
| **Internal** | Non-public procedures, internal project plans, non-sensitive operational notes | Keep out of public repositories. Store only in an organization-approved private location with access controls. | Use only in an approved work tool when the owner permits it; minimize and redact. |
| **Confidential** | Customer/vendor records, personal data, contracts, non-public pricing, unreleased financial or business information, private source code | Do not commit to this public website repository. Use approved systems with least-privilege access. | Never enter into a general-purpose or unapproved AI tool. Use in a specifically approved workflow only if the data owner and security owner authorize it. |
| **Restricted** | Credentials, private keys, authentication tokens, payment-card/security credentials, highly sensitive personal data, active incident details | Never commit. Use an approved secrets manager or restricted system; do not place secrets in Git history. | Never paste, upload, or connect to an AI tool. |

When uncertain, treat the information as confidential and ask the data owner or security contact. Public availability of a repository does not authorize disclosure of unrelated internal data.

## 2. Repository safeguards

For this public-facing static website:

- Commit only content and assets approved for public release. Check image/document metadata and remove unintended personal or confidential information.
- Never store passwords, API keys, tokens, private keys, or environment-specific credentials in source files, comments, commits, or issues.
- Keep unpublished business data, customer/vendor material, and personal information out of the repository and its issue/PR discussion.
- Review changes before merging. For visible content changes, verify the page in a browser at desktop and mobile sizes.
- If a secret is committed, revoke or rotate it immediately, notify the security/repository owner, and follow incident guidance. Removing it from the latest file does not remove it from Git history, forks, caches, or clones.
- Grant access only to people who need it, review membership regularly, and remove access promptly when it is no longer needed.

## 3. Recommended GitHub team access

Use organization teams rather than granting broad individual access where practical. These are recommended role boundaries; adapt them to the organization's team structure and verify them in repository settings.

| Team purpose | Suggested GitHub role | Intended access |
| --- | --- | --- |
| Readers / stakeholders | **Read** | View and clone the repository; no changes. |
| Content or code contributors | **Write** | Create branches and pull requests; cannot administer repository settings. |
| Repository maintainers | **Maintain** | Manage routine repository work without organization-level administration. |
| Repository administrators | **Admin** | A small, named owner group responsible for settings, access, and incident response. |

Avoid assigning **Admin** broadly. Use **Triage** only where issue and pull-request management without code-write access is useful. Review team membership and effective permissions periodically, and after role changes or departures.

### Access lifecycle

- **Grant:** The repository owner confirms the business need, selects the least-privilege team/role, and grants access through the organization team or repository settings. Use the organization's normal approval process.
- **Change:** When responsibilities change, update team membership and repository permissions promptly; do not leave old and new access in place without a reason and review date.
- **Remove:** On departure or loss of business need, remove organization/team and direct repository access promptly, and review related publishing or deployment access. Follow the organization's offboarding process.
- **Review:** At least monthly for this priority deliverable, compare team membership and effective access with the current approved need. Record reviewer, date, removals, and exceptions in an approved internal tracker, not this public repository.
- **Request:** Ask the repository owner through an approved internal channel. Do not put names, access approvals, or employee details in public issues or commits.

## 4. Default-branch protection checklist

An administrator should configure and verify protection for the actual default branch (currently expected to be `main`; confirm in GitHub):

- Require pull requests before merging; disallow direct pushes for routine work.
- Require at least one approval from an authorized reviewer. For changes with elevated risk, require a second independent reviewer when staffing permits.
- Dismiss stale approvals when new commits are pushed, and require approval of the most recent reviewable push where available.
- Require conversation resolution before merging.
- Require relevant status checks when CI checks exist; do not mark nonexistent checks as required.
- Block force pushes and branch deletion.
- Restrict who can bypass protections; keep bypass rights limited to designated administrators and document any exception.
- Consider requiring signed commits if the organization has key provisioning and support in place.

Use a repository ruleset or branch protection rule according to the organization's GitHub plan and standards. Verify enforcement on the target branch after saving; this document alone does not enable any setting.

### Where to configure and verify

In the repository on GitHub, an administrator should inspect **Settings → Collaborators and teams** for effective team and direct access, and **Settings → Rules → Rulesets** (or **Settings → Branches** for branch protection rules) for default-branch enforcement. GitHub labels can vary by plan and interface version. Also check the repository's **Settings → Environments** and publishing workflow permissions if deployment credentials or production publishing are used.

After saving, verify that the rule targets the actual default branch, required reviews apply, force-push/deletion protections are active, and bypass access is limited. Perform a safe test with a non-admin account or ask an authorized contributor to confirm direct pushes are blocked. Do not test by pushing secrets or sensitive data.

## 5. Monthly verification and evidence

The repository owner should record completion in the organization's approved tracking location (not by adding access lists or private configuration screenshots to this public repository):

- Confirm the default branch and repository visibility.
- Review teams, members, and effective repository roles; confirm least privilege.
- Review direct collaborators as well as team-based access, and confirm former contributors no longer have access.
- Confirm the protection/ruleset is enabled for the default branch and test that a change cannot bypass the required PR flow.
- Confirm applicable status checks still run and are correctly named.
- Review who can publish/deploy and the permissions granted to publishing workflows.
- Review recent changes and published assets for accidental disclosure.
- Record the reviewer, date, and outstanding exceptions in the approved internal system.

## 6. Incident reporting

Report suspected data disclosure, exposed credentials, unauthorized access, or a protection bypass promptly to the organization's security contact and repository owner. Revoke exposed credentials first where possible, preserve relevant incident details according to internal procedures, and do not publish sensitive incident evidence in repository issues or pull requests.

## 7. Adoption checklist

- [ ] Organization approves the classification rules and identifies data owners/security contacts.
- [ ] Organization approves the [AI and Data Usage Policy](AI-AND-DATA-USAGE-POLICY.md), names allowed AI tools, and communicates the policy.
- [ ] Repository owner confirms visibility, default branch, and deployment permissions.
- [ ] Repository owner assigns role-appropriate GitHub teams, reviews direct collaborators, and removes unnecessary access.
- [ ] Repository administrator enables and verifies default-branch protection/rulesets.
- [ ] Repository owner reviews publishing/deployment permissions and workflow access.
- [ ] Repository owner records evidence and exceptions in an approved internal location.
