# Ateliers de réflexion

Génère des questions de réflexion de haut niveau taxonomique à partir d'un
document (PDF ou texte collé) : des mises en situation concrètes, ouvertes,
sans réponse unique, situées aux niveaux 3 à 5 de la taxonomie de Bloom.

**→ https://practice-imtbs.github.io/ateliers-de-reflexion/**

Rien à installer, aucune clé à saisir, aucun réglage : dépose un PDF, génère.
Les questions sont modifiables dans la page avant d'être copiées ou
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

**DeepSeek V4 Flash**, fixé — il n'y a rien à choisir dans la page.
L'identifiant `~deepseek/deepseek-v4-flash-latest` est un alias qui suit
automatiquement la dernière version de la famille (le tilde en fait partie).

Contexte de 1,3 M tokens : un document de 126 pages passe entier, sans
découpage, pour environ 0,6 centime.

## Limites

- PDF scannés non pris en charge (pas d'OCR) — la page le signale
- Word (.docx) non pris en charge : passer par un export PDF
- Un seul format de sortie : les questions de réflexion. Ni QCM, ni glossaire,
  ni cartes de révision

---

IMT Business School — service PracTice
