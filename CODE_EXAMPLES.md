# Code examples — SYM

> **Exemple illustratif et simplifié**, non extrait du firmware ou du code privé. Il montre une frontière de sécurité, pas un contrôleur robotique complet.

## Une intention IA n'est pas une commande moteur

```python
from dataclasses import dataclass
from enum import Enum
from time import monotonic

class Action(Enum):
    STOP = "stop"
    TURN_HEAD = "turn_head"

@dataclass(frozen=True)
class ProposedAction:
    action: Action
    angle_deg: float = 0.0

def authorize_action(
    proposal: ProposedAction,
    *,
    emergency_stop: bool,
    last_sensor_update: float,
) -> ProposedAction:
    if emergency_stop:
        return ProposedAction(Action.STOP)

    if monotonic() - last_sensor_update > 0.25:
        return ProposedAction(Action.STOP)

    if proposal.action is Action.TURN_HEAD:
        if not -30.0 <= proposal.angle_deg <= 30.0:
            return ProposedAction(Action.STOP)

    return proposal
```

**Point d'architecture :** une décision probabiliste passe par une frontière déterministe avant toute commande physique.

**Limites :** exemple purement logiciel ; il ne remplace pas l'arrêt d'urgence matériel, les limites électriques/mécaniques, le watchdog embarqué ni les essais physiques.
