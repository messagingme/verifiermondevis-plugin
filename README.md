# VerifierMonDevis pour Claude Code

Analysez un devis de travaux depuis Claude Code : prix comparés à un référentiel, entreprise vérifiée aux registres,
clauses du devis, conseils et message à envoyer à l'artisan. Le service est celui de
[verifiermondevis.fr](https://www.verifiermondevis.fr/developpeurs), avec votre clé d'API et vos crédits.

## Installer

1. Créez une clé d'API sur [votre espace développeur](https://www.verifiermondevis.fr/developpeurs/compte). La
   première clé offre quelques analyses.
2. Posez-la dans la variable `VMD_API_KEY`, avant de lancer Claude Code :

   ```
   export VMD_API_KEY="vmd_VOTRE_CLE"
   ```

   Sous Windows : `setx VMD_API_KEY "vmd_VOTRE_CLE"`, puis ouvrez un nouveau terminal.

3. Dans Claude Code :

   ```
   /plugin marketplace add messagingme/verifiermondevis-plugin
   /plugin install verifiermondevis@verifiermondevis
   ```

## Utiliser

Écrivez par exemple « analyse ce devis ./devis.pdf ». Claude envoie le fichier, lance l'analyse (un crédit), attend le
résultat et vous le recopie. Besoin d'aide pour la clé : `/verifiermondevis:demarrer`.

Codex, ou Claude Code sans le plugin : voir la
[documentation](https://www.verifiermondevis.fr/developpeurs/documentation#claude-code).
