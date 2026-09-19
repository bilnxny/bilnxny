name: Generate Snake

on:
  schedule:
    - cron: "0 */12 * * *"
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: Platane/snk/svg-only@v3
        with:
          github_user_name: bilnxny
          outputs: |
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark&color_snake=00FF41&color_dots=000000,003300,006600,00CC00,00FF41
      - uses: crazy-max/ghaction-github-pages@v3
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
