---
name: analyser-devis
description: Analyse un devis de travaux (PDF, JPEG ou PNG) avec VerifierMonDevis et en rend le résultat - verdict, écart sur les prix, entreprise vérifiée, points à vérifier, conseils, message à envoyer à l'artisan. À utiliser quand l'utilisateur demande d'analyser, de vérifier ou de juger un devis, ou s'il faut le signer.
---

# Analyser un devis

L'utilisateur veut savoir ce que vaut un devis de travaux. Une analyse débite un crédit de son compte VerifierMonDevis.

## Avant tout

- Les outils `verifiermondevis` (`prepare_upload`, `analyze_quote`, `get_analysis`, `list_analyses`) doivent être
  disponibles. S'ils ne le sont pas, ou s'ils répondent que la clé est absente, invalide ou révoquée, suivez la
  compétence `demarrer` de ce plugin et arrêtez-vous là.
- Le fichier doit exister, être un PDF, un JPEG ou un PNG, et peser 4 Mo au plus. Un PDF qui contient plusieurs devis
  est refusé : il faut les envoyer un par un.
- N'affichez jamais la clé d'API, et ne la mettez dans aucune commande.

## Les étapes

1. Appelez `prepare_upload`. Il rend une commande `curl` et un `upload_id`.
2. Lancez cette commande en remplaçant `CHEMIN/DU/DEVIS.pdf` par le chemin du fichier, entre guillemets. Sous
   PowerShell, écrivez `curl.exe` au lieu de `curl`. Si la commande échoue, recommencez à l'étape 1 : l'adresse ne sert
   qu'une fois et vaut 10 minutes.
3. Appelez `analyze_quote` avec l'`upload_id` et le nom du fichier (`file_name`). Notez l'identifiant de l'analyse.
4. Attendez 20 secondes, puis appelez `get_analysis` avec cet identifiant. Recommencez tant que l'analyse est en cours
   (en général 1 à 3 minutes). Au-delà de 6 minutes, donnez l'identifiant à l'utilisateur et dites-lui qu'il pourra
   relire l'analyse plus tard.
5. Recopiez à l'utilisateur le texte rendu par `get_analysis`, en entier et tel quel : ne le résumez pas, ne le
   reformulez pas, n'ajoutez pas votre propre avis sur les prix. Si le texte annonce une relecture par un expert,
   dites-le : la version relue arrivera au même endroit sous 24 h ouvrées.

## Si un appel est refusé

Dites à l'utilisateur la phrase rendue par l'outil, telle quelle. Crédits épuisés : donnez-lui le lien d'achat qu'elle
contient. Relancer `analyze_quote` avec le même `upload_id` ne débite pas une seconde fois.

Plusieurs devis à analyser : un à la fois, de la même façon.
