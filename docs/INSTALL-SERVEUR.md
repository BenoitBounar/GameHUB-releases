# Installer un serveur GameHuB (CasaOS / NAS / Docker)

Le **serveur** héberge la bibliothèque ; les **apps clientes** (Windows) s'y connectent
via son adresse réseau. Trois façons de faire tourner le serveur :

| Vous avez… | Solution |
|---|---|
| Un PC Windows | L'**app serveur** (installeur `GameHuB-Setup.exe`, cocher « Serveur »). |
| Un **CasaOS** | Import 1-clic (ci-dessous). |
| Un **NAS / Docker** | `docker compose` (ci-dessous). |

> ⚠️ **Prérequis unique** : l'image `ghcr.io/benoitbounar/gamehub` doit être **publique**
> (GitHub → repo GameHUB → *Packages* → `gamehub` → *Package settings* → *Change visibility* → **Public**).

---

## CasaOS (import 1-clic)

1. CasaOS → **Applications** → **+** → **Installer une app personnalisée** → **Importer**.
2. Collez le contenu de [`casaos/docker-compose.yml`](../casaos/docker-compose.yml).
3. **Installer**. GameHuB apparaît dans vos apps.
4. Adresse à donner aux clients : `http://[IP-du-CasaOS]:3000`.

## NAS / Docker Compose

```bash
mkdir -p /DATA/AppData/gamehub/data
# Récupérez casaos/docker-compose.yml (ou docker-compose.yml à la racine), puis :
docker compose up -d
```
Adresse à donner aux clients : `http://[IP-de-la-machine]:3000`.

## Mise à jour du serveur

```bash
docker compose pull && docker compose up -d
```

---

## Côté client (chaque PC)

Ouvrez l'app **GameHuB**, écran **« Adresse du serveur »**, saisissez l'adresse
du serveur (ex. `192.168.1.104:3000`). Vous pouvez en changer à tout moment
(menu ⚙ → « Changer de serveur »).
