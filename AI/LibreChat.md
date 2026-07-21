# Docker
install follow [[Docker]]
```bash


```

# LibreChat

```bash
cd /opt
```
```bash
sudo git clone https://github.com/danny-avila/LibreChat.git
```
```bash
cd LibreChat
```
```bash
sudo cp .env.example .env
```
```bash
sudo vim .env
```
```bash
sudo su -
```
```bash
openssl rand -hex 32 >> .env
```
```bash
vim .env
```
copy last line after ADMIN_PANEL_SESSION_SECRET
```bash
cp docker-compose.override.yml.example docker-compose.override.yml
```
```bash
vim docker-compose.override.yml
```
uncomment services:
```bash
docker compose up -d
```
