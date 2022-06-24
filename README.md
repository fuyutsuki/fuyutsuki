# Visit https://github.com/lowlighter/metrics/blob/master/action.yml for full reference
name: Metrics
on:
  # Schedule updates (daily)
  schedule:
    - cron: "30 3 * * *"
  # Lines below let you run workflow manually and on each commit
  workflow_dispatch:
  push:
    branches: ["main"]
jobs:
  github-metrics:
    runs-on: ubuntu-latest
    steps:
      - uses: lowlighter/metrics@latest
        with:
          # Your GitHub token
          # The following scopes are required:
          #  - public_access (default scope)
          # The following additional scopes may be required:
          #  - read:org      (for organization related metrics)
          #  - read:user     (for user related data)
          #  - read:packages (for some packages related data)
          #  - repo          (optional, if you want to include private repositories)
          token: ${{ secrets.METRICS_TOKEN }}

          # Options
          user: fuyutsuki
          template: terminal
          base: header, activity, community, repositories, metadata
          config_timezone: Asia/Tokyo
          plugin_achievements: true
          plugin_achievements_display: compact
          plugin_achievements_secrets: true
          plugin_achievements_threshold: C
          plugin_languages: true
          plugin_languages_analysis_timeout: 15
          plugin_languages_categories: markup, programming
          plugin_languages_colors: github
          plugin_languages_limit: 8
          plugin_languages_recent_categories: markup, programming
          plugin_languages_recent_days: 14
          plugin_languages_recent_load: 300
          plugin_languages_sections: most-used
          plugin_languages_threshold: 0%
          plugin_people: true
          plugin_people_limit: 28
          plugin_people_size: 28
          plugin_people_types: followers, following
