# WIK-DPS-TP02

Image Docker mono-stage permettant d'executer l'API du TP01.

## Construire l'image

```sh
docker build -t wik-dps-tp02 .
```

## Demarrer l'API

```sh
docker run --rm -p 3000:3000 --name wik-dps-tp02 wik-dps-tp02
```

L'endpoint est disponible sur `http://localhost:3000/ping`.
