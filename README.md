# zabbix-compose

Оф страница с инструкцией по установке docker
[Docker Doks](https://docs.docker.com/engine/install/ubuntu/)

# Установка Docker на ubuntu 20.04,20.10
```bash
sudo apt-get install apt-transport-https ca-certificates curl \
    gnupg lsb-release
	
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose

sudo usermod -aG docker $USER
```

## Перед запуском сервера отредактируйте переменные в compose файле под себя
```bash
POSTGRES_USER=zabbix
POSTGRES_PASSWORD=zabbix
POSTGRES_DB=zabbixNew
```

# Старт и остановка сервера

## Старт
```bash
sudo docker-compose -f docker-compose-server-amd64.yaml up -d
```

Если хотите обнулить данные БД и накатить сервер заново но с чистой конфигурацией то удалить папку /var/lib/postgresql/data
```bash
sudo rm -rf /var/lib/postgresql/data
```

## Остановка
```bash
sudo docker-compose -f docker-compose-server-amd64.yaml down
```




# Старт и остановка proxy
## Старт
```bash
sudo docker-compose -f docker-compose-proxy-amd64.yaml up -d
```

## Остановка
```bash
sudo docker-compose -f docker-compose-proxy-amd64.yaml down
```
