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
appelle un **Worker Cloudflare** qui détient la clé ILaaS côté serveur et
relaie la requête. Ouvrir le code source de cette page ne donne accès à rien.

```
navigateur  ──POST──▶  Worker Cloudflare  ──POST + clé──▶  ILaaS
(cette page)           (secret ILAAS_API_KEY)
```

Le Worker n'accepte que les requêtes venant de ce site, borne la taille des
réponses, et peut être verrouillé par un mot de passe d'atelier. Le code du
relais et la procédure de déploiement vivent dans le dossier projet PracTice,
hors dépôt public.

## Modèle

**Qwen 3.6** (`qwen-3.6-35b-instruct`) via [ILaaS](https://www.ilaas.fr), le
service d'inférence mutualisé de l'enseignement supérieur et de la recherche.
Le modèle est fixé par le relais : il n'y a rien à choisir dans la page.

Contexte de 256 k tokens : un document de 126 pages passe entier, sans
découpage. Une génération prend quelques secondes.

Les requêtes transitent par le Worker Cloudflare avant d'atteindre ILaaS ;
le relais ne conserve rien.

## Limites

- PDF scannés non pris en charge (pas d'OCR) — la page le signale
- Word (.docx) non pris en charge : passer par un export PDF
- Un seul format de sortie : les questions de réflexion. Ni QCM, ni glossaire,
  ni cartes de révision

---

IMT Business School — service PracTice
