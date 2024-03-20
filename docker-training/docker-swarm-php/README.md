# Preparing the env
## Create the required folders:
```
mkdir -p /var/www/html
mkdir -p /var/www/conf
```

## Copy the example files
```
cp files/nginx.conf /var/www/conf
cp files/index.php /var/www/html
```

# Starting the stack
```
docker stack deploy -c docker-compose.yml myweb
```

# Using docker-compose - NO SWARM (alternative)
```
docker-compose up -d
```
