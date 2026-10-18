# 🗺️ Windows Project Structure Generator

Un micro-utilitaire d'automatisation léger pour Windows (`.bat`) qui permet de cartographier instantanément l'arborescence complète de n'importe quel dossier de projet et de générer un rapport au format texte épuré.

Idéal pour documenter rapidement vos dépôts GitHub ou enrichir vos fichiers `README.md` sans dépendance externe.

---

## 🚀 Fonctionnalités

- **Zéro Dépendance :** Fonctionne de manière 100% autonome grâce aux outils natifs de Windows et à une commande PowerShell masquée.
- **Détection Dynamique :** Identifie automatiquement le nom du dossier racine actuel pour l'afficher en tête de l'arborescence (évite le point brut `.` par défaut de la commande `tree`).
- **Rapport Isolé :** Crée un répertoire de rapport dédié et nettoie instantanément ses fichiers système temporaires pour laisser votre espace de travail impeccable.

---

## 📁 Rendu Visuel Obtenu

Le script génère un dossier `Infos/` contenant un fichier `structure.txt` structuré comme ceci :

```text
C:.\Mon_Super_Projet
|   .gitignore
|   index.html
|   README.md
|
+---Assets
│       logo.png
│
+---JavaScript
│       main.js
│
\---Style
        style.css
```

---

## 🛠️ Comment l'utiliser ?

1. Téléchargez le fichier `generate_structure.bat`.
2. Placez le fichier à la **racine** du dossier que vous souhaitez cartographier.
3. Double-cliquez sur `generate_structure.bat`.

Le terminal va s'ouvrir brièvement et créer instantanément un sous-dossier contenant l'arborescence finale :

```text
Infos/
└── structure.txt
```

Vous n'avez plus qu'à copier-coller ce texte directement dans la section correspondante de votre documentation !

---

## 🖥️ Aperçu du Code Source

Développé dans un esprit de performance et de légèreté :

```batch
@echo off
echo Generation de la structure du projet...

if not exist Infos mkdir Infos

tree /F /A > Infos\structure_temp.txt

powershell -NoProfile -Command "\$nomProjet = Split-Path '%CD%' -Leaf; (Get-Content 'Infos\structure_temp.txt') -replace '^C:\.\(', ('C:.\' +\)nomProjet) | Set-Content 'Infos\structure.txt'"

del Infos\structure_temp.txt

echo Structure mise a jour !
pause
```

---

## 👤 À propos de l'Auteur

Ce micro-utilitaire a été développé avec passion par **Ki->ir->rA**, développeur indépendant spécialisé dans la création d'outils d'automatisation légers et d'interfaces web dynamiques.

Si vous aimez ce script ou que vous l'utilisez dans vos projets, n'hésitez pas à laisser une ⭐️ sur ce dépôt pour soutenir le projet !

- **GitHub :** [@Sylvain-G404](https://github.com/Sylvain-G404)
- **Portfolio :** [Mon-Portfolio-Temps](https://sylvain-g404.github.io/Mon-Portfolio-Temps/)

_« Une arborescence propre pour un code lisible. »_
