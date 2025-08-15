# Olá, eu sou o Pedro! 👋

💻 Apaixonado por tecnologia e programação  
🚀 Sempre aprendendo algo novo  
🎯 Foco em criar projetos divertidos e úteis

---

## 📊 Minhas estatísticas no GitHub:
![GitHub Stats](https://github-readme-stats.vercel.app/api?username=traag&show_icons=true&theme=radical)
![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=traag&layout=compact&theme=radical)

---

## 🎖️ Badges e Redes:
[![LinkedIn](https://img.shields.io/badge/-LinkedIn-blue?style=for-the-badge&logo=linkedin)](https://www.linkedin.com)
[![Instagram](https://img.shields.io/badge/-Instagram-pink?style=for-the-badge&logo=instagram)](https://instagram.com)

---

name: Generate Snake

on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2

      - name: Generate Snake - Light
        uses: Platane/snk@v3
        with:
          github_user_name: traag
          outputs: dist/github-contribution-grid-snake.svg

      - name: Generate Snake - Dark
        uses: Platane/snk@v3
        with:
          github_user_name: traag
          outputs: dist/github-contribution-grid-snake-dark.svg
          snake_color: "#00ff00"
          background_color: "#000000"

      - name: Push to Output Branch
        uses: crazy-max/ghaction-github-pages@v3
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

