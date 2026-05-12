# 🛠️ TP 2 — Habillage et interactivité du formulaire CV

> **Durée :** 2h30 (1h CSS + 1h30 JS)
> **Prérequis :** TP 1 terminé (formulaire CV en HTML)
> **Rendu :** dossier compressé `tp2-cv-nom-prenom.zip` à déposer sur l'espace pédagogique

---

## 🎯 Objectif

Reprendre le formulaire CV créé en TP 1 et :

1. L'**habiller** aux couleurs JUNIA avec CSS (Flexbox/Grid, responsive)
2. Le rendre **interactif** avec JavaScript (validation en direct, aperçu dynamique, persistance des données)

À la fin du TP, l'étudiant disposera d'un **formulaire fonctionnel et stylisé** prêt à être branché sur PHP en séance 3.

---

## 📦 Mise en place

```
tp2-cv/
├── index.html          ← votre formulaire du TP 1
├── css/
│   └── style.css       ← à créer
└── js/
    └── form-cv.js      ← à créer
```

Dans `index.html`, ajoutez dans le `<head>` et avant `</body>` :

```html
<head>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <!-- ... votre formulaire ... -->
    <script src="js/form-cv.js"></script>
</body>
```

---

# PARTIE 1 — Habillage CSS (1h)

## Étape 1 — Variables CSS et reset

Dans `css/style.css`, commencez par définir la palette JUNIA et un reset minimal :

```css
:root {
    --junia-violet: #6B2C91;
    --junia-violet-clair: #A569BD;
    --junia-orange: #F39200;
    --junia-orange-clair: #FDB44B;
    --junia-texte: #333333;
    --junia-fond: #FAF7F2;
    --junia-blanc: #FFFFFF;
    --junia-erreur: #E74C3C;
    --junia-succes: #27AE60;
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Open Sans', Arial, sans-serif;
    background: var(--junia-fond);
    color: var(--junia-texte);
    line-height: 1.6;
    padding: 2rem;
}
```

> ☐ **À cocher :** Variables définies, reset appliqué, fond beige clair visible.

---

## Étape 2 — Header avec dégradé JUNIA

```css
header {
    background: linear-gradient(135deg, var(--junia-violet) 0%, var(--junia-orange) 100%);
    color: var(--junia-blanc);
    padding: 3rem 2rem;
    text-align: center;
    border-radius: 12px;
    margin-bottom: 2rem;
    box-shadow: 0 5px 20px rgba(107, 44, 145, 0.2);
}

header h1 {
    font-size: 2.5rem;
    margin-bottom: 0.5rem;
}
```

> ☐ **À cocher :** Header avec dégradé violet → orange visible, titre blanc bien lisible.

---

## Étape 3 — Conteneur principal et structure du formulaire

Le formulaire doit être centré et limité en largeur :

```css
form {
    max-width: 800px;
    margin: 0 auto;
    background: var(--junia-blanc);
    padding: 2rem;
    border-radius: 12px;
    box-shadow: 0 5px 20px rgba(0, 0, 0, 0.08);
}

fieldset {
    border: 2px solid var(--junia-violet);
    border-radius: 8px;
    padding: 1.5rem;
    margin-bottom: 1.5rem;
}

legend {
    color: var(--junia-violet);
    font-weight: bold;
    padding: 0 0.5rem;
}
```

> ☐ **À cocher :** Formulaire centré sur fond blanc, fieldsets bordés en violet.

---

## Étape 4 — Champs de saisie

```css
label {
    display: block;
    margin-top: 1rem;
    margin-bottom: 0.3rem;
    color: var(--junia-violet);
    font-weight: 600;
}

input[type="text"],
input[type="email"],
input[type="date"],
input[type="tel"],
textarea,
select {
    width: 100%;
    padding: 0.75rem;
    border: 2px solid #ddd;
    border-radius: 6px;
    font-size: 1rem;
    font-family: inherit;
    transition: border-color 0.3s, box-shadow 0.3s;
}

input:focus,
textarea:focus,
select:focus {
    outline: none;
    border-color: var(--junia-orange);
    box-shadow: 0 0 0 3px rgba(243, 146, 0, 0.2);
}

textarea {
    min-height: 120px;
    resize: vertical;
}
```

> ☐ **À cocher :** Champs stylisés, halo orange au focus.

---

## Étape 5 — Disposition en grille pour les champs personnels

Utilisez **CSS Grid** pour disposer les champs nom/prénom/email/téléphone sur 2 colonnes :

```css
.champs-perso {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
}

/* Sur mobile, repasser sur une colonne */
@media (max-width: 600px) {
    .champs-perso {
        grid-template-columns: 1fr;
    }
}
```

> ☐ **À cocher :** Champs en 2 colonnes sur desktop, 1 colonne sur mobile.

---

## Étape 6 — Bouton de soumission stylisé

```css
button[type="submit"] {
    background: linear-gradient(135deg, var(--junia-violet), var(--junia-orange));
    color: var(--junia-blanc);
    border: none;
    padding: 1rem 2rem;
    border-radius: 8px;
    font-size: 1.1rem;
    font-weight: bold;
    cursor: pointer;
    transition: transform 0.2s, box-shadow 0.2s;
    margin-top: 1.5rem;
    width: 100%;
}

button[type="submit"]:hover {
    transform: translateY(-2px);
    box-shadow: 0 5px 15px rgba(107, 44, 145, 0.4);
}
```

> ☐ **À cocher :** Bouton avec dégradé, effet de survol fonctionnel.

---

## 🏁 Checkpoint CSS

Vérifiez avant de passer à la suite :

- [ ] Page entièrement aux couleurs JUNIA
- [ ] Header avec dégradé
- [ ] Champs stylisés avec halo au focus
- [ ] Layout responsive (testez en réduisant la fenêtre)
- [ ] Aucune erreur dans la console (F12)

---

# PARTIE 2 — Interactivité JavaScript (1h30)

## Étape 7 — Validation en direct de l'email JUNIA

Dans `js/form-cv.js` :

```js
const champEmail = document.querySelector("#email");
const erreurEmail = document.createElement("span");
erreurEmail.classList.add("erreur");
champEmail.parentElement.appendChild(erreurEmail);

champEmail.addEventListener("input", () => {
    const email = champEmail.value.trim();

    if (email === "") {
        erreurEmail.textContent = "";
        champEmail.classList.remove("invalide", "valide");
    } else if (!email.endsWith("@junia.com")) {
        erreurEmail.textContent = "❌ Utilisez votre adresse @junia.com";
        champEmail.classList.add("invalide");
        champEmail.classList.remove("valide");
    } else {
        erreurEmail.textContent = "✅ Email valide";
        champEmail.classList.add("valide");
        champEmail.classList.remove("invalide");
    }
});
```

CSS associé à ajouter :

```css
.invalide {
    border-color: var(--junia-erreur) !important;
    background-color: #fdf2f2;
}

.valide {
    border-color: var(--junia-succes) !important;
    background-color: #f0faf4;
}

.erreur {
    display: block;
    margin-top: 0.3rem;
    font-size: 0.9rem;
    color: var(--junia-erreur);
}

.valide + .erreur,
.valide ~ .erreur {
    color: var(--junia-succes);
}
```

> ☐ **À cocher :** Saisie d'un email non-JUNIA → message rouge. Email JUNIA → message vert.

---

## Étape 8 — Compteur de caractères pour la lettre de motivation

```js
const champMotivation = document.querySelector("#motivation");
const compteur = document.createElement("small");
compteur.classList.add("compteur");
champMotivation.parentElement.appendChild(compteur);

const MAX_CARACTERES = 500;

const mettreAJourCompteur = () => {
    const longueur = champMotivation.value.length;
    compteur.textContent = `${longueur} / ${MAX_CARACTERES} caractères`;
    compteur.style.color = longueur > 450 ? "var(--junia-orange)" : "var(--junia-violet)";
};

champMotivation.addEventListener("input", mettreAJourCompteur);
mettreAJourCompteur();    // affichage initial
```

> ☐ **À cocher :** Compteur visible et qui se met à jour à chaque frappe.

---

## Étape 9 — Aperçu dynamique du CV

Ajoutez dans le HTML, après le formulaire :

```html
<section id="apercu-cv" class="apercu">
    <h2>Aperçu de votre CV</h2>
    <div id="apercu-contenu"></div>
</section>
```

Puis en JS :

```js
const formulaire = document.querySelector("#form-cv");
const apercuContenu = document.querySelector("#apercu-contenu");

const mettreAJourApercu = () => {
    const donnees = new FormData(formulaire);

    apercuContenu.innerHTML = `
        <h3>${donnees.get("prenom") || "Prénom"} ${donnees.get("nom") || "Nom"}</h3>
        <p>📧 ${donnees.get("email") || "—"}</p>
        <p>📞 ${donnees.get("telephone") || "—"}</p>
        <p>🎂 Né(e) le ${donnees.get("date-naissance") || "—"}</p>
        <h4>Lettre de motivation</h4>
        <p>${donnees.get("motivation") || "—"}</p>
    `;
};

formulaire.addEventListener("input", mettreAJourApercu);
mettreAJourApercu();
```

> ☐ **À cocher :** Aperçu mis à jour en direct quand on remplit le formulaire.

---

## Étape 10 — Persistance avec localStorage

Sauvegardez les données dans le navigateur pour qu'elles soient conservées après un rechargement :

```js
// Sauvegarde à chaque modification
formulaire.addEventListener("input", () => {
    const donnees = {};
    new FormData(formulaire).forEach((valeur, cle) => {
        donnees[cle] = valeur;
    });
    localStorage.setItem("cv-junia", JSON.stringify(donnees));
});

// Rechargement au démarrage
window.addEventListener("DOMContentLoaded", () => {
    const sauvegarde = localStorage.getItem("cv-junia");
    if (!sauvegarde) return;

    const donnees = JSON.parse(sauvegarde);
    for (const [cle, valeur] of Object.entries(donnees)) {
        const champ = formulaire.querySelector(`[name="${cle}"]`);
        if (champ) champ.value = valeur;
    }
    mettreAJourApercu();
});
```

> ☐ **À cocher :** Remplissez quelques champs, rechargez la page (F5) : les données sont toujours là.

---

## Étape 11 — Soumission avec notification

```js
formulaire.addEventListener("submit", (event) => {
    event.preventDefault();

    if (!champEmail.value.endsWith("@junia.com")) {
        alert("⚠️ Merci d'utiliser votre adresse JUNIA.");
        return;
    }

    // Plus tard : envoi vers PHP via fetch
    console.log("✅ CV généré :", Object.fromEntries(new FormData(formulaire)));

    afficherNotification("✅ Votre CV a bien été enregistré !");
    localStorage.removeItem("cv-junia");
    formulaire.reset();
    mettreAJourApercu();
});

const afficherNotification = (message) => {
    const notif = document.createElement("div");
    notif.classList.add("notification");
    notif.textContent = message;
    document.body.appendChild(notif);
    setTimeout(() => notif.remove(), 3000);
};
```

CSS associé :

```css
.notification {
    position: fixed;
    bottom: 20px;
    right: 20px;
    background: var(--junia-orange);
    color: var(--junia-blanc);
    padding: 1rem 1.5rem;
    border-radius: 8px;
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
    z-index: 1000;
    animation: slideIn 0.3s ease;
}

@keyframes slideIn {
    from { transform: translateX(100%); opacity: 0; }
    to { transform: translateX(0); opacity: 1; }
}
```

> ☐ **À cocher :** Soumission du formulaire → notification orange en bas à droite.

---

# 🎁 BONUS (facultatif)

### Bonus 1 — Photo de profil avec aperçu

```html
<input type="file" id="photo" accept="image/*">
<img id="apercu-photo" style="max-width: 150px; display: none;">
```

```js
document.querySelector("#photo").addEventListener("change", (event) => {
    const fichier = event.target.files[0];
    if (!fichier) return;
    const url = URL.createObjectURL(fichier);
    const apercu = document.querySelector("#apercu-photo");
    apercu.src = url;
    apercu.style.display = "block";
});
```

### Bonus 2 — Choix multiples des domaines de recherche avec checkboxes stylisées

Vous pouvez transformer les checkboxes en boutons-pilules cliquables (stage / alternance / CDI / mobilité).

### Bonus 3 — Mode sombre

Ajoutez un toggle qui inverse les couleurs de la page.

---

# 📊 Évaluation

| Critère | Points |
|---------|--------|
| Charte JUNIA respectée (violet/orange, dégradé header) | /3 |
| Layout responsive (Grid + Media Query) | /3 |
| Validation email en direct fonctionnelle | /3 |
| Compteur de caractères fonctionnel | /2 |
| Aperçu dynamique du CV | /3 |
| localStorage opérationnel | /3 |
| Notification de soumission | /2 |
| Bonus | /1 |
| **TOTAL** | **/20** |

---

## 📤 Rendu

Compressez votre dossier `tp2-cv/` en `.zip` (avec le nom : `tp2-cv-nom-prenom.zip`) et déposez-le sur l'espace pédagogique avant la prochaine séance.

> 💡 **Préparation à la séance 3 :** Ce TP pose les fondations qui seront branchées sur PHP : le `fetch` remplacera `localStorage`, et les données seront stockées en base MySQL. Soignez votre code, il vous servira !
