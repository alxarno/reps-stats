# reps-stats

## Usage

```yml
name: Member Contribution Report

on:
  schedule:
    # Runs on the first day of the month at 00:00 UTC
    #
    #        ┌────────────── minute
    #        │ ┌──────────── hour
    #        │ │ ┌────────── day (month)
    #        │ │ │ ┌──────── month
    #        │ │ │ │ ┌────── day (week)
    - cron: "0 0 1 * *"

jobs:
  member-contribution-report:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v2

      - name: Get Member Contributions
        uses: alxarno/reps-stats@0.0.4
        with:
          token: ${{ secrets.ORG_TOKEN }}
          days: 1
          stale: 14
          old: 120
          org-name: "1712n"
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-s3-bucket: "nterminal-lite"
          aws-s3-path: "debug/github-statistics"
```
