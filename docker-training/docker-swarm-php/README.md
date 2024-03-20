# Preparing the env

# Fix the docker address-pool:
```
cat <<EOF | sudo tee /etc/docker/daemon.json
{
  "default-address-pools": [
    {
      "base": "172.66.66.0/16",
      "size": 24
    }
  ]
}
EOF

systemctl restart docker
```

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
