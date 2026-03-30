name: 📰 Latest Activity Feed

on:
  schedule:
    - cron: "0 6 * * *"   # runs every day at 6 AM UTC
  workflow_dispatch:

jobs:
  update-readme:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Fetch latest GitHub activity
        uses: jamesgeorge007/github-activity-readme@master
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          COMMIT_MSG: "⚡ Update activity feed"
          MAX_LINES: 6

# ─────────────────────────────────────────────────────────────
# SETUP: Add this to your README.md where you want activity:
#
# <!--START_SECTION:activity-->
# <!--END_SECTION:activity-->
#
# This auto-populates with your 6 most recent GitHub events:
# pushes, PRs, issues opened, stars given, etc.
# No secrets needed — uses built-in GITHUB_TOKEN.
# ─────────────────────────────────────────────────────────────
