# Sviluppo

## Requisiti sul PC
- Docker 18 o superiore 
- Docker Compose 1.17 o superiore

## Avviare i containers
```bash
docker-compose up -d
```

## Verifica stato containers
```bash
docker-compose ps
```

## Dati di accesso Vtiger
Vtiger1: admin/admin
Vtiger2: admin/admin

## Installare le dipendence
```bash
docker-compose run --rm myddleware php composer.phar install --ignore-platform-reqs --no-scripts
```

## Preparazione dei file e cartelle
```bash
docker-compose run --rm myddleware php composer.phar run-script post-install-cmd
```

## Installare il database
```bash
docker-compose run --rm myddleware ./prepare-database.sh
```

## Dati di accesso Myddleware
Myddleware: admin/admin

## Permessi di scrittura
```bash
linux: sudo chmod 777 -R var/cache var/logs
macos: find var/cache -type d -exec sudo chmod 0777 {} +
       find var/logs -type d -exec sudo chmod 0777 {} +
```

## Aggiornare le dipendenze
```bash
sudo rm -fr var/cache/*
sudo rm -rf vendor && composer update -v --ignore-platform-reqs --no-scripts
docker-compose run --rm myddleware php composer.phar run-script post-install-cmd
```