# Preparing the env
## Create the required folders:
```
mkdir -p /var/www/html
mkdir -p /var/www/conf
```

## Copy the example files
```
cp files/nginx.conf /var/www/conf
cp files/*.php /var/www/html
```

# Using docker-compose - NO SWARM (alternative)
```
docker-compose up -d
```

# Starting the stack - When using SWARM
```
docker stack deploy -c docker-compose.yml myweb
```
