# WIK-DPS-TP02

Images Docker permettant d'executer l'API du TP01.

Le serveur web est execute avec l'utilisateur non-root dedie `webapp`.

## Image mono-stage

Construire l'image :

```sh
docker build -t wik-dps-tp02 .
```

Demarrer l'API :

```sh
docker run --rm -p 3000:3000 --name wik-dps-tp02 wik-dps-tp02
```

## Image multi-stage

Le fichier `Dockerfile.multistage` utilise un stage `build` pour compiler le
projet et un stage `runtime` pour executer l'API. L'image finale contient
uniquement le fichier JavaScript compile dans `dist`, sans les sources
TypeScript.

Construire l'image :

```sh
docker build -f Dockerfile.multistage -t wik-dps-tp02-multistage .
```

Demarrer l'API :

```sh
docker run --rm -p 3000:3000 --name wik-dps-tp02-multistage wik-dps-tp02-multistage
```

L'endpoint est disponible sur `http://localhost:3000/ping`.

## Scan de l'image

Image analysee : `wik-dps-tp02:latest`

| Severite | Nombre |
| --- | ---: |
| UNKNOWN | 0 |
| LOW | 0 |
| MEDIUM | 2 |
| HIGH | 0 |
| CRITICAL | 0 |

Les paquets Alpine ne contiennent aucune vulnerabilite detectee. Les deux
vulnerabilites proviennent de paquets Node.js inclus dans l'image de base.

## Vulnerabilites detectees

| Paquet | CVE | Severite | Version installee | Version corrigee | Statut |
| --- | --- | --- | --- | --- | --- |
| `brace-expansion` | [`CVE-2026-45149`](https://avd.aquasec.com/nvd/cve-2026-45149) | MEDIUM | `5.0.5` | `5.0.6` | fixed |
| `ip-address` | [`CVE-2026-42338`](https://avd.aquasec.com/nvd/cve-2026-42338) | MEDIUM | `10.1.0` | `10.1.1` | fixed |

## Commande utilisee

```sh
docker run --rm -v /var/run/docker.sock:/var/run/docker.sock aquasec/trivy:latest image --scanners vuln --severity UNKNOWN,LOW,MEDIUM,HIGH,CRITICAL wik-dps-tp02:latest
```

Pour scanner l'image multi-stage :

```sh
docker run --rm -v /var/run/docker.sock:/var/run/docker.sock aquasec/trivy:latest image --scanners vuln --severity UNKNOWN,LOW,MEDIUM,HIGH,CRITICAL wik-dps-tp02-multistage:latest
```
