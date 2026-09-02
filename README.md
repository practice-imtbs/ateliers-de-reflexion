# Ateliers de réflexion

Génère des questions de réflexion de haut niveau taxonomique à partir d'un
document (PDF ou texte collé), en reproduisant le format de l'activité
« Ateliers de réflexion » de Nolej.

**→ https://practice-imtbs.github.io/ateliers-de-reflexion/**

Rien à installer, aucune clé à saisir : dépose un PDF, choisis le modèle,
génère. Les questions sont modifiables dans la page avant d'être copiées ou
téléchargées en `.md`.

## Où est la clé

Elle n'est pas ici, et c'est volontaire. La page n'embarque aucun secret : elle
appelle un **Worker Cloudflare** qui détient la clé OpenRouter côté serveur et
relaie la requête. Ouvrir le code source de cette page ne donne accès à rien.

```
navigateur  ──POST──▶  Worker Cloudflare  ──POST + clé──▶  OpenRouter
(cette page)           (secret CLE_OPENROUTER)
```

Le Worker n'accepte que les requêtes venant de ce site, borne la taille des
réponses, et peut être verrouillé par un mot de passe d'atelier. Le code du
relais et la procédure de déploiement vivent dans le dossier projet PracTice,
hors dépôt public.

## Modèle

La liste des modèles est chargée en direct depuis OpenRouter : les nouveautés
apparaissent seules. Défaut : `~deepseek/deepseek-v4-flash-latest` (le tilde
fait partie de l'identifiant), contexte 1,3 M tokens — un document de 126 pages
passe entier, pour environ 0,6 centime.

## Limites

- PDF scannés non pris en charge (pas d'OCR) — la page le signale
- Word (.docx) non pris en charge : passer par un export PDF
- Une seule activité : les autres formats Nolej (QCM, glossaire, flashcards) ne
  sont pas couverts

---

IMT Business School — service PracTice
