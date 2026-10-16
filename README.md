# Espace · profils de modules

Profils de **modules et coefficients** pour l'app étudiante non officielle *Espace Android*
(projet indépendant, non affilié à l'ECAM LaSalle). Dans l'app : **Profil → Modules et
coefficients → Choisir un profil**. L'app relit le profil choisi une fois par jour, donc une
correction faite ici arrive chez tout le monde automatiquement.

Les coefficients viennent des syllabus (« document non contractuel ») : en cas de doute, c'est
le relevé officiel de l'ECAM qui fait foi.

## Profils

| Profil | Fichier |
|---|---|
| EENG P2028 · majeure Robotique (S5–S8) | `profiles/eeng-p2028-robotique.json` |

## Ajouter ou corriger un profil

1. Copier un fichier de `profiles/` et l'adapter (format ci-dessous).
2. L'ajouter dans `index.json` (`id` unique, `name`, `description`, `file`).
3. Proposer la modification (pull request) ou l'envoyer au mainteneur.

Les noms de matières doivent être ceux du **Journal des notes** (majuscules, `&`/`and` et
tirets sont tolérés).

## Format

```json
{
  "name": "EENG P2028 · majeure Robotique",
  "description": "Texte court affiché dans l'app",
  "date": "2026-10-15",
  "version": "4",
  "moduleConfig": {
    "7": {
      "__modules__": ["Module A", "Module B"],
      "Module A": {
        "credits": 12,
        "subjects": ["Matière 1", "Matière 2"],
        "coefficients": { "Matière 1": 60, "Matière 2": 40 }
      }
    }
  }
}
```

- La clé (`"7"`) est le numéro du semestre (« Semester 7 » sur le Journal des notes).
- `__modules__` : ordre d'affichage (facultatif).
- `coefficients` : poids de chaque matière dans le module (pas besoin que le total fasse 100).
- `credits` (ECTS, facultatif) : si tous les modules d'un semestre en ont, la moyenne du
  semestre est pondérée par les crédits ; sinon les modules comptent à égalité.
