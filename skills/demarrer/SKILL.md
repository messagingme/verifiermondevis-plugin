---
name: demarrer
description: Met en place VerifierMonDevis dans Claude Code - créer la clé d'API, la poser dans VMD_API_KEY, acheter des crédits.
disable-model-invocation: true
---

# Démarrer avec VerifierMonDevis

Le plugin parle au serveur `https://www.verifiermondevis.fr/mcp` avec la clé d'API de l'utilisateur, lue dans la
variable d'environnement `VMD_API_KEY`. Guidez-le, une étape à la fois.

1. **Un compte** : sur https://www.verifiermondevis.fr/inscription?returnTo=/developpeurs/compte, puis confirmer son
   adresse e-mail (lien reçu par e-mail).
2. **Une clé** : sur https://www.verifiermondevis.fr/developpeurs/compte, accepter les conditions d'utilisation de
   l'API et créer une clé. Elle commence par `vmd_` et ne s'affiche qu'une fois : il la copie lui-même. La première clé
   offre quelques analyses. Ne lui demandez jamais de vous la donner dans la conversation.
3. **La variable** : il la pose lui-même dans son terminal, avant de lancer Claude Code.
   - macOS ou Linux : `export VMD_API_KEY="vmd_..."` (dans `~/.zshrc` ou `~/.bashrc` pour la garder).
   - Windows : `setx VMD_API_KEY "vmd_..."`, puis ouvrir un nouveau terminal.
4. **Relancer Claude Code**, puis vérifier avec `/mcp` que le serveur `verifiermondevis` est connecté.
5. **Des crédits**, quand les analyses offertes sont utilisées : sur la même page, par carte, avec une facture à son
   entreprise.

Ensuite, il suffit d'écrire « analyse ce devis ./devis.pdf ».
