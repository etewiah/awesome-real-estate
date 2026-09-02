# Contribution Guidelines

We welcome contributions to this list. 

## Table of Contents

- [Adding to this list](#adding-to-this-list)
- [Updating your Pull Request](#updating-your-pull-request)

## Adding to this list

If you have something awesome to contribute to this list, this is how you do it.

You'll need a [GitHub account](https://github.com/join)!

1. Click on the `readme.md` file: 
2. Now click on the edit icon. 
3. You can start editing the text of the file in the in-browser editor. Make sure you follow guidelines above. You can use [GitHub Flavored Markdown](https://help.github.com/articles/github-flavored-markdown/). 
4. Say why you're proposing the changes, and then click on "Propose file change". ![Step 4 - Propose Changes](https://cloud.githubusercontent.com/assets/170270/9402937/7dd0652a-480c-11e5-9138-bd14244593d5.png)
6. Submit the [pull request](https://help.github.com/articles/using-pull-requests/)!

## Before you submit

A few things that keep the list useful and get your PR merged faster:

- **Meet the curation bar** — this is a selective list, not a directory. Submit only resources you would personally recommend to a real-estate practitioner. We do not accept generic AI wrappers, thin tools, SEO or lead-generation sites, or projects that cannot demonstrate meaningful usefulness beyond their own marketing copy.
- **Show why it belongs** — explain the concrete real-estate problem it solves, what makes it meaningfully different from entries already listed, and provide evidence of active maintenance or real-world use. Useful evidence includes public documentation, a changelog, a source repository, customer references, reputable coverage, or other independently verifiable material. A live landing page alone is insufficient.
- **Check the link is live** — not a parked domain, a 404, or something that only works after signing up.
- **Check it isn't already listed** — search the README for the domain or name first.
- **One line, ending with a period**, and don't just repeat the resource's name (e.g. avoid "RISMedia is a reputable source...").
- **Put it in the right region, then the right category.** The list is organized by region first (`## North America`, `## Europe`, ...), then by category within that region (`### CRMs`, `### APIs`, ...). If the resource is tied to a specific country or market (its data, coverage, or regulations only apply there), file it under that region. If it's genuinely usable regardless of market — most generic SaaS, CRMs, meta-lists — it goes under `## Global`. If the right region or category doesn't exist yet, propose one.
- **Disclose affiliation.** If you built or work on what you're submitting, that's welcome — just say so in the PR.

Submissions that do not meet these requirements may be closed without an extended review.

CI runs [`awesome-lint`](https://github.com/sindresorhus/awesome-lint) and a link checker on every PR, and will flag most formatting issues automatically. If the Table of Contents check fails, run `npx doctoc --github --title "## Contents" README.md` locally and commit the result.

## Updating your Pull Request

Sometimes, you may be asked to edit your Pull Request before it is included. [GitHub's guide to changing a commit message](https://docs.github.com/en/pull-requests/committing-changes-to-your-project/creating-and-editing-commits/changing-a-commit-message) explains how to amend a commit before updating your Pull Request.
