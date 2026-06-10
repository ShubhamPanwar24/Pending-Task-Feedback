# SA Owner Pending Feedback - GitHub Only

This version uses only GitHub:

- GitHub Pages hosts the form portal.
- `pending_tasks.json` stores current pending tasks.
- SA Owners submit feedback by opening a pre-filled GitHub Issue.
- GitHub Actions parses the issue and updates `feedback.csv` automatically.

## Important limitations

1. SA Owners must be able to create GitHub Issues in this repository.
2. If the repository is public, Issues and `feedback.csv` may be visible publicly. Use a private repository if data is confidential.
3. This is GitHub-only, so it does not use Netlify, Power Automate, Forms, or SharePoint.

## Setup

1. Create a new GitHub repository.
2. Upload all files/folders from this package to the repository root.
3. Go to repository **Settings > Pages**.
4. Under **Build and deployment**, choose:
   - Source: `Deploy from a branch`
   - Branch: `main`
   - Folder: `/root`
5. Save.
6. Go to **Settings > Actions > General**.
7. Under **Workflow permissions**, select:
   - `Read and write permissions`
8. Save.

Your app link will be:

```text
https://YOUR_USERNAME.github.io/YOUR_REPOSITORY/
```

## Daily admin process

Update `pending_tasks.json` daily with filtered pending tasks.

Required JSON format:

```json
[
  {
    "Cluster ID": "89971278",
    "HHID": "89971278",
    "PMAID": "2425458063",
    "Work Order Number": "03083394",
    "SA Owner": "Prem Verma",
    "Appointment Number": "SA-03619329",
    "Work Type": "Maintenance-Meter Related",
    "Task Status": "Dispatched",
    "Feedback Status": "Pending"
  }
]
```

## SA Owner process

1. Open GitHub Pages link.
2. Select SA Owner name.
3. Fill Reason and By which Date Connect.
4. Click **Submit Feedback to GitHub**.
5. GitHub issue page opens.
6. Click **Submit new issue**.
7. GitHub Action updates `feedback.csv`.

## Final output

Download/open `feedback.csv` from the repository. It has columns:

```text
Cluster ID, HHID, PMAID, Work Order Number, SA Owner, Appointment Number, Reason for Pending, By which Date Connect, Submitted Time
```
