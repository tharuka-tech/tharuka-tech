<div align="center">
  <img height="150" src="https://media2.giphy.com/media/l41lGnxllmN3YqOyI/giphy.webp?cid=790b7611387guzq783xq2run8gcgqfhd1wk91oxxpj8hl3c5&ep=v1_gifs_search&rid=giphy.webp&ct=g"  />
</div>

###

<div align="center">
  <a href="www.linkedin.com/in/tharuka-dilshan-27794a296" target="_blank">
    <img src="https://img.shields.io/static/v1?message=LinkedIn&logo=linkedin&label=&color=0077B5&logoColor=white&labelColor=&style=for-the-badge" height="25" alt="linkedin logo"  />
  </a>
  <a href=" www.youtube.com/@tharuz-yt" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Youtube&logo=youtube&label=&color=FF0000&logoColor=white&labelColor=&style=for-the-badge" height="25" alt="youtube logo"  />
  </a>
  <img src="https://img.shields.io/static/v1?message=Twitter&logo=twitter&label=&color=1DA1F2&logoColor=white&labelColor=&style=for-the-badge" height="25" alt="twitter logo"  />
</div>

###

<h1 align="center">hey there 👋 I'm Tharuka</h1>

###

<h3 align="left">👩‍💻  About Me</h3>

###

<p align="left">Welcome to My GitHub Profile!<br><br>- 🔭 I'm an undergraduate Software Engineering student<br>- 📚 I also follow Japanese and enjoy integrating language learning into my project<br>- ⚡  Feel free to reach out to me for collaboration or just to chat about tech!</p>

###

<img src="https://raw.githubusercontent.com/tharuka-tech/tharuka-tech/output/snake.svg" alt="Snake animation" />

###

name: Generate snake animation

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"

  workflow_dispatch:

  push:
    branches:
    - master

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: generate snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: dist/snake.svg?palette=github-dark


      - name: push snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
