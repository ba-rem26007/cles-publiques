# Clés publiques — infra sd-185908

Dépôt **public** volontairement : il ne contient **que des clés publiques et des empreintes**,
qu'on peut diffuser sans risque. Les secrets et la configuration sont dans un dépôt privé chiffré.

| Dossier | Contenu | Usage |
|---|---|---|
| `ssh-utilisateurs/` | clés SSH publiques des comptes | à ajouter dans `~/.ssh/authorized_keys` d'une machine pour y autoriser l'accès |
| `serveurs/` | clés d'hôte SSH, `known_hosts`, `EMPREINTES.txt` | vérifier qu'on se connecte au bon serveur (anti-usurpation) |
| `tls/` | empreintes des certificats auto-signés (Proxmox, PBS) | vérifier le certificat avant de l'accepter |

## Autoriser la clé root du serveur sur une autre machine

```
curl -fsSL https://raw.githubusercontent.com/ba-rem26007/cles-publiques/main/ssh-utilisateurs/root@sd-proxmox-1.pub >> ~/.ssh/authorized_keys
```

## Autoriser l'ancien serveur web (WEB01, 92.222.113.170) — migration eco-gobelets

```
curl -fsSL https://raw.githubusercontent.com/ba-rem26007/cles-publiques/main/ssh-utilisateurs/elrems@WEB01-ed25519.pub >> ~/.ssh/authorized_keys
```

## Faire confiance aux serveurs avant la première connexion

```
curl -fsSL https://raw.githubusercontent.com/ba-rem26007/cles-publiques/main/serveurs/known_hosts >> ~/.ssh/known_hosts
```

Mis à jour automatiquement depuis le serveur (chaque nuit).
