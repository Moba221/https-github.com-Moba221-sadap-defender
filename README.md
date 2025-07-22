# https-github.com-Moba221-sadap-defender
Bisa install langsung lewat Termux  Auto-update kalau kamu edit file .sh di repo
🧱 Struktur Folder Repo-nya:

sadap-defender/
│
├── install-sadap.sh         ✅ Installer utama
├── antiSadap/               📁 Tools folder
│   ├── sadapScan.sh
│   ├── monitorSadap.sh
│   └── menu-defender.sh
└── .github/
    └── workflows/
        └── auto-update.yml  ⚙️ GitHub Action

        🔧 Langkah Lengkap Upload & Setup

🔹 1. Buat folder lokal:

mkdir sadap-defender
cd sadap-defender

🔹 2. Salin semua script kamu:

mkdir antiSadap
cd antiSadap
nano sadapScan.sh     # paste isi script sadapScan
nano monitorSadap.sh  # paste isi monitor script
nano menu-defender.sh # paste menu script
cd ..
nano install-sadap.sh # paste script installer

🔹 3. Tambahkan GitHub Action

mkdir -p .github/workflows
nano .github/workflows/auto-update.yml

Isi file:

name: Auto Update Installer

on:
  push:
    branches:
      - main
    paths:
      - '**.sh'

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout Repository
      uses: actions/checkout@v3

    - name: Compress Tools Folder
      run: tar -czvf sadap-defender.tar.gz antiSadap/

    - name: Upload Artifact
      uses: actions/upload-artifact@v4
      with:
        name: sadap-defender
        path: sadap-defender.tar.gz

        🔹 4. Upload ke GitHub

git init
git remote add origin https://github.com/Moba221/sadap-defender.git
git add .
git commit -m "Initial upload sadap defender"
git branch -M main
git push -u origin main

✅ Setelah Itu...

Kamu bisa langsung install dari Termux siapa pun pakai:

