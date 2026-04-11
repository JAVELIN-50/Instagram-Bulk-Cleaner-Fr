# 🧹 Instagram Cleaner — Scripts de nettoyage en masse

Scripts JavaScript à lancer directement dans la console du navigateur pour supprimer en masse tes **commentaires** et tes **likes** sur Instagram.

> ⚠️ **Les suppressions sont irréversibles. Lis tout avant de lancer.**

---

## 📁 Fichiers

| Fichier | Description |
|---|---|
| `instagram_comment_deleter_fr.js` | Supprime tous tes commentaires en masse |
| `instagram_unlike_fr.js` | Retire tous tes likes en masse |

---

## ✅ Prérequis

- Un **ordinateur** (PC ou Mac) — ne fonctionne pas sur mobile
- Le navigateur **Chrome**, Edge ou Brave (recommandé)
- Être connecté à **instagram.com** dans ce navigateur

---

## 🗑️ Script 1 — Supprimer ses commentaires

### Étape 1 — Ouvre la bonne page

Va sur cette URL exacte dans ton navigateur :

```
https://www.instagram.com/your_activity/interactions/comments
```

Tu dois voir la liste de tous tes commentaires.

### Étape 2 — Ouvre la console développeur

Appuie sur **F12** (ou clic droit sur la page → "Inspecter"), puis clique sur l'onglet **Console**.

### Étape 3 — Colle le script

Ouvre le fichier `instagram_comment_deleter_fr.js`, copie **tout** le contenu, colle-le dans la console et appuie sur **Entrée**.

### Étape 4 — Laisse tourner

Le script tourne tout seul. Dans la console tu verras :

```
▶ Cliqué sur Sélectionner
✅ Sélection de 15 commentaire(s) dans ce lot.
▶ Cliqué sur Supprimer (bas de page).
🗑 Confirmation de suppression dans la popup.
⏳ Attente de 12s avant le prochain lot...
👀 Cercles visibles après suppression : 12
```

Il supprime **15 commentaires toutes les 12 secondes** environ.

### Étape 5 — Arrêter le script

Pour stopper à tout moment, tape dans la console :

```javascript
stopAuto = true
```

Pour relancer après un arrêt :

```javascript
stopAuto = false; deleteLoop();
```

---

## 💔 Script 2 — Retirer ses likes

### Étape 1 — Ouvre la bonne page

Va sur cette URL exacte :

```
https://www.instagram.com/your_activity/interactions/likes
```

Tu dois voir la grille de tous les posts que tu as aimés.

### Étape 2 — Ouvre la console développeur

Appuie sur **F12**, puis clique sur l'onglet **Console**.

### Étape 3 — Colle le script

Ouvre le fichier `instagram_unlike_fr.js`, copie **tout** le contenu, colle-le dans la console et appuie sur **Entrée**.

### Étape 4 — Laisse tourner

Dans la console tu verras :

```
▶ Cliqué sur Sélectionner
✅ Sélection de 15 like(s) dans ce lot.
▶ Cliqué sur 'Je n'aime plus' (bas de page).
💔 Confirmation dans la popup.
⏳ Attente de 12s avant le prochain lot...
👀 Cases visibles restantes : 10
```

### Étape 5 — Arrêter le script

```javascript
stopAuto = true
```

Pour relancer :

```javascript
stopAuto = false; unlikeLoop();
```

---

## ⚙️ Paramètres personnalisables

En haut de chaque script tu peux modifier ces valeurs :

```javascript
const WAIT_AFTER_DELETE = 12000;    // Délai entre chaque lot (ms) — augmente si Instagram ralentit
const BATCH_SIZE = 15;              // Nombre d'éléments supprimés par lot
const TIME_BETWEEN_SELECTIONS = 150; // Délai entre chaque sélection (ms)
const MAX_POPUP_WAIT = 5000;        // Temps max pour attendre la popup de confirmation (ms)
```

---

## 💡 Tips & astuces

**Le script s'arrête tout seul après un lot ?**
C'est normal si Instagram rate-limite ton compte. Attends 1-2 minutes et relance avec :
```javascript
stopAuto = false; deleteLoop(); // ou unlikeLoop()
```

**Le script tourne mais rien ne se supprime ?**
Instagram a peut-être mis un blocage temporaire sur ton compte. Arrête tout, attends 30 minutes, et relance.

**Accélérer le processus**
Réduis le zoom de la page à **25%** avec `Ctrl` + `-` — cela charge plus d'éléments visibles à l'écran en même temps, donc plus d'éléments sélectionnés par lot.

**Connexion lente ?**
Augmente `WAIT_AFTER_DELETE` ou `WAIT_AFTER_UNLIKE` à `15000` ou `20000` pour laisser plus de temps à Instagram de se rafraîchir entre chaque lot.

**Ne ferme pas la fenêtre**
Le script tourne dans ton navigateur. Si tu fermes l'onglet ou la fenêtre, il s'arrête.

**Garde un œil sur la console**
Les messages en console te disent exactement ce qui se passe. Si tu vois une erreur répétée, arrête le script et signale-le.

**Instagram change souvent son interface**
Si le script casse après une mise à jour d'Instagram, les sélecteurs CSS peuvent ne plus fonctionner. C'est le seul vrai risque technique — il faudra mettre à jour le script.

---

## 🔒 Sécurité & vie privée

- Les scripts tournent **100% localement** dans ton navigateur
- Aucune donnée n'est envoyée à un serveur externe
- Aucun mot de passe n'est lu ou transmis
- Le code est lisible et court — tu peux tout vérifier toi-même avant de lancer

---

## ⚠️ Avertissements

- Les suppressions sont **définitives** — pas de corbeille, pas de retour en arrière
- Instagram peut détecter une activité automatisée et **bloquer temporairement** certaines actions sur ton compte (rarement permanent)
- Utilise ces scripts de manière raisonnée — ne lance pas des milliers de suppressions d'un coup sans pauses

---

## 🐛 Dépannage

| Problème | Solution |
|---|---|
| `rray is not defined` | Le `A` de `Array` a été coupé au copier-coller. Retape le `A` manuellement au début. |
| `Bouton introuvable` | Instagram a peut-être changé son interface. Attends une mise à jour du script. |
| Rien ne se passe | Vérifie que tu es bien sur la bonne URL (`/comments` ou `/likes`) |
| Le script se relance en boucle sans rien faire | Rafraîchis la page et relance le script |
| Erreur de syntaxe | Assure-toi de copier **tout** le script, du début à la fin |
