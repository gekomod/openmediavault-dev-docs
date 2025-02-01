---
title: Tworzenie Wpisu
description: 
published: 1
date: 2025-01-26T10:28:43.618Z
tags: 
editor: markdown
dateCreated: 2025-01-26T10:28:41.505Z
---

# Tworzenie Wpisu

```tree
└──ContainerName
   ├──ContainerName.env
   ├──ContainerName.yml
   ├──Containername - This is icon
   └──readme
```

# ContainerName.env

   ```env
      Różne Opcje
   ```

# ContainerName.yml

Przykład na podstawie pliku radarr.yml

  ```yml
  ---
services:
  radarr:
    image: lscr.io/linuxserver/radarr:latest
    container_name: radarr
    environment:
      - PUID=1000
      - PGID=100
      - TZ=Europe/Istanbul
    volumes:
      - CHANGE_TO_COMPOSE_DATA_PATH/radarr/config:/config
      - CHANGE_TO_COMPOSE_DATA_PATH/radarr/movies:/movies
      - CHANGE_TO_COMPOSE_DATA_PATH/radarr/downloads:/downloads
    ports:
      - 7878:7878
    restart: unless-stopped
  ```

# Readme

```readme
Opis kontenera
```

# Icon

Ikone należy pobrać do katalogu kontenera czyli np.

ContainerName/ContainerName 

Ikona musi być bez koncówki tzn bez .png .jpg .svg .bmp itp.