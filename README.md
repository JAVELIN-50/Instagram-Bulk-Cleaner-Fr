# 🧹 Instagram Cleaner — Scripts de nettoyage en masse

Scripts JavaScript à lancer directement dans la console du navigateur pour supprimer en masse tes **commentaires** et tes **likes** sur Instagram, sans aucune application tierce.

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

## 🚀 Utilisation

Les deux scripts fonctionnent exactement de la même façon. La seule différence c'est la page sur laquelle tu dois te rendre et le fichier à copier.

### Étape 1 — Ouvre la bonne page

**Pour les commentaires :**
```
https://www.instagram.com/your_activity/interactions/comments
```

**Pour les likes :**
```
https://www.instagram.com/your_activity/interactions/likes
```

Tu dois voir la liste de tous tes commentaires, ou la grille de tous les posts que tu as aimés.

---

### Étape 2 — Ouvre la console développeur

Appuie sur **F12** (ou clic droit sur la page → "Inspecter"), puis clique sur l'onglet **Console**.

---

### Étape 3 — Colle le bon script

**Pour les commentaires** → copie tout le contenu de `instagram_comment_deleter_fr.js`

**Pour les likes** → copie tout le contenu de `instagram_unlike_fr.js`

Colle le code dans la console et appuie sur **Entrée**.

> ⚠️ Attention au copier-coller : si le premier caractère est coupé (ex: `rray` au lieu de `Array`), retape la lettre manquante manuellement avant de valider.

---

### Étape 4 — Laisse tourner

Le script tourne tout seul. Dans la console tu verras en temps réel ce qui se passe :

**Commentaires :**
```
▶ Cliqué sur Sélectionner
✅ Sélection de 15 commentaire(s) dans ce lot.
▶ Cliqué sur Supprimer (bas de page).
🗑 Confirmation de suppression dans la popup.
⏳ Attente de 12s avant le prochain lot...
👀 Cercles visibles après suppression : 12
```

**Likes :**
```
▶ Cliqué sur Sélectionner
✅ Sélection de 15 like(s) dans ce lot.
▶ Cliqué sur 'Je n'aime plus' (bas de page).
💔 Confirmation dans la popup.
⏳ Attente de 12s avant le prochain lot...
👀 Cases visibles restantes : 10
```

Les scripts traitent **15 éléments toutes les 12 secondes** environ. Ne ferme pas la fenêtre pendant que ça tourne.

---

### Étape 5 — Arrêter / Relancer

Pour stopper à tout moment, tape dans la console :
```javascript
stopAuto = true
```

Pour relancer après un arrêt :
```javascript
// Commentaires
stopAuto = false; deleteLoop();

// Likes
stopAuto = false; unlikeLoop();
```

---

## ⚙️ Paramètres personnalisables

En haut de chaque script tu peux modifier ces valeurs selon ta connexion et ta tolérance au risque :

```javascript
const WAIT_AFTER_DELETE = 12000;     // Délai entre chaque lot en ms (recommandé : 12000-15000)
const BATCH_SIZE = 15;               // Nombre d'éléments traités par lot
const TIME_BETWEEN_SELECTIONS = 150; // Délai entre chaque sélection en ms
const MAX_POPUP_WAIT = 5000;         // Temps max pour attendre la popup de confirmation en ms
```

---

## 💡 Tips & astuces

**Zoomer à 25% pour aller plus vite**
Réduis le zoom de la page à 25% avec `Ctrl` + `-` — cela charge plus d'éléments visibles à l'écran en même temps, donc le script en sélectionne plus par lot.

**Connexion lente ?**
Augmente `WAIT_AFTER_DELETE` à `15000` ou `20000` pour laisser plus de temps à Instagram de rafraîchir la liste entre chaque lot.

**Le script s'arrête après un lot ?**
C'est souvent un rate-limit d'Instagram. Attends 1-2 minutes et relance :
```javascript
stopAuto = false; deleteLoop(); // ou unlikeLoop()
```

**Faire les deux à la suite**
Lance d'abord un script jusqu'à la fin, puis ouvre la deuxième URL et lance le second script. Ne les lance pas en même temps dans deux onglets.

**Garde un œil sur la console**
Les messages te disent exactement ce qui se passe. Si une erreur se répète, arrête le script avec `stopAuto = true` et attends quelques minutes.

**Ne ferme pas la fenêtre**
Le script tourne dans ton navigateur. Si tu fermes l'onglet ou mets l'ordinateur en veille, il s'arrête.

---

## 🔒 Sécurité & vie privée

- Les scripts tournent **100% localement** dans ton navigateur
- Aucune donnée n'est envoyée à un serveur externe
- Aucun mot de passe n'est lu ou transmis
- Le code est court et lisible — tu peux tout vérifier toi-même avant de lancer

---

## ⚠️ Avertissements

- Les suppressions sont **définitives** — pas de corbeille, pas de retour en arrière
- Instagram peut détecter une activité automatisée et **bloquer temporairement** certaines actions sur ton compte (rarement permanent, jamais constaté en utilisation normale)
- Ne lance pas des milliers de suppressions d'un coup sans pauses — les délais intégrés dans les scripts sont là pour ça

---

## 🐛 Dépannage

| Problème | Solution |
|---|---|
| `rray is not defined` | Le `A` de `Array` a été coupé au copier-coller. Retape le `A` manuellement. |
| `Bouton introuvable` | Rafraîchis la page et relance. Si ça persiste, Instagram a peut-être mis à jour son interface. |
| Rien ne se passe au démarrage | Vérifie que tu es bien sur la bonne URL (`/comments` ou `/likes`). |
| Le script tourne mais ne supprime rien | Instagram t'a rate-limité. Arrête tout, attends 30 min, relance. |
| Erreur de syntaxe au collage | Assure-toi de copier le script **en entier**, du début à la fin. |
| La page se rafraîchit toute seule | Normal — Instagram recharge la liste après chaque suppression. Le script gère ça automatiquement. |
