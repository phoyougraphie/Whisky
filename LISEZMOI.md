# Whiskythèque — Mode d'emploi

## Structure des fichiers

```
whiskytheque/
├── index.html        ← L'application (ne pas modifier)
├── whiskies.json     ← Vos données (seul fichier à éditer)
└── LISEZMOI.md       ← Ce fichier
```

## Ajouter des whiskies

Ouvrez `whiskies.json` dans n'importe quel éditeur (VS Code, Notepad++, etc.)
et ajoutez vos entrées en suivant ce modèle exactement :

```json
{
  "id":     "macallan12",        ← Identifiant unique, minuscules, sans espaces
  "name":   "Macallan 12",       ← Nom complet affiché
  "region": "Speyside",          ← Région EXACTE parmi la liste ci-dessous
  "age":    12,                   ← Nombre entier, ou null si pas d'âge affiché
  "price":  65,                   ← Prix entier en euros
  "peat":   5,                    ← Tourbage de 0 (aucun) à 100 (maximal)
  "rich":   85,                   ← Richesse aromatique de 0 à 100
  "comp":   82,                   ← Complexité de 0 à 100
  "sweet":  70,                   ← Douceur de 0 à 100
  "tags":   ["Sherry","Chêne"],   ← 2 à 5 mots-clés aromatiques
  "qp":     2,                    ← Rapport qualité/prix : 1, 2 ou 3
  "note":   "Votre avis caviste." ← Phrase libre, note personnelle
}
```

## Régions disponibles

| Valeur exacte | Couleur sur la carte |
|---------------|---------------------|
| `"Islay"`     | Bleu     |
| `"Speyside"`  | Vert     |
| `"Highlands"` | Orange   |
| `"Irlande"`   | Menthe   |
| `"Japon"`     | Rose     |
| `"USA"`       | Ambre    |
| `"Taïwan"`    | Violet   |
| `"Autres"`    | Rose foncé (France, Chine, etc.) |

Pour ajouter une nouvelle région, ajoutez-la dans `COLORS` dans index.html.

## Échelles aromatiques

| Champ  | 0                  | 50            | 100                  |
|--------|--------------------|---------------|----------------------|
| peat   | Aucune tourbe      | Tourbe modérée | Très tourbé (Islay)  |
| rich   | Léger, aqueux      | Équilibré      | Riche, onctueux      |
| comp   | Simple, direct     | Bonne longueur | Très complexe        |
| sweet  | Sec, austère       | Équilibré      | Très doux, sucré     |

## Lancer l'application

**Méthode recommandée (fonctionne toujours) :**
```bash
cd whiskytheque/
python3 -m http.server 8080
```
Puis ouvrir : http://localhost:8080

**Pourquoi pas en double-cliquant ?**
Les navigateurs bloquent le chargement de fichiers JSON locaux par sécurité
(erreur CORS). Un mini serveur web contourne ce problème en 1 commande.

## Ajouter en masse via Claude

Envoyez une photo de rayon à Claude avec ce prompt :
> "Génère le JSON pour ces whiskies au format whiskies.json (peat 0-100,
> rich 0-100, comp 0-100, sweet 0-100, qp 1-3). Retourne uniquement le
> JSON, sans commentaires."

Copiez-collez le résultat à la fin du tableau dans whiskies.json
(avant le `]` final), en ajoutant une virgule après la dernière entrée existante.
