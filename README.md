# ftpiiu FR - Un plugin de serveur FTP pour la Wii U basé sur ftpd

## Installation
(`[ENVIRONMENT]` est à remplacer par le nom de l'environnement que vous utilisez.)

1. Copiez-collez `ftpiiu.wps` dans `sd:/wiiu/environments/[ENVIRONMENT]/plugins`.
2. Requiert [WiiUPluginLoaderBackend](https://github.com/wiiu-env/WiiUPluginLoaderBackend) dans `sd:/wiiu/environments/[ENVIRONMENT]/modules`.

## Informations d'utilisations et paramètres

- Par défaut, le plugin FTPiiU tourne en fond tand que le plugin est chargé (le fichier est dans le chemin d'accès correspondant à l'environnement).
- L'accès aux fichiers systèmes est **désactivé par défaut**, mais vous pouvez l'activer dans le menu de configuration.
- Pour vous connecter au serveur vous pouvez laisser les informations de connexion vides
- La carte SD peut être accédée via `/fs/vol/external01/`

Grâce au menu de configuration des plugins, (pressez L, DPAD Bas et - sur le gamepad) vous pouvez configurer le plugin. Les options disponibles sont les suivantes:
- **Paramètres**:
  - Activer FTPiiU:
    - Démarre/Éteint le serveur ftp qui tourne en fond. Les changements prennent effet après avoir quitté le menu de configuration. (Activé par défaut).
  - Autoriser l'accès aux fichiers systèmes:
    - Autorise l'accès aux fichiers systèmes. Si cette option est désactivée, vous ne pourrez uniquement accéder qu'à `/fs/vol/content`, `/fs/vol/save` et `/fs/vol/external01` (carte SD). Les changements prennent effet après avoir quitté le menu de configuration, mais le serveur pourrait redémarrer. (Désactivé par défaut).
- Le menu de configuration affichera l'adresse IP et le port que votre console utilise pour le serveur FTP.

Voir le [dépôt ftpd](https://github.com/mtheall/ftpd?tab=readme-ov-file#supported-commands) pour avoir une liste des commandes supportées. (Anglais!)

### Logs
Les logs apparaîtront uniquement dans les logs systèmes. (OSReport).

## Crédits

Ce plugin est basé sur [ftpd](https://github.com/mtheall/ftpd) by mtheall
Plugin original : mtheall, Maschell [ftpiiu_plugin](https://github.com/wiiu-env/ftpiiu_plugin)
Nairod Informatique : Traduction française

## Pas encore traduit en français :
## Building using the Dockerfile

It's possible to use a docker image for building. This way you don't need anything installed on your host system.

```
# Build docker image (only needed once)
docker build . -t ftpiiuplugin-builder

# make 
docker run -it --rm -v ${PWD}:/project ftpiiuplugin-builder make

# make clean
docker run -it --rm -v ${PWD}:/project ftpiiuplugin-builder make clean
```

## Format the code via docker

`docker run --rm -v ${PWD}:/src ghcr.io/wiiu-env/clang-format:13.0.0-2 -r ./source ./include -i`

