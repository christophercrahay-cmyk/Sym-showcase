# Audit 01 — Perception / action

**Question :** une caméra, un microphone ou un modèle peut-il garantir à lui seul une action physique correcte ?

**Réponse vérifiable dans la présentation publique :** non. La chaîne décrite sépare acquisition audio/vision, traitement IA et sorties vocales ou physiques. Les interfaces entre composants et leurs défaillances possibles sont des points d'inspection.

**Limite :** aucun journal de latence, protocole embarqué ni essai matériel reproductible n'est publié ici. Il s'agit d'un principe architectural documenté, pas d'une validation expérimentale.

**Trace d'audit :** `01 / PERCEPTION / frontière identifiée`

**Étape suivante :** [02 — génération et validation](https://github.com/christophercrahay-cmyk/local-agents-neurobase-showcase/blob/main/AUDIT.md). La perception produit des informations imparfaites ; que fait-on des sorties probabilistes ?
