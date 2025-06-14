name: Alertes Paris Sportifs
on:
  schedule:
    - cron: "0 18 * * *"  # Exécution tous les jours à 18h UTC
  workflow_dispatch:  # Permet de lancer manuellement

jobs:
  analyse:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout du code
        uses: actions/checkout@v4

      - name: Installer Python et les dépendances
        run: |
          python -m pip install --upgrade pip
          pip install requests pandas python-telegram-bot

      - name: Lancer le script
        run: python alertes_paris.py
