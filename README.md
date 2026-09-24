# NVA Aggregate Repo

This repository aggregates the core [BIBSYSDEV](https://github.com/BIBSYSDEV) repositories that make up the NVA (National Research Archive) system, each included as a git **submodule** under `modules/`.

This repo does not contain any code of its own — it exists to give a single checkout point that references a specific, pinned commit of each component repo. Each submodule remains a fully independent git repository with its own history, branches, and remote.

## Included submodules

| Repo | Path | Source |
|---|---|---|
| nva-publication-api | `modules/nva-publication-api` | https://github.com/BIBSYSDEV/nva-publication-api |
| nva-commons | `modules/nva-commons` | https://github.com/BIBSYSDEV/nva-commons |
| nva-nvi | `modules/nva-nvi` | https://github.com/BIBSYSDEV/nva-nvi |
| nva-publication-channels-java | `modules/nva-publication-channels-java` | https://github.com/BIBSYSDEV/nva-publication-channels-java |
| nva-identity-service | `modules/nva-identity-service` | https://github.com/BIBSYSDEV/nva-identity-service |
| nva-search-api | `modules/nva-search-api` | https://github.com/BIBSYSDEV/nva-search-api |
| nva-person-preferences | `modules/nva-person-preferences` | https://github.com/BIBSYSDEV/nva-person-preferences |
| nva-cristin-service | `modules/nva-cristin-service` | https://github.com/BIBSYSDEV/nva-cristin-service |
| nva-data-report-api | `modules/nva-data-report-api` | https://github.com/BIBSYSDEV/nva-data-report-api |
| nva-doi-registrar-client | `modules/nva-doi-registrar-client` | https://github.com/BIBSYSDEV/nva-doi-registrar-client |
| nva-doi-partner-data | `modules/nva-doi-partner-data` | https://github.com/BIBSYSDEV/nva-doi-partner-data |
| nva-orcid-client | `modules/nva-orcid-client` | https://github.com/BIBSYSDEV/nva-orcid-client |
| nva-monitoring | `modules/nva-monitoring` | https://github.com/BIBSYSDEV/nva-monitoring |
| nva-fetch-doi | `modules/nva-fetch-doi` | https://github.com/BIBSYSDEV/nva-fetch-doi |
| nva-verified-funding-sources | `modules/nva-verified-funding-sources` | https://github.com/BIBSYSDEV/nva-verified-funding-sources |
| nva-language-java | `modules/nva-language-java` | https://github.com/BIBSYSDEV/nva-language-java |
| nva-handle-service | `modules/nva-handle-service` | https://github.com/BIBSYSDEV/nva-handle-service |
| nva-swagger-generator | `modules/nva-swagger-generator` | https://github.com/BIBSYSDEV/nva-swagger-generator |
| NVA-Frontend | `modules/NVA-Frontend` | https://github.com/BIBSYSDEV/NVA-Frontend |
| nva-language | `modules/nva-language` | https://github.com/BIBSYSDEV/nva-language |
| nva-language-js | `modules/nva-language-js` | https://github.com/BIBSYSDEV/nva-language-js |
| nva-github-workflows | `modules/nva-github-workflows` | https://github.com/BIBSYSDEV/nva-github-workflows |
| nva-common-resources | `modules/nva-common-resources` | https://github.com/BIBSYSDEV/nva-common-resources |
| nva-backups | `modules/nva-backups` | https://github.com/BIBSYSDEV/nva-backups |
| nva-api-documentation | `modules/nva-api-documentation` | https://github.com/BIBSYSDEV/nva-api-documentation |
| nva-gradle-template | `modules/nva-gradle-template` | https://github.com/BIBSYSDEV/nva-gradle-template |
| nva-api-integration-test | `modules/nva-api-integration-test` | https://github.com/BIBSYSDEV/nva-api-integration-test |

> **Note:** There is also an `NVA-infrastructure` repo in the BIBSYSDEV org (https://github.com/BIBSYSDEV/NVA-infrastructure), but it is **not included** as a submodule here because it is a private repo.

## Cloning

Clone with all submodules populated in one step:

```bash
git clone --recurse-submodules git@github.com:BIBSYSDEV/nva-as-a-monolith.git
```

If you've already cloned without that flag:

```bash
git submodule update --init --recursive
```

## Access requirements

Cloning the parent repo alone does **not** grant access to the submodules. Each submodule is an independent repo with its own permissions. Whatever credentials (SSH key, PAT, GitHub App installation) are used to run `git submodule update` need read access to **all** repos listed above.

## Updating a submodule to a newer commit

Submodules are pinned to a specific commit, not a branch. To bump one to a newer commit from its source repo:

```bash
cd modules/<repo-name>
git checkout <branch-or-commit>
git pull        # if tracking a branch
cd ../..
git add modules/<repo-name>
git commit -m "Bump <repo-name> to latest"
git push
```

## Bulk operations across all submodules

```bash
# Check status of every submodule (branch/commit each is on)
git submodule status

# Pull the latest commit for every submodule's tracked branch
git submodule foreach 'git pull origin main'
```
