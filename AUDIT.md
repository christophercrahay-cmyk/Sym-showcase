# Audit 01 — Perception / action

**Question :** une caméra, un microphone ou un modèle peut-il garantir à lui seul une action physique correcte ?

**Réponse vérifiable dans la présentation publique :** non. La chaîne décrite sépare acquisition audio/vision, traitement IA et sorties vocales ou physiques. Les interfaces entre composants et leurs défaillances possibles sont des points d'inspection.

**Élément observable :** [démonstration vidéo du robot](https://christopher-crahay.vercel.app/work/sym) avec réponse vocale et animation de la mâchoire.

**Limite :** aucun journal de latence ni essai matériel reproductible n'est publié ici. La vidéo ne valide pas tous les comportements du matériel, du protocole ou des chemins logiciels.

**Trace d'audit :** `01 / PERCEPTION / frontière identifiée`

**Étape suivante :** [02 — génération et validation](https://github.com/christophercrahay-cmyk/local-agents-neurobase-showcase/blob/main/AUDIT.md). La perception produit des informations imparfaites ; que fait-on des sorties probabilistes ?
