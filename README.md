# Discourse Bulk User Creator

Create many Discourse users from an Excel workbook.

## What changed
- No hardcoded secrets in code
- Uses CLI args and environment variables
- Validates required columns before running
- Writes per-row status, response, user id, and notes back to the sheet
- Supports `--dry-run` to validate safely before API calls
- Generates a strong password when the `password` cell is empty

## Files
- `users.py`: bulk creation script
- `users.xlsx`: input template
- `requirements.txt`: dependencies

## Requirements
- Python 3.9+
- Discourse admin API key
- Access to `https://<your-discourse-site>`

## Install
```bash
python -m venv .venv
. .venv/Scripts/activate  # Windows PowerShell: .\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

## Configure
Set environment variables (recommended):

```powershell
$env:DISCOURSE_SITE_URL="https://community.example.com"
$env:DISCOURSE_API_KEY="your_api_key"
$env:DISCOURSE_API_USERNAME="admin_username"
```

Or pass these with CLI flags.

## Excel format (`users.xlsx`)
Row 1 must include these columns:
- `username` (required)
- `email` (required)
- `name` (required)
- `password` (optional)

Output columns are auto-managed by the script:
- `User Status`
- `API Response`
- `User ID`
- `Notes`

If `password` is blank, the script generates a temporary strong password.

## Usage
Dry run first:

```bash
python users.py --file users.xlsx --dry-run
```

Create users:

```bash
python users.py --file users.xlsx --active --approved --suppress-welcome-message
```

You can override config directly:

```bash
python users.py --file users.xlsx --site-url https://community.example.com --api-key <key> --api-username <admin>
```

## Notes
- Rows with an existing `User ID` are skipped.
- Rows missing required fields are marked `Invalid row`.
- Results are written back into the same workbook.