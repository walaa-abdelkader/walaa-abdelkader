name: Generate Snake

on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch:

permissions:
  contents: write

jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - uses: Platane/snk@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-snake-dark.svg?color_snake=C7A9D0&color_dots=#161b22,#4a3a5c,#6b4f8a,#8e6fb0,#C7A9D0

      - uses: crazy-max/github-pages-deploy-action@v4
        with:
          branch: output
          folder: dist
