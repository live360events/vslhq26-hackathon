# Setting Up Your GitHub Repo for the VSLive! Redmond 2026 Hackathon

Welcome, hackers. This guide walks you through everything you need to get a GitHub-hosted project ready before the event starts, plus how to give the moderators (Brian Randell and Phil Japikse) access so we can evaluate your work.

Assumed knowledge: you know Git basics (clone, commit, branch, push, pull). If you need a refresher, the [Pro Git book](https://git-scm.com/book/en/v2) is free and excellent.

## Moderator GitHub Handles

Updated July 29, 2026

- `brianrandell` (Brian A. Randell)
- `skimedic` (Philip Japikse)
- `AllenConway` (Allen Conway)
- `ericdboyd` (Eric D. Boyd)
- `TonyChampion` (Tony Champion)

---

## 1. Create a Free GitHub Account

If you already have a personal GitHub account, skip to Section 2.

### Steps

1. Go to [github.com/signup](https://github.com/signup).
2. Enter your email, choose a password, and pick a username. Your username becomes part of every URL you share, so pick something you'll be happy with in five years.
3. Verify your email address.
4. Enable two-factor authentication (2FA). It's required if you plan to own an organization, and it's a good practice regardless. See [Configuring 2FA](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/configuring-two-factor-authentication).

### What you get on the Free plan

The GitHub Free plan includes:

- Unlimited public and private repositories
- Unlimited collaborators on public and private repos
- 2,000 GitHub Actions minutes per month for private repos (unlimited for public)
- GitHub Copilot Free tier (limited monthly completions and chat requests)
- Dependabot alerts, secret scanning for public repos

Full plan comparison: [GitHub plans documentation](https://docs.github.com/en/get-started/learning-about-github/githubs-plans).

---

## 2. Create a Repository

You can create the repo under your personal account or under an organization. If you're **flying solo**, a personal repo is fine. If you're **on a team**, an organization is strongly recommended (see Section 3).

### Create a personal repo

1. Click the **+** menu in the top-right of GitHub and choose **New repository**.
2. Give it a name following the [naming convention](#5-naming-convention-and-topics) below.
3. Add a short description.
4. Choose **Public** or **Private** (see tradeoffs below).
5. Check **Add a README file**.
6. Add a **.gitignore** template appropriate for your stack (VisualStudio, Node, Python, etc.).
7. Optionally choose a **license** (MIT is a common permissive default). Note that you retain all IP per the hackathon rules regardless of license choice.
8. Click **Create repository**.

Reference: [Creating a new repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository).

### Public vs. private tradeoffs

| | Public | Private |
| --- | --- | --- |
| Anyone can view the code | Yes | No |
| Anyone can fork | Yes | No |
| Moderator access setup | None needed (just share URL) | Requires adding collaborators |
| Risk during the event | Other teams could see your approach | None |
| GitHub Actions minutes | Unlimited | 2,000/month on Free |

Most hackathon projects are fine as public repos and become part of your portfolio. Choose private only if you have a specific reason.

---

## 3. Create an Organization (Recommended for Teams)

Organizations give you real access control, which matters when you have teammates and moderators with different permission levels. The Free tier is enough for the hackathon.

> **Rules of the road:**
>
> - **Team of 2–4:** create exactly **one** organization for the team, and put your repo under it. Don't create separate orgs per person and cross-invite each other. One org, one repo, everyone as an Owner (see below).
> - **Team of one (solo):** skip this section. Use a personal repo per Section 2. Creating an org for yourself adds setup overhead you don't need.

### Create the organization

1. Go to [github.com/organizations/plan](https://github.com/organizations/plan).
2. Choose the **Free** plan.
3. Pick an organization name (this is also the URL slug: `github.com/your-org-name`).
4. Provide a billing email (nothing gets billed on Free).
5. Confirm ownership and complete setup.

Reference: [Creating a new organization from scratch](https://docs.github.com/en/organizations/collaborating-with-groups-in-organizations/creating-a-new-organization-from-scratch).

### Add your teammates

1. Go to your org's **People** tab.
2. Click **Invite member**.
3. Enter each teammate's GitHub username or email.
4. Choose **Member** as the role (you're the **Owner** by default).
5. Send the invitations. Teammates need to accept via email or their GitHub notifications.

Reference: [Inviting users to join your organization](https://docs.github.com/en/organizations/managing-membership-in-your-organization/inviting-users-to-join-your-organization).

### For the hackathon: make everyone an Owner

Organizations have two roles at the org level: **Owner** and **Member**. Owners can do everything (add/remove people, create/delete repos, change settings, delete the org). Members can only do what they're explicitly granted.

For a short-lived hackathon team, **make every teammate an Owner** when you invite them. Reasons:

- No bottleneck if one person needs to add someone, change a repo setting, or grant moderator access
- Redundancy: nobody gets locked out because the sole owner stepped away from the table
- You already trust each other, you're on the same team

To do this: when inviting, choose **Owner** as the role instead of **Member**. To upgrade an existing member: **People** → click their row → **Change role** → **Owner**.

After the event, if you keep the org around, you can dial roles back down.

### Create the team repo

Same steps as a personal repo, but under the org:

1. Go to your org page and click **New repository**.
2. Owner is automatically the org.
3. Follow the same steps as Section 2 (name, description, visibility, README, .gitignore, license).
4. On the org Free plan, private repos support unlimited collaborators.

### Optional: create a Moderators team

If you want a clean, reusable way to grant read-only access to multiple people, create a team:

1. In the org, go to **Teams** → **New team**.
2. Name it something like `moderators`.
3. Add `brianrandell` and `skimedic` as members.
4. Go to your repo → **Settings** → **Collaborators and teams** → **Add teams**.
5. Add the `moderators` team with the **Read** role.

Reference: [Organizing members into teams](https://docs.github.com/en/organizations/organizing-members-into-teams).

---

## 4. Give the Moderators Access

There are three paths depending on how you set up your repo. Pick the one that matches your setup.

### Path A: Public personal repo (simplest)

**No action needed.** Share the repo URL in your hackathon submission form and we'll clone it. Since the repo is public, we can view and pull without being added as collaborators.

**Tradeoff:** Other participants can see your code during the event.

### Path B: Private personal repo (has a caveat)

Personal repositories on GitHub **do not have granular permission roles**. If you add someone as a collaborator, they get **write access**. There is no read-only collaborator role on personal repos.

To add us anyway:

1. Go to your repo → **Settings** → **Collaborators**.
2. Click **Add people**.
3. Enter `brianrandell`, send invite.
4. Enter `skimedic`, send invite.
5. We'll accept via email or GitHub notification.

We won't push to your repo, but be aware the permissions technically allow it. If you want true read-only, use Path C.

Reference: [Inviting collaborators to a personal repository](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-access-to-your-personal-repositories/inviting-collaborators-to-a-personal-repository).

### Path C: Organization repo (recommended for private projects)

Organizations support proper read-only access. Two ways to do it:

#### Option 1: Outside collaborators with Read role

1. Go to your repo → **Settings** → **Collaborators and teams**.
2. Click **Add people**.
3. Enter `brianrandell`, choose the **Read** role, send invite.
4. Enter `skimedic`, choose the **Read** role, send invite.

#### Option 2: Moderators team (see Section 3)

Create a team with the two of us as members and grant the team **Read** access to the repo.

Either option gives us read-only access. We can clone, view issues, view actions, and comment on PRs, but we can't push code.

Reference: [Managing an individual's access to an organization repository](https://docs.github.com/en/organizations/managing-user-access-to-your-organizations-repositories/managing-an-individuals-access-to-an-organization-repository).

### After the event: removing moderator access

Judging wraps and winners are announced Thursday morning. After that, feel free to remove moderator access to your repo or org. We don't need to stay in there. To clean up:

- **Personal repo (Path B):** Repo → **Settings** → **Collaborators** → remove `brianrandell` and `skimedic`.
- **Org repo with outside collaborators (Path C, Option 1):** Repo → **Settings** → **Collaborators and teams** → remove both handles.
- **Org repo with moderators team (Path C, Option 2):** Org → **Teams** → **moderators** → remove members, or remove the team's access to the repo, or delete the team.

If you decide to make a private repo public after the event to share your project, you can do that in **Settings** → **General** → **Danger Zone** → **Change repository visibility**.

---

## 5. Naming Convention and Topics

To make evaluation easier, please follow these conventions.

### Repository name

Use this pattern:

```text
vslhq26-<team-or-handle>
```

Examples:

- `vslhq26-copilot-crushers`
- `vslhq26-jdoe`

### GitHub topics (tags)

On your repo main page, click the gear icon next to **About** and add these topics:

- `vslive-hackathon-2026` (required)
- Your primary category tag (required):
  - `category-azure-openai`
  - `category-copilot-integration`
  - `category-ai-agents`
  - `category-dotnet-business-app`
  - `category-creative-application`
- Your secondary category tag, if you're declaring one, using the same list

Reference: [Classifying your repository with topics](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/classifying-your-repository-with-topics).

---

## 6. README Template

Copy this into your `README.md` and fill it in. A good README makes judging faster and helps other attendees learn from your project after the event.

````markdown
# Project Name

One-sentence description of what your project does.

## Team

- **Team name (or "Solo"):**
- **Members:**
  - Name (@github-handle)
  - Name (@github-handle)

## Category

- **Primary:** Azure OpenAI/LLM app | Copilot integration | AI agent/workflow automation | .NET business app | Creative application
- **Secondary (optional):**

## What it does

Two to four sentences describing the problem you're solving and how your project addresses it.

## Architecture

Brief description of the components and how they connect. A diagram (image, mermaid, or ASCII) is welcome.

## Tech stack

- Languages:
- Frameworks/libraries:
- AI models/services:
- Hosting:

## Getting started

### Prerequisites

- List required SDKs, runtimes, accounts, if any API Keys are needed (but not the value of the key itself)

### Setup

```bash
# Clone the repo
git clone https://github.com/<owner>/<repo>.git
cd <repo>

# Install dependencies
# Configure environment variables (see .env.example)

# Run
```

### Configuration

List the environment variables or config files needed. Do NOT commit secrets. Use `.env.example` to show the shape.

## Demo (required)

- Video file in this repo (preferred): `./demo/demo.mp4` (or similar path)
- Video link (YouTube, Loom, etc.) if not committed to repo:
- Deployed URL (if any):

## Known limitations

Be honest about what doesn't work yet. Judges appreciate this.

## License

MIT (or your choice)
````

---

## 7. Branch Protection and Commit Hygiene

Two days is short, so don't over-engineer your workflow. That said, a few habits will save you from disaster and make your code more evaluable.

### .gitignore

Pick the right template when creating the repo, or grab one from [github/gitignore](https://github.com/github/gitignore). Common ones:

- `VisualStudio` for .NET projects
- `Node` for JavaScript/TypeScript
- `Python` for Python projects

Add anything else your tooling generates (build artifacts, local databases, IDE settings you don't want to share).

**One gotcha for the hackathon:** we prefer you commit your demo video to the repo (see Section 8). Some `.gitignore` templates or copied-from-elsewhere ignore rules exclude video files. Before committing, check that patterns like `*.mp4`, `*.mov`, `*.mkv`, or a `demo/` or `media/` directory are **not** in your `.gitignore`. Run `git check-ignore -v path/to/your/video.mp4` to confirm. If Git is ignoring it, remove or negate the pattern.

### Never commit secrets

Secrets in a public repo can be exploited within minutes. Even in private repos, they end up in your history and become a cleanup nightmare.

- Use environment variables, .NET user secrets, or a secrets manager
- Add `.env`, `appsettings.Development.json`, and similar files to `.gitignore`
- Provide `.env.example` or `appsettings.Example.json` showing the shape without values
- If you leak a secret, [rotate it immediately](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/about-authentication-to-github). Deleting the commit is not enough.

### Secret scanning: what you get on Free

GitHub's native secret scanning coverage depends on repo visibility and plan. Here's the current state (as of mid-2026):

| Repo type | Secret scanning | Push protection |
| --- | --- | --- |
| Public (any plan) | Free, automatic, always on | Free, automatic, always on |
| Private personal repo (Free plan) | Not available | Not available |
| Private org repo (Free or Team plan) | Requires **GitHub Secret Protection** paid add-on ($19/active committer/month) | Requires **GitHub Secret Protection** paid add-on |
| Enterprise Cloud | Included via Secret Protection | Included via Secret Protection |

#### What this means for your hackathon repo

- **Going public?** You get GitHub's full secret scanning and push protection automatically. No configuration required. GitHub will block pushes containing detected credentials and notify partner services (AWS, Azure, Stripe, etc.) if a token from theirs ends up in your history.
- **Going private?** GitHub-native secret scanning won't be there on the Free plan. You need to be extra careful yourself. Options:
  - Add `.env`, `appsettings.Development.json`, `secrets.json`, etc. to `.gitignore` before you ever commit
  - Run a local pre-commit hook like [`gitleaks`](https://github.com/gitleaks/gitleaks) or [`trufflehog`](https://github.com/trufflesecurity/trufflehog) to catch secrets before they leave your machine
  - If you leak a credential, rotate it immediately. Removing the commit is not enough because Git history preserves it.

Reference: [About secret scanning](https://docs.github.com/en/code-security/secret-scanning/about-secret-scanning).

### Dependabot alerts (free everywhere)

Dependabot alerts are free on all repositories including private repos on Free plans. Turn them on:

**Settings** → **Code security** → enable **Dependabot alerts** and **Dependabot security updates**.

Reference: [About Dependabot alerts](https://docs.github.com/en/code-security/dependabot/dependabot-alerts/about-dependabot-alerts).

### Commit messages

Write commits that would help you (or a judge) understand the change in six months. A good format:

```text
Short summary in 50 characters or less

Optional longer explanation of what and why (not how, the code shows how).
Wrap at ~72 characters.
```

The [Pro Git book chapter on commit guidelines](https://git-scm.com/book/en/v2/Distributed-Git-Contributing-to-a-Project#_commit_guidelines) covers this well.

### Branching (optional for solo, recommended for teams)

For a two-day hackathon, a heavyweight branch strategy is overkill. But:

- **Solo:** committing to `main` is fine. Consider a branch when trying something risky.
- **Teams:** use feature branches and merge to `main` via pull requests. It prevents stomping on each other's work and gives you a clean history to show judges.

### Optional: branch protection on `main`

If you're on a team, consider protecting `main`:

1. Repo → **Settings** → **Branches** → **Add branch protection rule**
2. Branch name pattern: `main`
3. Enable **Require a pull request before merging**
4. Optionally require one approval

Reference: [Managing a branch protection rule](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/managing-a-branch-protection-rule).

Skip this if you're solo. It'll just get in your way.

### License compliance for what you pull in

The hackathon rules require all assets and dependencies to be properly licensed. For an AI-focused build, that means checking more than just NuGet or npm packages. A quick checklist:

- **Packages:** look at the license field. Permissive (MIT, Apache 2.0, BSD) is safe. Copyleft (GPL, AGPL) can force your whole project under the same license. Look for `LICENSE` or `LICENSE.md` in the source repo.
- **AI models:** check the model card. Open-weight is not the same as unrestricted. Some Llama, Mistral, and DeepSeek variants have use restrictions (acceptable-use policy, commercial-use limits). Hugging Face lists the license on each model page.
- **Datasets:** many public datasets are research-only or have attribution requirements. Verify before you fine-tune or ship anything.
- **Images, icons, fonts, sounds:** stock sites and free-tier assets often have attribution or non-commercial clauses. Read the license, not the marketing copy.
- **AI-generated code:** GitHub Copilot output is yours to use per Microsoft's terms. Other tools vary. Check.
- **Sample code from blog posts or Stack Overflow:** Stack Overflow contributions are CC BY-SA, which means attribution required. Blog snippets vary.

If you use anything with attribution requirements, add a `NOTICE` or `CREDITS.md` file. If a license conflicts with what you want to do, swap the dependency before you build too much on it.

Reference: [choosealicense.com](https://choosealicense.com/) for picking your own license.

---

## 8. Submitting Your Repo

When the hackathon submission form opens, you'll provide:

- Your repo URL
- Team name and members (with GitHub handles)
- Declared primary category (and optional secondary)
- **Demo video (required)** — recorded and submitted on Night 2 per the event schedule
- Any special instructions to run your project

### Where to put the demo video

**Preferred: commit the video into your repo.** It's not a Git best practice for real projects (binaries in Git aren't great), but for the hackathon it's the easiest thing for judges. One repo, everything in one place. A common pattern:

```text
your-repo/
├── src/
├── README.md
└── demo/
    └── demo.mp4
```

Then reference it in the README's Demo section.

**Format:** MP4 (H.264) is preferred. Keep the file under **100 MB** — that's GitHub's per-file hard limit for non-LFS files. For a 3–5 minute 1080p demo, that's easy to hit. If your recording is bigger, re-encode at a lower bitrate or trim it before committing.

**Before committing, check `.gitignore`** so your video isn't silently excluded (see Section 7).

**Alternative:** if you'd rather host on YouTube or Loom, put the link in your README. Either works, but committed video is what we prefer.

Make sure moderators have access (Section 4) **before** you submit. If we can't view your code, we can't judge it.

---

## Resources

### Official GitHub Docs

- [GitHub Docs home](https://docs.github.com/)
- [Get started with GitHub](https://docs.github.com/en/get-started)
- [Repositories](https://docs.github.com/en/repositories)
- [Organizations](https://docs.github.com/en/organizations)
- [GitHub Skills (interactive tutorials)](https://skills.github.com/)

### Git

- [Pro Git book (free)](https://git-scm.com/book/en/v2)
- [Git reference](https://git-scm.com/docs)

### Security

- [About supply chain security on GitHub](https://docs.github.com/en/code-security/supply-chain-security)
- [Managing your personal access tokens](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)

---

Questions during the event? Find Brian or Phil at the moderator table. Happy hacking.
